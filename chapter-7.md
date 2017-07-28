1. Run the Networking troubleshooting pack.

    Get-Command *module*

    CommandType     Name                                               ModuleName
    -----------     ----                                               ----------
    Function        ImportSystemModules
    Cmdlet          Export-ModuleMember                                Microsoft.PowerShell.Core
    Cmdlet          Get-Module                                         Microsoft.PowerShell.Core
    Cmdlet          Import-Module                                      Microsoft.PowerShell.Core
    Cmdlet          New-Module                                         Microsoft.PowerShell.Core
    Cmdlet          New-ModuleManifest                                 Microsoft.PowerShell.Core
    Cmdlet          Remove-Module                                      Microsoft.PowerShell.Core
    Cmdlet          Test-ModuleManifest                                Microsoft.PowerShell.Core


    Get-Module *troubleshoot* -ListAvailable


        Directory: C:\Windows\system32\WindowsPowerShell\v1.0\Modules


    ModuleType Version    Name                                ExportedCommands
    ---------- -------    ----                                ----------------
    Manifest   1.0.0.0    TroubleshootingPack                 {Get-TroubleshootingPack, Invoke-Troubles...


    Import-Module TroubleshootingPack


    Get-Help Get-TroubleshootingPack -Detailed

    Example 1: Get a troubleshooting pack

        PS C:\> Get-TroubleshootingPack -Path "C:\Windows\Diagnostics\System\Audio"

        The command gets the troubleshooting pack for Audio in the specified path.




    Get-TroubleshootingPack -Path C:\Windows\diagnostics\system\Networking

    Id                        Name                                     Publisher
    --                        ----                                     ---------
    NetworkDiagnostics        Windows Network Diagnostics              Microsoft Windows


    Get-TroubleshootingPack -Path C:\Windows\diagnostics\system\Networking | Invoke-TroubleshootingPack
    Starting network diagnostics...

    Instance ID
    Not to be specified outside of MSDT application.
    :


    Select entry point
    Please select the entry point for Network Diagnostics.

    [1] Web Connectivity
    [2] File Sharing
    [3] Network Adapter
    [4] Winsock Connectivity
    [5] Grouping
    [6] Inbound
    [7] DirectAccess
    [8] DefaultConnectivity
    [9] Reserved

    [?] Help
    [x] Exit
    :1


    Please select the issue Windows should troubleshoot

    [1] Troubleshoot my connection to the Internet
    [2] Help me connect to a specific web page

    [?] Help
    [x] Exit
    :2

    Enter the address of the website you want to access
    For example, http://www.microsoft.com.
    :http://videotraining.interfacett.com

    Looking for problems...
    Looking for problems in Web connectivity...
    Collecting results...

    Collecting configuration details...


    No problems were detected
