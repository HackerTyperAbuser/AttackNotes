![[Pasted image 20261123134623.png]]
Every files downloaded is marked by Windows with MoTW to define it's trust and origin of the file. MoTW is stored hidden in the file **Alternate Data Stream (ADS)**. The MoTW is use to tag if file is unsafe. Security effects:
- **Microsoft Office**: open in Protected View and block macros or active content from untrusted sources.
- **Executable and Scripts**: Trigger Smart Screen checks and prompts or blocks execution for untrusted binaries (.exe, .dll) and scripts (.ps1, .js, .vbs).
## Bypass
https://attack.mitre.org/techniques/T1553/005/
- **No longer work** as files in ISO now inherits the mark (CVE-2022-41091)
Adversaries may abuse container files such as compressed/archive (.arj, .gzip) and/or disk image (.iso, .vhd) file formats to deliver malicious payloads that may not be tagged with MOTW. Container files downloaded from the Internet will be marked with MOTW but the files within may not inherit the MOTW after the container files are extracted and/or mounted. MOTW is an NTFS feature and many container files do not support NTFS alternative data streams. After a container file is extracted and/or mounted, the files contained within them may be treated as local files on disk and run without protections.
