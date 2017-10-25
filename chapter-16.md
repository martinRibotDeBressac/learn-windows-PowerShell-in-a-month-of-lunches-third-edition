# Working with many objects, one at a time

1)
```powershell
Get-Service | gm -Name pause
```
`output:`
```
TypeName: System.ServiceProcess.ServiceController

Name  MemberType Definition  
----  ---------- ----------  
Pause Method     void Pause()
```
---

2)
```powershell
Get-Process | gm -Name kill
```
`output:`
```
TypeName: System.Diagnostics.Process

Name MemberType Definition 
---- ---------- ---------- 
Kill Method     void Kill()
```
---

3)
```powershell
Get-CimClass -ClassName Win32_Process | Select-Object -ExpandProperty CimClassMethods
```
`Look for Terminate:`

---

4) 
`1.`
```powershell
Get-Process -Name Notepad | Stop-Process
```
`2.`
```powershell
Get-Process -Name Notepad | ForEach-Object {$_.kill()}
```
`3.`
```powershell
Get-CimInstance -ClassName Win32_Process -filter "name = 'notepad.exe'" | Invoke-CimMethod -MethodName Terminate
```
`4. (It's an answer but not really practical for working with objects)`
```powershell
Stop-Process -Name Notepad
```
---

5) 
```powershell
Get-Content C:\dev\servers.txt | ForEach-Object {$_.toUpper()}
```
`output:`
```
SERVER1
SERVERB
SERVER#
REVRES3
REVRESB
REVRES!
```