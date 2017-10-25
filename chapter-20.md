# Sessions: remote control with less work

1) Close all open sessions in your shell.
```powershell
Get-PSSession | Remove-PSSession
```
---

2) Establish a session to a remote computer. Save the session in a variable named $session.
```powershell
$session = New-PSSession -ComputerName winserver
```
---

3) Use the $session variable to establish a one-to-one remote shell session with the remote computer. Display a list of processes and then exit.
```powershell
Enter-PSSession -Session $session
```
```powershell
Get-Process
```
```powershell
Exit-PSSession
```
---

4) Use the $session variable with Invoke-Command to get a list of services from the remote computer.
```powershell
Invoke-Command -ScriptBlock {Get-Service} -Session $session
```
---

5) Use Get-PSSession and Invoke-Command to get a list of the 20 most recent Security event log entries from the remote computer.
```powershell
Invoke-Command -ScriptBlock {Get-EventLog -Newest 20 -LogName Security} -Session (Get-PSSession)
```
---

6) Use Invoke-Command and your $session variable to load the ServerManager module on the remote computer.
```powershell
Invoke-Command -ScriptBlock {Import-Module ServerManager} -Session $session
```
---

7) Import the ServerManager module’s commands from the remote computer to your computer. Add the prefix rem to the imported commands’ nouns.
```powershell
Import-PSSession -Session $session -Module ServerManager -Prefix rem
```
---

8) Run the imported Get-WindowsFeature command.
```powershell
Get-remWindowsFeature
```
---

9) Close the session that’s in your $session variable.
```powershell
Remove-PSSession $session
```