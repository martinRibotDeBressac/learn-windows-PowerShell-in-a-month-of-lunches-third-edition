# Using the help system

1) Run Update-Help and ensure that it completes without errors, so that you have a copy of the help on your local computer. You need an internet connection, and the shell needs to run under elevated privileges (which means Administrator must appear in the shell window’s title bar).
```powershell
update-help
```
---
2) Windows-only: can you find any cmdlets capable of converting other cmdlets’ output into HTML?
```powershell
get-help *html*
```
`output:`
```
    NAME
        ConvertTo-Html

    SYNOPSIS
        Converts Microsoft .NET Framework objects into HTML that can be displayed in a Web browser.
```
---
3) Partially Windows-only: are there any cmdlets that can redirect output into a file, or to a printer?
```powershell
get-help *output*
```
`output:`
```
    Name                              Category  Module                    Synopsis
    ----                              --------  ------                    --------
    Write-Output                      Cmdlet    Microsoft.PowerShell.U... Sends the specified objects to the next command in the pipeline. If the command is the last command in the pipeline, the objects are...
    about_Functions_OutputTypeAttr... HelpFile                            Describes an attribute that reports the type of object that the function
    about_Remote_Output               HelpFile                            Describes how to interpret and format the output of remote commands.

    NAME
        Write-Output

    SYNOPSIS
        Sends the specified objects to the next command in the pipeline. If the command is the last
        command in the pipeline, the objects are displayed in the console.
```
---
4) How many cmdlets are available for working with processes? (Hint: remember that cmdlets all use a singular noun.)
```powershell
get-help *process*
```
`output:`
```
    Name                              Category  Module                    Synopsis
    ----                              --------  ------                    --------
    Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or more processes running on the local computer.
    Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the processes that are running on the local computer or a remote computer.
    Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or more processes on the local computer.
    Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or more running processes.
    Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the processes to be stopped before accepting more input.
```
---
5) What cmdlet might you use to write to an event log? (This one’s possible on non-Windows operating systems, but you’ll get a different answer.)
```powershell
get-help *eventlog*
```
`output:`
```
    Name                              Category  Module                    Synopsis
    ----                              --------  ------                    --------
    Clear-EventLog                    Cmdlet    Microsoft.PowerShell.M... Deletes all entries from specified event logs on the local or remote computers.
    Get-EventLog                      Cmdlet    Microsoft.PowerShell.M... Gets the events in an event log, or a list of the event logs, on the local or remote computers.
    Limit-EventLog                    Cmdlet    Microsoft.PowerShell.M... Sets the event log properties that limit the size of the event log and the age of its entries.
    New-EventLog                      Cmdlet    Microsoft.PowerShell.M... Creates a new event log and a new event source on a local or remote computer.
    Remove-EventLog                   Cmdlet    Microsoft.PowerShell.M... Deletes an event log or unregisters an event source.
    Show-EventLog                     Cmdlet    Microsoft.PowerShell.M... Displays the event logs of the local or a remote computer in Event Viewer.
    Write-EventLog                    Cmdlet    Microsoft.PowerShell.M... Writes an event to an event log.
    about_Eventlogs                   HelpFile                            Windows PowerShell creates a Windows event log that is
```
```powershell
get-help Write-EventLog
```
`output:`
```
    NAME
        Write-EventLog

    SYNOPSIS
        Writes an event to an event log.
```
---
6) You’ve learned that aliases are nicknames for cmdlets; what cmdlets are available to create, modify, export, or import aliases?
```powershell
get-help *alias*
```
`output:`
```
    Name                              Category  Module                    Synopsis
    ----                              --------  ------                    --------
    Export-Alias                      Cmdlet    Microsoft.PowerShell.U... Exports information about currently defined aliases to a file.
    Get-Alias                         Cmdlet    Microsoft.PowerShell.U... Gets the aliases for the current session.
    Import-Alias                      Cmdlet    Microsoft.PowerShell.U... Imports an alias list from a file.
    New-Alias                         Cmdlet    Microsoft.PowerShell.U... Creates a new alias.
    Set-Alias                         Cmdlet    Microsoft.PowerShell.U... Creates or changes an alias (alternate name) for a cmdlet or other command element in the current Windows PowerShell session.
    Alias                             Provider  Microsoft.PowerShell.Core Provides access to the Windows PowerShell aliases and the values that they represent.
    about_Aliases                     HelpFile                            Describes how to use alternate names for cmdlets and commands in Windows
```
---
7) Is there a way to keep a transcript of everything you type in the shell, and save that transcript to a text file?
```powershell
get-help *transcript*
```
`output:`
```
    Name                              Category  Module                    Synopsis
    ----                              --------  ------                    --------
    Start-Transcript                  Cmdlet    Microsoft.PowerShell.Host Start-Transcript...
    Stop-Transcript                   Cmdlet    Microsoft.PowerShell.Host Stop-Transcript...
```
```powershell
get-help Start-Transcript -detailed
```
`output:`
```
    -------------------------- EXAMPLE 2 --------------------------

        PS C:\>start-transcript -path c:\transcripts\transcript0.txt -noclobber

        This command starts a transcript in the Transcript0.txt file in C:\transcripts. The NoClobber parameter prevents any existing files from being overwritten. If the Transcript0.txt file already exists,
        the command fails.
```
---
8) Windows-only: it can take a long time to retrieve all of the entries from the Security event log. How can you get only the 100 most recent entries?
```powershell
get-help Get-EventLog -Detailed
```
`output:`
```
    NAME
        Get-EventLog

    SYNOPSIS
        Gets the events in an event log, or a list of the event logs, on the local or remote computers.

    -------------------------- EXAMPLE 2 --------------------------

        PS C:\>get-eventlog -newest 5 -logname application

        This command gets the five most recent entries from the Application event log.

**Change newest to 100 and logname to security**
```
---
9) Windows-only: is there a way to retrieve a list of the services that are installed on a remote computer?
```powershell
Get-Help *service*
```
`output:`
```

    Name                              Category  Module                    Synopsis
    ----                              --------  ------                    --------
    Get-Service                       Cmdlet    Microsoft.PowerShell.M... Gets the services on a local or remote computer.
    New-Service                       Cmdlet    Microsoft.PowerShell.M... Creates a new Windows service.
    New-WebServiceProxy               Cmdlet    Microsoft.PowerShell.M... Creates a Web service proxy object that lets you use and manage the Web service in Windows PowerShell.
    Restart-Service                   Cmdlet    Microsoft.PowerShell.M... Stops and then starts one or more services.
    Resume-Service                    Cmdlet    Microsoft.PowerShell.M... Resumes one or more suspended (paused) services.
    Set-Service                       Cmdlet    Microsoft.PowerShell.M... Starts, stops, and suspends a service, and changes its properties.
    Start-Service                     Cmdlet    Microsoft.PowerShell.M... Starts one or more stopped services.
    Stop-Service                      Cmdlet    Microsoft.PowerShell.M... Stops one or more running services.
    Suspend-Service                   Cmdlet    Microsoft.PowerShell.M... Suspends (pauses) one or more running services.

Get-Help Get-Service -Detailed

    NAME
        Get-Service

    SYNOPSIS
        Gets the services on a local or remote computer.

    -------------------------- EXAMPLE 6 --------------------------

        PS C:\>get-service -computername Server02

        This command gets the services on the Server02 remote computer.

        Because the ComputerName parameter of Get-Service does not use Windows PowerShell remoting, you can use this parameter even if the computer is not configured for remoting in Windows PowerShell.
```
---
10. Is there a way to see what processes are running on a remote computer? (You can find the answer on non-Windows operating systems, but the command itself might not work for you.)
```powershell
get-help Get-Process -Detailed
```
`output:`
```
    NAME
        Get-Process

    SYNOPSIS
        Gets the processes that are running on the local computer or a remote computer.

    PARAMETERS
        -ComputerName <String[]>
            Gets the processes running on the specified computers. The default is the local computer.

            Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more computers. To specify the local computer, type the computer name, a dot (.), or "localhost".

            This parameter does not rely on Windows PowerShell remoting. You can use the ComputerName parameter of Get-Process even if your computer is not configured to run remote commands.
```
---
11) Examine the help file for the Out-File cmdlet. The files created by this cmdlet default to a width of how many characters? Is there a parameter that would enable you to change that width?
```powershell
Get-Help Out-File -Detailed
```
`output:`
```
    NAME
        Out-File

    SYNOPSIS
        Sends output to a file.

    -Width <Int32>
        Specifies the number of characters in each line of output. Any additional characters are truncated, not wrapped. If you omit this parameter, the width is determined by the characteristics of the host. The default for the
        Windows PowerShell console is 80 (characters).
```
---
12) By default, Out-File overwrites any existing file that has the same filename as what you specify. Is there a parameter that would prevent the cmdlet from overwriting an existing file?
```powershell
Get-Help Out-File -Detailed
```
`output:`
```
    NAME
        Out-File

    SYNOPSIS
        Sends output to a file.

    -NoClobber [<SwitchParameter>]
        Will not overwrite (replace the contents) of an existing file. By default, if a file exists in the specified path, Out-File overwrites the file without warning. If both Append and NoClobber are used, the output is appended
        to the existing file.
```
---
13) How could you see a list of all aliases defined in PowerShell?
```powershell
get-help *alias*
```
`output:`
```
    Name                              Category  Module                    Synopsis
    ----                              --------  ------                    --------
    Export-Alias                      Cmdlet    Microsoft.PowerShell.U... Exports information about currently defined aliases to a file.
    Get-Alias                         Cmdlet    Microsoft.PowerShell.U... Gets the aliases for the current session.
    Import-Alias                      Cmdlet    Microsoft.PowerShell.U... Imports an alias list from a file.
    New-Alias                         Cmdlet    Microsoft.PowerShell.U... Creates a new alias.
    Set-Alias                         Cmdlet    Microsoft.PowerShell.U... Creates or changes an alias (alternate name) for a cmdlet or other command element in the current Windows PowerShell session.
    Alias                             Provider  Microsoft.PowerShell.Core Provides access to the Windows PowerShell aliases and the values that they represent.
    about_Aliases                     HelpFile                            Describes how to use alternate names for cmdlets and commands in Windows
```
```powershell
get-help Get-Alias
```
`output:`
```
    NAME
        Get-Alias

    SYNOPSIS
        Gets the aliases for the current session.

```
---
14) Using both an alias and abbreviated parameter names, what is the shortest command line you could type to retrieve a list of running processes from a computer named Server1?
```powershell
Get-Alias
```
`output:`
```
    Alias           ps -> Get-Process
```
```powershell
Get-Help ps
```
`output:`
```
    NAME
        Get-Process

    SYNOPSIS
        Gets the processes that are running on the local computer or a remote computer.


    SYNTAX
        Get-Process [[-Name] <String[]>] [-ComputerName <String[]>] [-FileVersionInfo] [-Module] [<CommonParameters>]
```
```powershell
ps -c Server1
```
---
15) How many cmdlets are available that can deal with generic objects? (Hint: remember to use a singular noun like object rather than a plural one like objects.)
```powershell
get-help *object*
```
`output:`
```
    Name                              Category  Module                    Synopsis
    ----                              --------  ------                    --------
    ForEach-Object                    Cmdlet    Microsoft.PowerShell.Core Performs an operation against each item in a collection of input objects.
    Where-Object                      Cmdlet    Microsoft.PowerShell.Core Selects objects from a collection based on their property values.
    Get-WmiObject                     Cmdlet    Microsoft.PowerShell.M... Gets instances of Windows Management Instrumentation (WMI) classes or information about the available classes.                                                   
    Remove-WmiObject                  Cmdlet    Microsoft.PowerShell.M... Deletes an instance of an existing Windows Management Instrumentation (WMI) class.
    Compare-Object                    Cmdlet    Microsoft.PowerShell.U... Compares two sets of objects.
    Group-Object                      Cmdlet    Microsoft.PowerShell.U... Groups objects that contain the same value for specified properties.
    Measure-Object                    Cmdlet    Microsoft.PowerShell.U... Calculates the numeric properties of objects, and the characters, words, and lines in string objects, such as files of text.
    New-Object                        Cmdlet    Microsoft.PowerShell.U... Creates an instance of a Microsoft .NET Framework or COM object.
    Register-ObjectEvent              Cmdlet    Microsoft.PowerShell.U... Subscribes to the events that are generated by a Microsoft .NET Framework object.
    Select-Object                     Cmdlet    Microsoft.PowerShell.U... Selects objects or object properties.
    Sort-Object                       Cmdlet    Microsoft.PowerShell.U... Sorts objects by property values.
    Tee-Object                        Cmdlet    Microsoft.PowerShell.U... Saves command output in a file or variable and also sends it down the pipeline.
    about_Objects                     HelpFile                            Provides essential information about objects in Windows PowerShell.
    about_Object_Creation             HelpFile                            Explains how to create objects in Windows PowerShell.
```
---
16) This chapter briefly mentioned arrays. What help topic could tell you more about them?
```powershell
get-help *array*
```
`output:`
```
    TOPIC
        about_Arrays

    SHORT DESCRIPTION
        Describes arrays, which are data structures designed to store
        collections of items.
```