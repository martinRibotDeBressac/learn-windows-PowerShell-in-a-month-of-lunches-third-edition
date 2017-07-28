1. Display a list of running processes.

    get-process

    Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
    -------  ------    -----      ----- -----   ------     -- -----------
        102      12     3108       8172    58     0.34   1508 ac.sharedstore
        233      22     7176      15444   107     0.17   5084 accrdsub
        132      16     4668      10284    70     2.05   1544 acevents
        149      17     4976      11788    91     2.33   4956 acevents
        194      19     5768      12980   100     0.17   5052 acsagent
        321      34     9720      20708   104     0.78   2768 AppVClient
        200      33    30728      33216   604     0.56   4680 AppVStreamingUX
         73       8     1304       4148    43     0.47   1928 armsvc
         98      11     5360       8856   174     0.05   3504 atom
        375      58   284932     339624  1237   706.91   4088 atom

##############################

2. Display the 100 most recent entries from the Application event log. (Don’t use Get-WinEvent for this. We’ve shown you another command that will do this task.) This is for Windows operating systems only.

    Get-EventLog -Newest 100 -LogName Application

       Index Time          EntryType   Source                 InstanceID Message
       ----- ----          ---------   ------                 ---------- -------
      189969 May 17 10:40  Error       AutoEnrollment         1073741830 The description for Event ID '1073741830' in Source 'AutoEnrollment' cannot be found.  The local computer may not have the necessary registry information or me...
      189968 May 17 10:39  0           Software Protecti...   1073742727 The Software Protection service has stopped....
      189967 May 17 10:39  Information Software Protecti...   1073758208 Successfully scheduled Software Protection service for re-start at 2017-05-19T09:01:27Z. Reason: GVLK.
      189966 May 17 10:34  0           Software Protecti...   1073742726 The Software Protection service has started....
      189965 May 17 10:34  Information Software Protecti...   1073742827 The Software Protection service has completed licensing status check....
      189964 May 17 10:34  Information Software Protecti...   1073742890 Initialization status for service objects....
      189963 May 17 10:34  Information Software Protecti...   1073742724 The Software Protection service is starting....
      189962 May 17 10:26  Information Wlclntfy               2147489648 The winlogon notification subscriber <VMWVvpsvc> was unavailable to handle a notification event.
      189961 May 17 10:02  0           Software Protecti...   1073742727 The Software Protection service has stopped....
      189960 May 17 10:02  Information Software Protecti...   1073758208 Successfully scheduled Software Protection service for re-start at 2017-05-19T09:02:18Z. Reason: GVLK.
      189959 May 17 09:57  0           Software Protecti...   1073742726 The Software Protection service has started....
      189958 May 17 09:57  Information Software Protecti...   1073742827 The Software Protection service has completed licensing status check....
      189957 May 17 09:57  Information Software Protecti...   1073742890 Initialization status for service objects....

##############################

3. Display a list of all commands that are of the cmdlet type. (This is tricky—we’ve shown you Get-Command, but you’re going to have to read the help to find out how to narrow down the list as we’ve asked.)

    Get-Command -CommandType Cmdlet

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

##############################

4. Display a list of all aliases.

    Get-Alias

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

##############################

5. Make a new alias, so you can run np to launch Notepad from a PowerShell prompt. This is for Windows only unless you’ve installed wine on Linux.

    New-Alias -Name np -Value Notepad

##############################

6. Display a list of services that begin with the letter M. Again, read the help for the necessary command—and don’t forget that the asterisk (*) is a near-universal wildcard in PowerShell. Note that this will work only on Windows operating -systems.

    Get-Service -Name M*

    Status   Name               DisplayName
    ------   ----               -----------
    Running  MMCSS              Multimedia Class Scheduler
    Running  MpsSvc             Windows Firewall
    Running  MSDTC              Distributed Transaction Coordinator
    Stopped  MSiSCSI            Microsoft iSCSI Initiator Service
    Stopped  msiserver          Windows Installer
    Running  MsMpSvc            Microsoft Antimalware Service

##############################

7. Display a list of all Windows Firewall rules. You’ll need to use Help or Get-Command to discover the necessary cmdlet. Again, this will work only on Windows operating systems.

    get-help *firewall*

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

    Get-Help Get-NetFirewallRule

    NAME
        Get-NetFirewallRule

    SYNOPSIS
        Retrieves firewall rules from the target computer.



##############################

8. Display a list of all Windows Firewall rules. You’ll need to use Help or Get-Command to discover the necessary cmdlet. Again, this will work only on Windows operating systems.

    Get-Help Get-NetFirewallRule -Detailed


        -Direction <Direction[]>
            Specifies that matching firewall rules of the indicated direction are retrieved.
                                     
            This parameter specifies which direction of traffic to match with this rule.
            The acceptable values for this parameter are:  Inbound or Outbound.

            The default value is Inbound.



    Get-NetFirewallRule -Direction Inbound


    Name                  : vm-monitoring-dcom
    DisplayName           : Virtual Machine Monitoring (DCOM-In)
    Description           : Allow DCOM traffic for remote Windows Management Instrumentation.
    DisplayGroup          : Virtual Machine Monitoring
    Group                 : @icsvc.dll,-700
    Enabled               : False
    Profile               : Any
    Platform              : {}
    Direction             : Inbound
    Action                : Allow
    EdgeTraversalPolicy   : Block
    LooseSourceMapping    : False
    LocalOnlyMapping      : False
    Owner                 :
    PrimaryStatus         : OK
    Status                : The rule was parsed successfully from the store. (65536)
    EnforcementStatus     : NotApplicable
    PolicyStoreSource     : PersistentStore
    PolicyStoreSourceType : Local

    Name                  : vm-monitoring-icmpv4
    DisplayName           : Virtual Machine Monitoring (Echo Request - ICMPv4-In)
    Description           : Echo Request messages are sent as ping requests to other nodes.
    DisplayGroup          : Virtual Machine Monitoring
    Group                 : @icsvc.dll,-700
    Enabled               : False
    Profile               : Any
    Platform              : {}
    Direction             : Inbound
    Action                : Allow
    EdgeTraversalPolicy   : Block
    LooseSourceMapping    : False
    LocalOnlyMapping      : False
    Owner                 :
    PrimaryStatus         : OK
    Status                : The rule was parsed successfully from the store. (65536)
    EnforcementStatus     : NotApplicable
    PolicyStoreSource     : PersistentStore
    PolicyStoreSourceType : Local
