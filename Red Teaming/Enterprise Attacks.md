[Kerberos](Techniques/Kerberos.md)
# Initial Access
## T1190 Exploit Public-Facing Application
https://attack.mitre.org/techniques/T1190/
**NOTES:**
- [[Web Application Attacks]]

# Privilege Escalation
https://attack.mitre.org/tactics/TA0004/
**NOTES:**
-  [[Capabilities Abuse]]
## T1548: Abuse Elevation Control Mechanism
https://attack.mitre.org/techniques/T1548/

| Sub-Technique | Name                           | Notes             |
| ------------- | ------------------------------ | ----------------- |
| T1548.001     | Setuid and Setgid              | [[SUID Binaries]] |
| T1548.002     | Bypass User Account Control    |                   |
| T1548.003     | Sudo and Sudo Caching          | [[SUDO]]          |
|               | Elevated Execution with Prompt |                   |

# Credential Access

## T1557: Adversary-in-the-Middle
https://attack.mitre.org/techniques/T1557/

| Sub-Technique | Name                                    | Notes                                                                                             |
| ------------- | --------------------------------------- | ------------------------------------------------------------------------------------------------- |
| T1557.001     | Name Resolution Poisoning and SMB Relay | [LLMNR/NBT-NS Poisoning](Techniques/LLMNR%20Poisoning.md) and [SMB Relay](Techniques/SMB%20Relay) |
| T1557.002     | Arp Cache Poisoning                     |                                                                                                   |
| T1557.003     | DHCP Spoofing                           |                                                                                                   |
| T1557.004     | Evil Twin                               |                                                                                                   |

## T1110: Brute-Force
https://attack.mitre.org/techniques/T1110/

| Sub-Technique | Name                | Notes                                  |
| ------------- | ------------------- | -------------------------------------- |
| T1110.001     | Password Guessing   | [[Password Tools]]                     |
| T1110.002     | Password Cracking   | [[Password Tools]], [[Cracking Files]] |
| T1110.003     | Password Spraying   | [[Password Spraying]]                  |
| T1110.004     | Credential Stuffing | N/A                                    |
# T1555: Credentials from Password Stores
https://attack.mitre.org/techniques/T1555/

| Sub-Technique | Name                            | Notes                                                 |
| ------------- | ------------------------------- | ----------------------------------------------------- |
| T1555.001     | Keychain                        | [[iOS Storage]]                                       |
| T1555.002     | Securityd Memory                |                                                       |
| T1555.003     | Credentials from Web Browsers   | [[Credential Dumping]]                                |
| T1555.004     | Windows Credential Manager      | [[Windows Credential Manager]] [[Credential Dumping]] |
| T1555.005     | Password Managers               | [[Cracking Files]]                                    |
| T1555.006     | Cloud Secrets Management Stores |                                                       |
## T1187: Forced Authentication
https://attack.mitre.org/techniques/T1187/
**NOTES:**
- [LNK File Attack](Techniques/LNK%20File%20Attack.md)

## T1649: Steal or Forge Authentication Certificates

## T1552: Unsecured Credentials
| Sub-Technique | Name                     | Notes   |
| ------------- | ------------------------ | ------- |
| T1552.006     | Group Policy Preferences | [[GPP - cPassword Attacks]] |


# Lateral Movement
## T1550: Use Alternate Authentication Material
T1550.002: [Pass the Hash](Techniques/Pass-The-Hash.md)
T1550.003: Pass the Ticket

| Sub-Technique | Name            | Notes                                        |
| ------------- | --------------- | -------------------------------------------- |
| T1550.001     |                 |                                              |
| T1550.002     | Pass the Hash   | [Pass the Hash](Techniques/Pass-The-Hash.md) |
| T1550.003     | Pass the Ticket |                                              |
