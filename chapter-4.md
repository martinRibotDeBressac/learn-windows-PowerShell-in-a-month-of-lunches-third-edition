1) Display a list of running processes.
```powershell
get-process
```
----------
2) Display the 100 most recent entries from the Application event log. (Don’t use Get-WinEvent for this. We’ve shown you another command that will do this task.) This is for Windows operating systems only.
```powershell
Get-EventLog -Newest 100 -LogName Application
```
----------

3) Display a list of all commands that are of the cmdlet type. (This is tricky—we’ve shown you Get-Command, but you’re going to have to read the help to find out how to narrow down the list as we’ve asked.)
```powershell
Get-Command -CommandType Cmdlet
```
`output:`
```
    CommandType     Name                                               ModuleName
    -----------     ----                                               ----------
    Cmdlet          Add-BitsFile                                       BitsTransfer
    Cmdlet          Add-Computer                                       Microsoft.PowerShell.Management
    Cmdlet          Add-Content                                        Microsoft.PowerShell.Management
    Cmdlet          Add-History                                        Microsoft.PowerShell.Core
    Cmdlet          Add-JobTrigger                                     PSScheduledJob
    Cmdlet          Add-Member                                         Microsoft.PowerShell.Utility
    Cmdlet          Add-PSSnapin                                       Microsoft.PowerShell.Core
    Cmdlet          Add-Type                                           Microsoft.PowerShell.Utility
```
----------

4) Display a list of all aliases.
```powershell
Get-Alias
```
`output:`
```
    CommandType     Name                                               ModuleName
    -----------     ----                                               ----------
    Alias           % -> ForEach-Object
    Alias           ? -> Where-Object
    Alias           ac -> Add-Content
    Alias           asnp -> Add-PSSnapin
    Alias           cat -> Get-Content
    Alias           cd -> Set-Location
    Alias           chdir -> Set-Location
    Alias           clc -> Clear-Content
    Alias           clear -> Clear-Host
    Alias           clhy -> Clear-History
    Alias           cli -> Clear-Item
    Alias           clp -> Clear-ItemProperty
    Alias           cls -> Clear-Host
    Alias           clv -> Clear-Variable
    Alias           cnsn -> Connect-PSSession
```
----------

5) Make a new alias, so you can run np to launch Notepad from a PowerShell prompt. This is for Windows only unless you’ve installed wine on Linux.
```powershell
New-Alias -Name np -Value Notepad
```
----------

6) Display a list of services that begin with the letter M. Again, read the help for the necessary command—and don’t forget that the asterisk (*) is a near-universal wildcard in PowerShell. Note that this will work only on Windows operating -systems.
```powershell
Get-Service -Name M*
```
----------

7) Display a list of all Windows Firewall rules. You’ll need to use Help or Get-Command to discover the necessary cmdlet. Again, this will work only on Windows operating systems.
```powershell
get-help *firewall*
```
`output:`
```
    Name                              Category  Module                    Synopsis
    ----                              --------  ------                    --------
    Copy-NetFirewallRule              Function  NetSecurity               ...
    Disable-NetFirewallRule           Function  NetSecurity               ...
    Enable-NetFirewallRule            Function  NetSecurity               ...
    Get-NetFirewallAddressFilter      Function  NetSecurity               ...
    Get-NetFirewallApplicationFilter  Function  NetSecurity               ...
    Get-NetFirewallInterfaceFilter    Function  NetSecurity               ...
    Get-NetFirewallInterfaceTypeFi... Function  NetSecurity               ...
    Get-NetFirewallPortFilter         Function  NetSecurity               ...
    Get-NetFirewallProfile            Function  NetSecurity               ...
    Get-NetFirewallRule               Function  NetSecurity               ...
    Get-NetFirewallSecurityFilter     Function  NetSecurity               ...
    Get-NetFirewallServiceFilter      Function  NetSecurity               ...
```
```powershell
Get-Help Get-NetFirewallRule
```
`output:`
```
    NAME
        Get-NetFirewallRule

    SYNOPSIS
        Retrieves firewall rules from the target computer.


```
----------

8) Display a list of all Windows Firewall rules. You’ll need to use Help or Get-Command to discover the necessary cmdlet. Again, this will work only on Windows operating systems.
```powershell
Get-Help Get-NetFirewallRule -Detailed
```
`output:`
```
    -Direction <Direction[]>
        Specifies that matching firewall rules of the indicated direction are retrieved.
                                    
        This parameter specifies which direction of traffic to match with this rule.
        The acceptable values for this parameter are:  Inbound or Outbound.

        The default value is Inbound.


```
```powershell
Get-NetFirewallRule -Direction Inbound
```