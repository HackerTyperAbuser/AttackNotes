T1557.003
## Background
- IPv6 and DNS?
    DNS is use for translating domain names into IP addresses. DNS can be used to publish information about LDAP within the network. DNS is used to locate domain controllers for authentication, directory queries… LDAP communication requires location of domain controllers.
    
    IPv6 is a protocol developed to replace IPv4, it uses 128-bits to create an IP address.
    
- What is WPAD?
    
    Web Proxy Auto-Discovery (WPAD) protocol to ensure all device on network use the same web proxy configuration. Network administrator use WPAD to automatically detect proxy configuration URL, which will be stored in Proxy Auto-Configuration (PAC) file. By default client query the DNS server for the URL of the PAC file. If PAC file is found, all web requests will be routed through the proxy configured in the PAC file.
    

## Anatomy of the Attack

IPv6 DNS Takeover, is a Man-in-the-Middle attack that takes advantage of machines utilizing IPv4 while still having IPv6 active in their network adapter properties.
- When the machine is configured this way, one question comes to mind. Who is DNS for IPv6? Most of the time nobody.
- Typically Windows computer enables IPv6 by default and prefers it over IPv4.
![](file:///C:/Users/admin/Downloads/Untitled.png)

- Usually IPv6 is enabled and it is not set (most likely set to obtain an IPv6 address automatically from DHCP server); `mitm6` can set up the IPv6 addresses for targets.

![](file:///C:/Users/admin/AppData/Local/Microsoft/Windows/Clipboard/HistoryData/%7B1D430A1A-83A8-40E7-9360-A9638732AF4D%7D/%7B2AADBFB1-6D83-407A-87B0-B54231447A2D%7D/ResourceMap/%7BCD538F1B-2CE7-43C6-9D80-EB297067E9F5%7D)
This misconfiguration allows attackers to listen for incoming IPv6 traffic, declaring themselves the DNS for IPv6 through this process attacker can gain authentication to the Domain Controller with LDAP or SMB.

![](file:///C:/Users/admin/AppData/Local/Microsoft/Windows/Clipboard/HistoryData/%7B1D430A1A-83A8-40E7-9360-A9638732AF4D%7D/%7B3D4E4732-D38A-4457-94E5-BC6FE68BFEBF%7D/ResourceMap/%7B6C05BE7D-A46D-4709-9E4C-B9F771191BDC%7D)

For this attack two tools are used: `mitm6` and `ntlmrelayx`

- First the `mitm6` will set up the IPv6 addresses to it’s targets, once this done it intercepts IPv6 traffic flowing through the network including DNS queries to resolve domain names. It sets the attacker as the primary DNS server.

```bash
python mitm6 -d <DOMAIN>
```

- We can capture traffic of the domain; to capture credentials we would need an authentication mechanism which is where WPAD abuse comes in. Since we are the DNS server, a fake WPAD can be hosted, which sets web proxy to the attacker’s IP address when queries.
- From here whenever victim uses application that connects to the internet, the attacker machine will be use as a proxy. Once connected attacker responds with a HTTP 407:Proxy Authentication, prompting Windows machine to send NTLM response. This can be relayed to different authentication services such as LDAP, SMB and HTTP.

→ This can be done with `ntlmrelayx`

```bash
impacket-ntlmrelayx -6 -t ldaps://<LDAP_SERVER_IP> -wh fakewpad.<DOMAIN> -l loot
```

The code starts a fake WPAD URL and relays the NTLM response to the targeted LDAP server (typically the DC) for authentication. Once authenticated domain information (LDAP database) can be **dumped** out to the loot directory.

- In the case where credentials of high privileged users such as the Domain Admin is captured, `ntlmrelayx` will create a new user.
- This account is created with an Access Control List (ACL) providing privileges ‘DS-Replication-Get-Changes-All’ and ‘DS-Replication-Get-Changes’ allowing retrieval of password hashes from AD.

[IPv6 DNS Takeover](https://redfoxsec.com/blog/ipv6-dns-takeover/)

## Lab Demo

Attacker’s IP: 10.0.2..6

DC IP: 10.0.2.15

THEPUNISHER IP (target1): 10.0.2.16

![[Pasted image 20261103103501.png]]

![[Pasted image 20261103103509.png]]

```bash
sudo python mitm6 -d <DOMAIN>
```

![[Pasted image 20261103103531.png]]

```bash
impacket-ntlmrelayx -6 -t ldaps://<LDAP_SERVER_IP> -wh fakewpad.<DOMAIN> -l loot
```

![[Pasted image 20261103103616.png]]

![[Pasted image 20261103103623.png]]
## Defenses

- If IPv6 is not needed in environment block DHCPv6 traffic and incoming router advertisements in Windows Firewall via Group Policy. Disabling IPv6 entirely may have unwanted side effects.
- Setting the following predefined rules to Block instead of Allow prevent the attack from working:
    - (Inbound) Core Networking - Dynamic Host Configuration Protocol for IPv6 (DHCPv6-In)
    - (Inbound) Core Networking - Router Advertisement (ICMPv6-In)
    - (Outbound) Core Networking - Dynamic Host Configuration Protocol for IPv6 (DHCPv6-Out)
- If WPAD is not in use internally, disable it via Group Policy and by disabling the WinHttpAutoProxySvc service.
- Relaying LDAP and LDAPS can only be mitigated by enabling LDAP signing and LDAP channel binding.
- Consider Administrative users to the Protected Users group or marking them as Account is sensitive and cannot be delegated which will prevent any impersonation of that user via delegation.