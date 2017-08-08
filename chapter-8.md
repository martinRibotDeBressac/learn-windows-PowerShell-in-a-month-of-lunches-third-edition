1) Identify a cmdlet that produces a random number.
```powershell
get-help *random*
```
`output:`
```
NAME
    Get-Random

SYNOPSIS
    Gets a random number, or selects objects randomly from a collection.

```
```powershell
Get-Random
```
`output:`
```
826626686
```

----------

2) Identify a cmdlet that displays the current date and time.
```powershell
Get-Help *date*
```
`output:`
```
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Update-Help                       Cmdlet    Microsoft.PowerShell.Core Downloads and installs th...
Get-Date                          Cmdlet    Microsoft.PowerShell.U... Gets the current date and...
Set-Date                          Cmdlet    Microsoft.PowerShell.U... Changes the system time o...
Update-FormatData                 Cmdlet    Microsoft.PowerShell.U... Updates the formatting da...
Update-List                       Cmdlet    Microsoft.PowerShell.U... Adds items to and removes...
Update-TypeData                   Cmdlet    Microsoft.PowerShell.U... Updates the extended type...
```
```powershell
get-date
```
`output:`
```
Thursday, 1 June 2017 2:04:25 PM
```

----------

3. What type of object does the cmdlet from task 2 produce? (What is the type name of the object produced by the cmdlet?)
```powershell
get-date | Get-Member
```
```
    TypeName: System.DateTime

Name                 MemberType     Definition
----                 ----------     ----------
Add                  Method         datetime Add(timespan value)
AddDays              Method         datetime AddDays(double value)
AddHours             Method         datetime AddHours(double value)
```
----------
4) Using the cmdlet from task 2 and Select-Object, display only the current day of the week in a table like the following (Caution: the output will right-align, so make sure your PowerShell window doesn’t have a horizontal scrollbar):
DayOfWeek
.---------
Monday
```powershell
    get-date | Select-Object -Property DayOfWeek
```
`output:`
```
      DayOfWeek
      ---------
       Thursday
```

----------

5) Identify a cmdlet that displays information about installed hotfixes on Windows systems.
```powershell
get-help *fix*
```
```
NAME
    Get-HotFix

SYNOPSIS
    Gets the hotfixes that have been applied to the local and remote computers.
```

----------

6) Using the cmdlet from task 5, display a list of installed hotfixes. Then extend the expression to sort the list by the installation date, and display only the installation date, the user who installed the hotfix, and the hotfix ID. Remember that the column headers shown in a command’s default output aren’t necessarily the real property names—you need to look up the real property names to be sure.
```powershell
Get-HotFix | Sort-Object InstalledOn | Select-Object InstalledOn,InstalledBy,HotFixID
```
```
    InstalledOn                      InstalledBy                      HotFixID
    -----------                      -----------                      --------
    12/05/2014 12:00:00 AM           VM106850FC\Support               KB2888049
    12/05/2014 12:00:00 AM           VM106850FC\Support               KB2834140
    12/05/2014 12:00:00 AM           VM106850FC\Support               KB2809215
    12/05/2014 12:00:00 AM           VM106850FC\Support               KB2775511
    12/05/2014 12:00:00 AM           VM106850FC\Support               KB2718654
    12/05/2014 12:00:00 AM           VM106850FC\Support               KB2758949
    12/05/2014 12:00:00 AM           VM106850FC\Support               KB2732673
```
----------

7) Repeat task 6, but this time sort the results by the hotfix description, and include the description, the hotfix ID, and the installation date. Put the results into an HTML file.
```powershell
Get-HotFix | Sort-Object Description | Select-Object Description,HotFixID,InstalledOn | ConvertTo-Html | Out-File -FilePath C:\workCode\TestOutput\hotfix.html
```
----------

8) Display a list of the 50 newest entries from the Security event log (you can use a different log, such as System or Application, if your Security log is empty). Sort the list with the oldest entries appearing first, and with entries made at the same time sorted by their index. Display the index, time, and source for each entry. Put this information into a text file (not an HTML file, but a plain-text file). You may be tempted to use Select-Object and its -first or -last parameters to achieve this; don’t. There’s a better way. Also, avoid using Get-WinEvent for now; a better cmdlet is available for this particular task.
```powershell
Get-EventLog -Newest 50 -LogName Security | Sort-Object -Property TimeGenerated,EventID | Select Index,TimeGenerated,Source | Out-File C:\workCode\TestOutput\output.txt
```