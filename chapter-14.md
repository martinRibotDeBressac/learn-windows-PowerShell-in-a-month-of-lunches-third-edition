1) What class can you use to view the current IP address of a network adapter? Does the class have any methods that you could use to release a DHCP lease? (Hint: network is a good keyword here.)

```powershell
Get-WmiObject -Namespace root\cimv2 -List *network*
```
```powershell
Get-WmiObject win32_networkadapterconfiguration
```

---
2) Create a table that shows a computer name, operating system build number, operating system description (caption), and BIOS serial number. (Hint: you’ve seen this technique, but you need to reverse it to query the OS class first, and then query the BIOS second.)

```powershell
Get-WmiObject -Namespace root\cimv2 cim_operatingsystem | Format-List @{n="ComputerName";e={$_.__SERVER}},BuildNumber,Caption,@{n="BIOSSerialNumber";e={Get-WmiObject win32_bios -ComputerName $_.__SERVER | Select-Object -ExpandProperty serialnumber}} 
```

---
3) Query a list of hotfixes using WMI. (Hint: Microsoft formally refers to these as quick-fix engineering.) Is the list different from that returned by the Get-Hotfix cmdlet?
```powershell
Get-WmiObject -Namespace root\cimv2 -List *quick*
```
```powershell
Get-WmiObject win32_quickfixengineering
```
`output:`
```
Source        Description      HotFixID      InstalledBy          InstalledOn              
------        -----------      --------      -----------          -----------              
WIN10         Update           KB3150513     NT AUTHORITY\SYSTEM  7/03/2017 12:00:00 AM    
WIN10         Update           KB3161102     NT AUTHORITY\SYSTEM                           
WIN10         Security Update  KB3172729     NT AUTHORITY\SYSTEM  7/03/2017 12:00:00 AM    
WIN10         Update           KB3173428     NT AUTHORITY\SYSTEM  7/03/2017 12:00:00 AM    
WIN10         Update           KB3181403     NT AUTHORITY\SYSTEM                           
WIN10         Update           KB4015220     NT AUTHORITY\SYSTEM                           
WIN10         Security Update  KB4025376     NT AUTHORITY\SYSTEM  8/04/2017 12:00:00 AM    
WIN10         Security Update  KB4025344                                                   
WIN10         Security Update  KB4022714     NT AUTHORITY\SYSTEM  7/03/2017 12:00:00 AM
```
`Get-HoxFix outputs the same list of items`

---
4) Display a list of services, including their current statuses, their start modes, and the accounts they use to log on.
```powershell
Get-WmiObject win32_service | Format-List name,status,startmode,startname
```

---
5) Using the CIM cmdlets, list all available classes in the SecurityCenter2 namespace with Product as part of the name.
```powershell
Get-CimClass -Namespace root\securitycenter2 -ClassName *product*
```
`output:`
```
   NameSpace: ROOT/securitycenter2

CimClassName                        CimClassMethods      CimClassProperties                          
------------                        ---------------      ------------------                          
FirewallProduct                     {}                   {displayName, instanceGuid, pathToSignedP...
AntiVirusProduct                    {}                   {displayName, instanceGuid, pathToSignedP...
AntiSpywareProduct                  {}                   {displayName, instanceGuid, pathToSignedP...
```

---
6) Once you discover the name, use the CIM cmdlets to display any antispyware application. You can also check for antivirus products.
```powershell
Get-CimInstance -Namespace root\securitycenter2 -ClassName antispywareproduct
```