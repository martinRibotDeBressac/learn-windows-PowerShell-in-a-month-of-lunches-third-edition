1) This lab requires you to recall some of what you learned in chapter 21, because you’ll be taking the following command, parameterizing it, and turning it into a script—just as you did for the lab in chapter 21. But this time we also want you to make the --computerName parameter mandatory and give it a hostname alias. Have your script display verbose output before and after it runs this command, too. Remember, you have to parameterize the computer name—but that’s the only thing you have to parameterize in this case.

Be sure to run the command as is before you start modifying it, to make sure it works on your system:

`example`
```powershell
get-wmiobject win32_networkadapter -computername localhost |
 where { $_.PhysicalAdapter } |
 select MACAddress,AdapterType,DeviceID,Name,Speed
```
To reiterate, here’s your complete task list:

- Make sure the command runs as is before modifying it.
- Parameterize the computer name.
- Make the computer name parameter mandatory.
- Give the computer name parameter an alias, hostname.
- Add comment-based help with at least one example of how to use the script.
- Add verbose output before and after the modified command.
- Save the script as Get-PhysicalAdapters.ps1.

### Answer

`Get-PhysicalAdapters.ps1`
```powershell
<#
.Description
This script is for outputing network adapter infomation
.Parameter computerName
The computer this script will query
.Example
./network.ps1 -computerName localhost

#>

[CmdletBinding()]
param(
[Parameter(Mandatory=$True)]
[Alias("hostname")]
[string]$computerName



)
Write-Verbose -Message "Querying $computerName for network adapters"
get-wmiobject win32_networkadapter -computername $computerName | where { $_.PhysicalAdapter } | select MACAddress,AdapterType,DeviceID,Name,Speed
Write-Verbose -Message "Query Sucessful!"
```

`get-help output`

```powershell
Get-Help .\Get-PhysicalAdapters.ps1 -Detailed

NAME
    C:\Users\debressa\Documents\Get-PhysicalAdapters.ps1
    
SYNOPSIS
    
    
SYNTAX
    C:\Users\debressa\Documents\Get-PhysicalAdapters.ps1 [-computerName] <String> [<CommonParameters>]
    
    
DESCRIPTION
    This script is for outputing network adapter infomation
    

PARAMETERS
    -computerName <String>
        The computer this script will query
        
    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see 
        about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216). 
    
    -------------------------- EXAMPLE 1 --------------------------
    
    PS C:\>./network.ps1 -computerName localhost
    
    
    
    
    
    
REMARKS
    To see the examples, type: "get-help C:\Users\debressa\Documents\Get-PhysicalAdapters.ps1 
    -examples".
    For more information, type: "get-help C:\Users\debressa\Documents\Get-PhysicalAdapters.ps1 
    -detailed".
    For technical information, type: "get-help C:\Users\debressa\Documents\Get-PhysicalAdapters.ps1 
    -full".
```