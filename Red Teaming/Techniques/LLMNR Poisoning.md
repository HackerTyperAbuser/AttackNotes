NBT-NS Poisoning
### Theory
- **NetBIOS - Network Basic Input/Output System** protocol in Windows system that act similar to domain names (link name for particular shares, printers.. e.g: \\printers, \\sharesfiles to a particular IP address). NetBIOS was replaced by SMB (Server Message Block) protocol in future implementation of Windows.
- **LLMNR - Link-Local Multicast Name Resolution** protocol use in Active Directory environment to resolve names of shared files (Similar to a DNS Resolver). LLMNR protocol resolves SMB file share names.
- **NBT-NS** - **NetBIOS Name Service** same as LLMNR, however, used for legacy systems where NetBIOS is used instead (DNS resolution for NetBIOS names).

![[Pasted image 20260120102314.png]]
Responder
```bash
responder -I <INTERFACE> -wdPv
```
## Defenses
- Policy to disable LLMNR protocol → LLMNR/NBT-NS poisoning not viable.
- Policy to disable NBT-NS (Network connections > Network Adapter Properties > TCP/IPv4 Properties > Advanced tab > WINS tabs and disable “NetBIOS over TCP/IP”.
- Disadvantages
    Disabling LLMNR/NBT-NS can be disadvantageous:
    - Removed fallback mechanism for DNS resolution.
    - LLMNR can be used for mixed-network environment where Windows and non-Windows devices coexists.
    - Some legacy applications relies on LLMNR for name resolution.
    - Removed diagnostic and troubleshooting method (remove potential information to troubleshoot network connectivity issues).

If LLMNR/NBT-NS **cannot be disabled** solutions can be:
- Using Network Access Control (network AC).
- Use strong passwords so hashes are more difficult to be cracked.