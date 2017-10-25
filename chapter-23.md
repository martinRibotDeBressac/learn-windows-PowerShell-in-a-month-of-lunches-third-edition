# Advanced remoting configuration


1) Create a remoting endpoint named TestPoint on your local computer. Configure the endpoint so that the SmbShare module is loaded automatically, but so that only the Get-SmbShare cmdlet is visible from that module. Also ensure that key cmdlets such as Exit-PSSession are available, but no other core PowerShell cmdlets can be used. Don’t worry about specifying special endpoint permissions or designating a “run as” credential. Test your endpoint by connecting to it using Enter-PSSession (specify localhost as the computer name, and TestPoint as the configuration name). When connected, run Get-Command to ensure that only the designated handful of commands can be seen. Note that this lab might be possible only on Windows 8, Windows Server 2012, and later versions of Windows; the SmbShare module didn’t ship with earlier versions of Windows.

```powershell
New-PSSessionConfigurationFile -Path C:\TestPoint.pssc -ModulesToImport SMBShare -SessionType RestrictedRemoteServer

Register-PSSessionConfiguration -Path C:\TestPoint.pssc -Name TestPoint
<# Warning Says:
WARNING: Register-PSSessionConfiguration may need to restart the WinRM service if a configuration usin
g this name has recently been unregistered, certain system data structures may still be cached. In tha
t case, a restart of WinRM may be required.
#>
Restart-Service WinRM

Enter-PSSession -ComputerName localhost -ConfigurationName TestPoint

Get-Command
```