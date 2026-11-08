# Attack Notes

Personal offensive-security knowledge base — payloads, techniques, and methodology distilled for real engagements and study. Organised by engagement phase and cross-referenced to [MITRE ATT&CK](https://attack.mitre.org/).

## Domains

| Domain | Entry point |
| ------ | ----------- |
| **Web Application** | [Web Application Attacks](Web%20Application%20Pentesting/Web%20Application%20Attacks.md) |
| **Network** | [Network Pentesting](Network%20Pentesting/Network%20Pentesting.md) · [Information Gathering](Network%20Pentesting/Information%20Gathering.md) |
| **Red Teaming / AD** | [Enterprise Attacks (ATT&CK matrix)](Red%20Teaming/MITRE%20ATT%26CK%20Enterprise%20Attacks.md) · [AD Checklists](Red%20Teaming/AD%20Checklists.md) · [AD Enumeration](Red%20Teaming/AD%20Enumeration.md) |
| **Post-Exploitation** | [Windows PrivEsc](Post%20Exploitation/Windows/Windows%20Privilege%20Escalation.md) · [Linux PrivEsc](Post%20Exploitation/Linux/Linux%20Privilege%20Escalation.md) |
| **Binary Exploitation** | [32-bit x86 Stack](Binary%20Exploitation/Stack/32-bit%20x86%20Stack.md) · [Buffer Overflow](Binary%20Exploitation/BoF/Buffer%20Overflow.md) |
| **Mobile** | [Android Architecture](Mobile%20Application%20Pentesting/Android/Android%20Architecture.md) · [iOS Architecture](Mobile%20Application%20Pentesting/iOS/iOS%20Architecture.md) |
| **Wi-Fi** | [Wi-Fi Enumeration](Wi-Fi/Wi-Fi%20Enumeration.md) |

## Quick reference

- **Payloads & shells:** [Payloads & Shells](Network%20Pentesting/Payloads%20&%20Shells.md) · [File Transfers](Network%20Pentesting/File%20Transfers.md)
- **Pivoting:** [Pivoting](Network%20Pentesting/Lateral%20Movement/Pivoting.md) · [Port-Forwarding](Network%20Pentesting/Lateral%20Movement/Port-Forwarding.md)
- **Credential access:** [Credential Dumping](Post%20Exploitation/Windows/Credential%20Dumping.md) · [Password Tools](Network%20Pentesting/Passwords%20Attacks/Password%20Tools.md)
- **C2:** [Sliver](Red%20Teaming/C2/Sliver.md) · [Cobalt Strike](Red%20Teaming/C2/Cobalt%20Strike.md)

## Conventions

- Notes link with Obsidian `[[wikilinks]]` where possible; index tables use relative paths.
- A note opening with a `> [!todo] STUB` callout is a **known gap**, not finished content — see the backlog below.

## Backlog (stubs to fill)

Highest-value gaps first:

1. [Pass-The-Ticket](Red%20Teaming/Techniques/Pass-The-Ticket.md), [Golden Ticket](Red%20Teaming/Techniques/Persistence/Golden%20Ticket.md), [Pass-The-Certificate](Red%20Teaming/Techniques/Pass-The-Certificate.md) — core AD lateral movement & persistence
2. [User Account Control (UAC)](Post%20Exploitation/Windows/User%20Account%20Control%20%28UAC%29.md), [Cron Jobs](Post%20Exploitation/Linux/Cron%20Jobs.md) — common privesc
3. [SAML](Web%20Application%20Pentesting/Authentication/SAML.md), [OSTicket](Web%20Application%20Pentesting/Common%20Applications/OSTicket.md)
4. [Linux Ret2Shell](Binary%20Exploitation/BoF/Linux%20Ret2Shell.md), [Egghunter](Binary%20Exploitation/SEH/Egghunter.md)
