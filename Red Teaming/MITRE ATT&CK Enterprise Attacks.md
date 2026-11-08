# TA0043 - Reconnaissance
## T1595: Active Scanning
Scanning target to gather information that can be used during targeting https://attack.mitre.org/techniques/T1595/.

| Sub-Technique                                               | Name                   | Notes                                          |
| ----------------------------------------------------------- | ---------------------- | ---------------------------------------------- |
| [T1595.001](https://attack.mitre.org/techniques/T1595/001/) | Scanning IP Blocks     | [Information Gathering](../Network%20Pentesting/Information%20Gathering.md)                      |
| [T1595.002](https://attack.mitre.org/techniques/T1595/002/) | Vulnerability Scanning | [Information Gathering](../Network%20Pentesting/Information%20Gathering.md)                      |
| [T1595.003](https://attack.mitre.org/techniques/T1595/003/) | Wordlist Scanning      | [Information Gathering](../Network%20Pentesting/Information%20Gathering.md), [Web Enumeration](../Web%20Application%20Pentesting/Web%20Enumeration.md) |

# TA0042 - Resource Development
# TA0001 - Initial Access
## T1190 Exploit Public-Facing Application
https://attack.mitre.org/techniques/T1190/
**NOTES:**
- [Web Application Attacks](../Web%20Application%20Pentesting/Web%20Application%20Attacks.md)

# TA0002 - Execution

# TA0003 - Persistence

# TA0004 - Privilege Escalation
https://attack.mitre.org/tactics/TA0004/
## T1548: Abuse Elevation Control Mechanism
https://attack.mitre.org/techniques/T1548/
**Other techniques:**
-  [Capabilities Abuse](../Post%20Exploitation/Linux/Capabilities%20Abuse.md)

| Sub-Technique | Name                            | Notes                                                            |
| ------------- | ------------------------------- | ---------------------------------------------------------------- |
| T1548.001     | Setuid and Setgid               | [SUID Binaries](../Post%20Exploitation/Linux/SUID%20Binaries.md) |
| T1548.002     | Bypass User Account Control     |                                                                  |
| T1548.003     | Sudo and Sudo Caching           | [SUDO](../Post%20Exploitation/Linux/SUDO.md)                     |
| T1548.004     | Elevated Execution with Prompt  | N/A                                                              |
| T1548.005     | Temporary Elevated Cloud Access | N/A                                                              |
| T1548.006     | TCC Manipulation                | N/A                                                              |
## T1134: Access Token Manipulation
Adversaries may modify access tokens to operate under a different user or system security context to perform actions and bypass access controls. https://attack.mitre.org/techniques/T1134/

| Sub-Technique                                               | Name                       | Notes                 |
| ----------------------------------------------------------- | -------------------------- | --------------------- |
| [T1134.001](https://attack.mitre.org/techniques/T1134/001/) | Token Impersonation/Theft  | [Access Privileges](../Post%20Exploitation/Windows/Access%20Privileges.md) |
| [T1134.002](https://attack.mitre.org/techniques/T1134/002/) | Create Process with Token  | [RunAs](../Post%20Exploitation/Windows/Privilege%20Escalation/RunAs.md)             |
| [T1134.003](https://attack.mitre.org/techniques/T1134/003/) | Make and Impersonate Token | N/A                   |
| [T1134.004](https://attack.mitre.org/techniques/T1134/004/) | Parent PID Spoofing        | N/A                   |
| [T1134.005](https://attack.mitre.org/techniques/T1134/005/) | SID-History Injection      | N/A                   |
## T1098: Account Manipulation
## T1547: Boot or Logon Autostart Execution
https://attack.mitre.org/techniques/T1547/

| Sub-Technique                                               | Name                                 | Notes                                          |
| ----------------------------------------------------------- | ------------------------------------ | ---------------------------------------------- |
| [T1547.001](https://attack.mitre.org/techniques/T1547/001/) | Registry Run Keys /  Startup Folders | [Windows Registry](../Post%20Exploitation/Windows/Privilege%20Escalation/Windows%20Registry.md), [Startup Applications](../Post%20Exploitation/Windows/Startup%20Applications.md) |
| [T1547.002](https://attack.mitre.org/techniques/T1547/002/) | Authentication Package               |                                                |
| [T1547.003](https://attack.mitre.org/techniques/T1547/003/) | Time Providers                       |                                                |
|                                                             | Winlogon Helper DLL                  |                                                |
|                                                             | Security Support Provider            |                                                |
|                                                             | Kernel Modules and Extensions        |                                                |
|                                                             | Re-opened Applications               | N/A                                            |
|                                                             | LSASS Driver                         |                                                |
|                                                             | Shortcut Modification                |                                                |
|                                                             | Port Monitors                        |                                                |
|                                                             | Print Processors                     |                                                |
|                                                             | XDG Autostart Entries                |                                                |
|                                                             | Active Setup                         |                                                |
|                                                             | Login Items                          | N/A                                            |


## T1611: Escape to Host
https://attack.mitre.org/techniques/T1611/
**NOTES:**
- [Privileged Groups](../Post%20Exploitation/Linux/Privileged%20Groups.md)
- [Kubernetes](../Post%20Exploitation/Linux/Kubernetes.md)
## T1068: Exploitation for Privilege Escalation
Exploiting Software vulnerabilities in attempt to elevate privileges.
**NOTES:**
- [Linux Userland Exploits](../Post%20Exploitation/Linux/Linux%20Userland%20Exploits.md)
- [Linux Kernel Exploits](../Post%20Exploitation/Linux/Linux%20Kernel%20Exploits.md)
- [Windows Kernel Exploits](../Post%20Exploitation/Windows/Privilege%20Escalation/Windows%20Kernel%20Exploits.md)
# TA0006 - Credential Access

## T1557: Adversary-in-the-Middle
https://attack.mitre.org/techniques/T1557/

| Sub-Technique | Name                                     | Notes                                                                                                                                                       |
| ------------- | ---------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| T1557.001     | Name Resolution Poisoning and SMB Relay  | [LLMNR/NBT-NS Poisoning](Techniques/LLMNR%20Poisoning.md), [IPv6 DNS Takeover](Techniques/IPv6%20DNS%20Takeover.md) and [SMB Relay](Techniques/SMB%20Relay.md) |
| T1557.002     | Arp Cache Poisoning                      |                                                                                                                                                             |
| T1557.003     | DHCP Spoofing                            | [IPv6 DNS Takeover](Techniques/IPv6%20DNS%20Takeover.md)                                                                                                       |
| T1557.004     | Evil Twin                                |                                                                                                                                                             |

## T1110: Brute-Force
https://attack.mitre.org/techniques/T1110/

| Sub-Technique | Name                | Notes                                                                                                                                                                |
| ------------- | ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| T1110.001     | Password Guessing   | [Password Tools](../Network%20Pentesting/Passwords%20Attacks/Password%20Tools.md)                                                                                    |
| T1110.002     | Password Cracking   | [Password Tools](../Network%20Pentesting/Passwords%20Attacks/Password%20Tools.md), [Cracking Files](../Network%20Pentesting/Passwords%20Attacks/Cracking%20Files.md) |
| T1110.003     | Password Spraying   | [Password Spraying](Techniques/Password%20Spraying.md)                                                                                                               |
| T1110.004     | Credential Stuffing | [Password Tools](../Network%20Pentesting/Passwords%20Attacks/Password%20Tools.md)                                                                                                                                                   |
## T1555: Credentials from Password Stores
https://attack.mitre.org/techniques/T1555/

| Sub-Technique | Name                            | Notes                                                                                                                                                                                                      |
| ------------- | ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| T1555.001     | Keychain                        | [iOS Storage](../Mobile%20Application%20Pentesting/iOS/iOS%20Storage.md)                                                                                                                                   |
| T1555.002     | Securityd Memory                |                                                                                                                                                                                                            |
| T1555.003     | Credentials from Web Browsers   | [Credential Dumping](../Post%20Exploitation/Windows/Credential%20Dumping.md)                                                                                                                               |
| T1555.004     | Windows Credential Manager      | [Windows Credential Manager](../Network%20Pentesting/Passwords%20Attacks/Password%20Theory/Windows%20Credential%20Manager.md) [Credential Dumping](../Post%20Exploitation/Windows/Credential%20Dumping.md) |
| T1555.005     | Password Managers               | [Cracking Files](../Network%20Pentesting/Passwords%20Attacks/Cracking%20Files.md)                                                                                                                          |
| T1555.006     | Cloud Secrets Management Stores |                                                                                                                                                                                                            |
## T1187: Forced Authentication
https://attack.mitre.org/techniques/T1187/
**NOTES:**
- [LNK File Attack](Techniques/LNK%20File%20Attack.md)

## T1649: Steal or Forge Authentication Certificates


## T1558: Steal or Forge Kerberos Tickets
https://attack.mitre.org/techniques/T1558/

| Sub-Technique | Name            | Notes               |
| ------------- | --------------- | ------------------- |
| T1558.001     | Golden Ticket   | [Golden Ticket](Techniques/Persistence/Golden%20Ticket.md)   |
| T1558.002     | Silver Ticket   |                     |
| T1558.003     | Kerberoasting   | [Kerberoasting](Techniques/Kerberoasting.md)   |
| T1558.004     | AS-REP Roasting | [AS-REP Roasting](Techniques/AS-REP%20Roasting.md) |
| T1558.005     | Ccache Files    |                     |

## T1539: Steal Web Session Cookie
Steal web application or service session cookie to gain access to web applications or Internet services as an authenticated user without needing credentials https://attack.mitre.org/techniques/T1539/
**NOTES**:
- Session Hijacking: [XSS](../Web%20Application%20Pentesting/Input%20Validation/XSS.md)
- Stealing Browser Cookies: [Credential Dumping](../Post%20Exploitation/Windows/Credential%20Dumping.md)
## T1552: Unsecured Credentials
Finding stored credentials on compromised systems https://attack.mitre.org/techniques/T1552/

| Sub-Technique | Name                        | Notes                                                                  |
| ------------- | --------------------------- | ---------------------------------------------------------------------- |
| T1552.001     | Credentials in Files        | [Windows Credential Hunting](../Post%20Exploitation/Windows/Windows%20Credential%20Hunting.md), [Linux Credential Hunting](../Post%20Exploitation/Linux/Linux%20Credential%20Hunting.md)           |
| T1552.002     | Credentials in Registry     | N/A                                                                    |
| T1552.003     | Shell History               | [Windows Credential Hunting](../Post%20Exploitation/Windows/Windows%20Credential%20Hunting.md), [Linux Credential Hunting](../Post%20Exploitation/Linux/Linux%20Credential%20Hunting.md)           |
| T1552.004     | Private Keys                | [SSH](../Network%20Pentesting/Services/Linux%20Remote%20Management/SSH.md)                                                                |
| T1552.005     | Cloud Instance Metadata API | N/A                                                                    |
| T1552.006     | Group Policy Preferences    | [GPP - cPassword Attacks](Techniques/GPP%20-%20cPassword%20Attacks.md) |
| T1552.007     | Container API               | N/A                                                                    |
| T1552.008     | Chat Messages               | N/A                                                                    |
# TA0007 - Discovery

# TA0008 - Lateral Movement
## T1210: Exploitation of Remote Services
Abusing software/system vulnerabilities to move laterally in the environment https://attack.mitre.org/techniques/T1210/
**NOTES:**
- [Linux Userland Exploits](../Post%20Exploitation/Linux/Linux%20Userland%20Exploits.md)
- [Linux Kernel Exploits](../Post%20Exploitation/Linux/Linux%20Kernel%20Exploits.md)
- [Windows Kernel Exploits](../Post%20Exploitation/Windows/Privilege%20Escalation/Windows%20Kernel%20Exploits.md)
- [AD CVE](Techniques/AD%20CVE.md)
## T1534: Internal Spearphishing
https://attack.mitre.org/techniques/T1534/
## T1570: Lateral Tool Transfer
Transferring of tools from external system to one system to another in the internal network. https://attack.mitre.org/techniques/T1570/
**NOTES**
- [File Transfers](../Network%20Pentesting/File%20Transfers.md)
## T1563: Remote Service Session Hijacking
Take control of pre-existing sessions with remote services to move laterally. https://attack.mitre.org/techniques/T1563/

| Sub-Technique | Name          | Notes |
| ------------- | ------------- | ----- |
| T1563.001     | SSH Hijacking | N/A   |
| T1563.002     | RDP Hijacking | N/A   |

## T1021: Remote Services
Using Valid Accounts to log into  service that accepts remote connections, such as SSH, VNC and telnet... https://attack.mitre.org/techniques/T1021

| Sub-Technique | Name                               | Notes                                    |
| ------------- | ---------------------------------- | ---------------------------------------- |
| T1021.001     | Remote Desktop Protocol            | [Password Spraying](Techniques/Password%20Spraying.md), [RDP](../Network%20Pentesting/Services/Windows%20Remote%20Management/RDP.md)           |
| T1021.002     | SMB/Windows Admin Shares           | [Password Spraying](Techniques/Password%20Spraying.md), [SMB & NetBIOS](../Network%20Pentesting/Services/SMB%20%26%20NetBIOS.md) |
| T1021.003     | Distributed Component Object Model | N/A                                      |
| T1021.004     | SSH                                | [SSH](../Network%20Pentesting/Services/Linux%20Remote%20Management/SSH.md)                                  |
| T1021.005     | VNC                                | N/A                                      |
| T1021.006     | Windows Remote Management          | [Password Spraying](Techniques/Password%20Spraying.md), [WinRM](../Network%20Pentesting/Services/Windows%20Remote%20Management/WinRM.md)         |
| T1021.007     | Cloud Services                     | N/A                                      |
| T1021.008     | Direct Cloud VM Connections        | N/A                                      |
## T1091: Replication Through Removable Media
https://attack.mitre.org/techniques/T1091/
## T1072: Software Deployment Tools
https://attack.mitre.org/techniques/T1072/
## T1080: Taint Shared Content
https://attack.mitre.org/techniques/T1080/
**NOTES:**
- [LNK File Attack](Techniques/LNK%20File%20Attack.md)
## T1550: Use Alternate Authentication Material
Alternate authentication material such as password hashes, Kerberos tickets and application access token to move laterally within an environment. https://attack.mitre.org/techniques/T1550/

| Sub-Technique | Name                     | Notes                                        |
| ------------- | ------------------------ | -------------------------------------------- |
| T1550.001     | Application Access Token | N/A                                          |
| T1550.002     | Pass the Hash            | [Pass the Hash](Techniques/Pass-The-Hash.md) |
| T1550.003     | Pass the Ticket          | [Pass-The-Ticket](Techniques/Pass-The-Ticket.md)                          |
| T1550.004     | Web Session Cookie       | [XSS](../Web%20Application%20Pentesting/Input%20Validation/XSS.md), [Credential Dumping](../Post%20Exploitation/Windows/Credential%20Dumping.md)              |
# Collection
# Command and Control
# Exfiltration
# Impact