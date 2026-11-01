## Background

- Group Policy Preferences (GPP) allowed admins to create policies with embedded credentials.
- These credentials were encrypted and placed in a “cPassword”, the key was accidentally released, allowing these “cPassword” to be decrypted.
- Location of these GPP files are within the **SYSVOL of the DC.**
- Patch is MS14-025 but it **doesn’t prevent previous uses**, may still be relevant.
- Should be in the Groups.xml file

## Attack

Locate the GPP file in the SYSVOL, could be in other Groups directories.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/87ef5288-5a42-4f2f-ba67-7679fc647188/7afd769a-f9b0-4639-8abc-c36cab429661/Untitled.png)

- Decrypting the cpassword

```powershell
gpp-decrypt <enc pass>
```

- Metasploit automated enumeration and decryption

```powershell
auxiliary/scanner/smb/smb_enum_gpp
```

## Mitigations

- Already patched! Fixed in KB2962486
- Delete the old GPP xml files stored in the SYSVOL