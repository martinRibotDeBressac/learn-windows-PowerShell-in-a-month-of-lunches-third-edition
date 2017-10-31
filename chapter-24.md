# Using regular expressions to parse text files

1) Get all files in your Windows directory that have a two-digit number as part of the name.

```powershell
Get-ChildItem -Path C:\Windows | Where-Object {$_.Name -match "\d{2}"}
```

---

2) Find all processes running on your computer that are from Microsoft, and display the process ID, name, and company name. Hint: pipe Get-Process to Get-Member to discover property names.

```powershell
Get-Process | where {$_.Company -match "microsoft"} | Select-Object -Property Id,Name,Company
```

---

3) In the Windows Update log, usually found in C:\Windows, you want to display only the lines where the agent began installing files. You may need to open the file in Notepad to figure out what string you need to select.

```powershell
Get-WindowsUpdateLog

<#

From here https://support.microsoft.com/en-us/help/902093/how-to-read-the-windowsupdate-log-file

2005-06-0212:10:41 99258cAgent** START **  Agent: Installing updates [CallerId = WindowsUpdate]

#>

Get-Content -Path C:\Users\martin.INTERNAL\Desktop\WindowsUpdate.log | Select-string "START[\w+\W+]+Agent: Installing updates"
```

---

4) Using the Get-DNSClientCache cmdlet, display all listings in which the Data property is an IPv4 address.

```powershell
Get-DnsClientCache | Where-Object {$_.data -match "\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}"}
```