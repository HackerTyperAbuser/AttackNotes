[Kerberos](Techniques/Kerberos.md)
# Initial Access
## T1190 Exploit Public-Facing Application
https://attack.mitre.org/techniques/T1190/
**NOTES:**
- [Web Application Attacks](../Web%20Application%20Pentesting/Web%20Application%20Attacks.md)

# TA0004 - Privilege Escalation
https://attack.mitre.org/tactics/TA0004/
**NOTES:**
-  [Capabilities Abuse](../Post%20Exploitation/Linux/Capabilities%20Abuse.md)
## T1548: Abuse Elevation Control Mechanism
https://attack.mitre.org/techniques/T1548/

| Sub-Technique | Name                           | Notes                                                            |
| ------------- | ------------------------------ | ---------------------------------------------------------------- |
| T1548.001     | Setuid and Setgid              | [SUID Binaries](../Post%20Exploitation/Linux/SUID%20Binaries.md) |
| T1548.002     | Bypass User Account Control    |                                                                  |
| T1548.003     | Sudo and Sudo Caching          | [SUDO](../Post%20Exploitation/Linux/SUDO.md)                     |
|               | Elevated Execution with Prompt |                                                                  |

# TA0006 - Credential Access

## T1557: Adversary-in-the-Middle
https://attack.mitre.org/techniques/T1557/

| Sub-Technique | Name                                     | Notes                                                                                                                                                       |
| ------------- | ---------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| T1557.001     | Name Resolution Poisoning and SMB Relay  | [LLMNR/NBT-NS Poisoning](Techniques/LLMNR%20Poisoning.md), [IPv6 DNS Takeover](Techniques/IPv6%20DNS%20Takeover) and [SMB Relay](Techniques/SMB%20Relay.md) |
| T1557.002     | Arp Cache Poisoning                      |                                                                                                                                                             |
| T1557.003     | DHCP Spoofing                            | [IPv6 DNS Takeover](Techniques/IPv6%20DNS%20Takeover)                                                                                                       |
| T1557.004     | Evil Twin                                |                                                                                                                                                             |

## T1110: Brute-Force
https://attack.mitre.org/techniques/T1110/

| Sub-Technique | Name                | Notes                                                                                                                                                                |
| ------------- | ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| T1110.001     | Password Guessing   | [Password Tools](../Network%20Pentesting/Passwords%20Attacks/Password%20Tools.md)                                                                                    |
| T1110.002     | Password Cracking   | [Password Tools](../Network%20Pentesting/Passwords%20Attacks/Password%20Tools.md), [Cracking Files](../Network%20Pentesting/Passwords%20Attacks/Cracking%20Files.md) |
| T1110.003     | Password Spraying   | [Password Spraying](Techniques/Password%20Spraying.md)                                                                                                               |
| T1110.004     | Credential Stuffing | [[Password Tools]]                                                                                                                                                   |
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
| T1558.001     | Golden Ticket   | [[Golden Ticket]]   |
| T1558.002     | Silver Ticket   |                     |
| T1558.003     | Kerberoasting   | [[Kerberoasting]]   |
| T1558.004     | AS-REP Roasting | [[AS-REP Roasting]] |
| T1558.005     | Ccache Files    |                     |

## T1539: Steal Web Session Cookie
Steal web application or service session cookie to gain access to web applications or Internet services as an authenticated user without needing credentials https://attack.mitre.org/techniques/T1539/
**NOTES**:
- Session Hijacking: [[XSS]]
- Stealing Browser Cookies: [[Credential Dumping]]

## T1552: Unsecured Credentials
Finding stored credentials on compromised systems https://attack.mitre.org/techniques/T1552/

| Sub-Technique | Name                        | Notes                                                                  |
| ------------- | --------------------------- | ---------------------------------------------------------------------- |
| T1552.001     | Credentials in Files        | [[Windows Credential Hunting]], [[Linux Credential Hunting]]           |
| T1552.002     | Credentials in Registry     |                                                                        |
| T1552.003     | Shell History               | [[Windows Credential Hunting]], [[Linux Credential Hunting]]           |
| T1552.004     | Private Keys                | [[SSH]]                                                                |
| T1552.005     | Cloud Instance Metadata API | N/A                                                                    |
| T1552.006     | Group Policy Preferences    | [GPP - cPassword Attacks](Techniques/GPP%20-%20cPassword%20Attacks.md) |
| T1552.007     | Container API               | N/A                                                                    |
| T1552.008     | Chat Messages               | N/A                                                                    |

# Lateral Movement
## T1550: Use Alternate Authentication Material
T1550.002: [Pass the Hash](Techniques/Pass-The-Hash.md)
T1550.003: Pass the Ticket

| Sub-Technique | Name            | Notes                                        |
| ------------- | --------------- | -------------------------------------------- |
| T1550.001     |                 |                                              |
| T1550.002     | Pass the Hash   | [Pass the Hash](Techniques/Pass-The-Hash.md) |
| T1550.003     | Pass the Ticket |                                              |
