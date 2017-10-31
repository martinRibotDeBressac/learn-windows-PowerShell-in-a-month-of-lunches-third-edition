# Remote control: one-to-one, and one-to-many

1) Make a one-to-one connection with a remote computer (or with localhost if you have only one computer). Launch Notepad.exe. What happens?

```powershell
PS C:\Users\martin.INTERNAL> Enter-PSSession -ComputerName winserver

[winserver]: PS C:\Users\martin\Documents> Start-Process notepad.exe
[winserver]: PS C:\Users\martin\Documents> Get-Process notepad
```
---
2) Using Invoke-Command, retrieve a list of services that aren’t started from one or two remote computers (it’s OK to use localhost twice if you have only one computer). Format the results as a wide list. (Hint: it’s OK to retrieve results and have the formatting occur on your computer—don’t include the Format- cmdlets in the commands that are invoked remotely.)

```powershell
PS C:\Windows\system32> Invoke-Command {Get-Service | Where-Object {$_.Status -eq "stopped"}} -ComputerName winserver,localhost | Format-Wide -Column 4
```
---
3) Use Invoke-Command to get a list of the top 10 processes for virtual memory (VM) usage. Target one or two remote computers, if you can; if you have only one computer, target localhost twice.

```powershell
PS C:\Windows\system32> Invoke-Command {Get-Process | Sort-Object -Property VM -Descending | Select-Object -First 10} -ComputerName winserver,localhost
```
---
4) Create a text file that contains three computer names, with one name per line. It’s OK to use the same computer name, or localhost, three times if you have access to only one computer. Then use Invoke-Command to retrieve the 100 newest Application event log entries from the computer names listed in that file.
```powershell
Invoke-Command {Get-EventLog -Newest 100 -LogName Application} -ComputerName (Get-Content .\localhost-winserver-localhost.txt)
```
---
5) Using Invoke-Command, query one or more remote computers to display the properties ProductName, EditionID, and CurrentVersion from the registry key HKEY_Local_Machine\SOFTWARE\Microsoft\Windows 

```powershell
Invoke-Command {Get-ItemProperty 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\' | Select-Object -Property ProductName,EditionID,CurrentVersion} -ComputerName winserver,localhost
```