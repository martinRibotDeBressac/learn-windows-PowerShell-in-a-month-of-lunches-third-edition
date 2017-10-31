# Working with providers

1) In the Registry, go to HKEY_CURRENT_USER\software\microsoft\Windows\-currentversion\explorer. Locate the Advanced key, and set its DontPrettyPath property to 1.
```powershell
Set-Location HKCU:
```
```powershell
Set-Location .\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer
```
```powershell
Set-ItemProperty -Path .\Advanced -PSProperty DontPrettyPath -Value 1
```
---

2) Create a new directory called C:\Labs.
```powershell
Set-Location C:\
```
```powershell
New-Item -Name Labs -ItemType directory
```

---

3) Create a zero-length file named C:\Labs\Test.txt (use New-Item).
```powershell
Set-Location C:\Labs
```
```powershell
New-Item -Name Test.txt -ItemType file
```
---

4. Is it possible to use Set-Item to change the contents of C:\Labs\Test.txt to TESTING? Or do you get an error? If you get an error, why?
```powershell
Set-Item .\Test.txt -Value TESTING
```
`output:`
```
    Set-Item : Provider operation stopped because the provider does not support this operation.
    At line:1 char:1
    + Set-Item .\Test.txt -Value TESTING
    + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
        + CategoryInfo          : NotImplemented: (:) [Set-Item], PSNotSupportedException
        + FullyQualifiedErrorId : NotSupported,Microsoft.PowerShell.Commands.SetItemCommand
```

---

5. Using the Environment provider, display the value of the system environment variable %TEMP%.
```powershell
Set-Location Env:
```
```powershell
get-ChildItem *TEMP*
```
`output:`
```
    Name                           Value
    ----                           -----
    TEMP                           C:\Users\debressa\AppData\Local\Temp
```
---

6. What are the differences between the -Filter, -Include, and -Exclude parameters of Get-ChildItem?
```
Include and Exclude both work after the cmdlet has retrived its objects, Filter works while the cmdlet is retriving objects
```
```
Include and Exclude both require Recurse to work, Filter doesn't require Recurse
```
```
Filter will not work in the Registry since Registry uses differing PSProvider structure
```