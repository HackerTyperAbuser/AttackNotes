- Identify domain usernames:
	- Found through enumeration on the network 
	- T1110: `Kerbrute` to brute-force usernames

- [ ] T1557.001: [LLMNR/NBT-NS Poisoning](Techniques/LLMNR%20Poisoning.md) and [SMB Relay](Techniques/SMB%20Relay.md)
- [ ] AS-REP Roasting 
For every new credentials obtained:
- [ ] [Kerberoasting](Techniques/Kerberoasting.md)
- [ ] Enumerate SMB shares
- [ ] [Password Spraying](Techniques/Password%20Spraying.md)
For every `PWNED`
- [Credential Dumping](../Post%20Exploitation/Windows/Credential%20Dumping.md) -> SAM, LSASS, Windows Credential Manger