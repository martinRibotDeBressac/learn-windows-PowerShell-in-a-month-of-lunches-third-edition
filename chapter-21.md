1) The following command is for you to add to a script. You should first identify any elements that should be parameterized, such as the computer name. Your final script should define the parameter, and you should create comment-based help within the script. Run your script to test it, and use the Help command to make sure your -comment-based help works properly. Don’t forget to read the help files referenced within this chapter for more information. 

Here’s the command:

`Example`
```powershell
Get-WmiObject Win32_LogicalDisk -comp $env:computername -filter "drivetype=3" |
Where { ($_.FreeSpace / $_.Size) -lt .1 } |
Select -Property DeviceID,FreeSpace,Size
```

### Answer

```powershell
<#
.Description
Gets the drives of the machine that are lower then the minimum percent of size space specified
.Parameter computerName
The machine that this script will run
.Parameter minimumFreePercent
The minimum percent of free space, drives with less space will come up
#>

param(
$computerName = "localhost",
$minimumFreePercent = 10
)

$minimumFreePercent = $minimumFreePercent / 100

Get-WmiObject Win32_LogicalDisk -comp $computername -filter "drivetype=3" | Where-Object { ($_.FreeSpace / $_.Size) -lt $minimumFreePercent } | Select-Object -Property DeviceID,FreeSpace,Size
```