# Multitasking with background jobs

1) Create a one-time background job to find all the PowerShell scripts on the C: drive. Any task that might take a long time to complete is a great candidate for a job.
```powershell
start-job -ScriptBlock {get-c C:\ -Recurse -Filter *.ps1}
```
---

2) You realize it would be helpful to identify all PowerShell scripts on some of your servers. How would you run the same command from task 1 on a group of remote computers?
```powershell
Invoke-Command -AsJob -ComputerName localhost,winserver -ScriptBlock {Get-ChildItem C:\ -Recurse -Filter *.ps1}
```
---

3) Create a background job that will get the latest 25 errors from the system event log on your computer and export them to a CliXML file. You want this job to run every day, Monday through Friday, at 6 a.m., in order for it to be ready for you to look at when you come in to work.
```powershell
Register-ScheduledJob -name "System Event Logs" -ScriptBlock {Get-EventLog -LogName System -Newest 25 | Export-Clixml} -Trigger (New-JobTrigger -At 6am -Weekly -DaysOfWeek Monday,Tuesday,Wednesday,Thursday,Friday)
```
---

4) What cmdlet would you use to get the results of a job, and how would you save the results in the job queue?
```powershell
Receive-Job -Keep -Id 3
```