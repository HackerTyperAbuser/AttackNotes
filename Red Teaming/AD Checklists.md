- Identify domain usernames:
	- Found through enumeration on the network 
	- T1110: `Kerbrute` to brute-force usernames

- [ ] T1557.001: [LLMNR/NBT-NS Poisoning](Techniques/LLMNR%20Poisoning.md) and [SMB Relay](Techniques/SMB%20Relay)
- [ ] AS-REP Roasting 
For every new credentials obtained:
- [ ] [[Kerberoasting]]
- [ ] Enumerate SMB shares
- [ ] [[Password Spraying]]
For every `PWNED`
- [[Credential Dumping]] -> SAM, LSASS, Windows Credential Manger