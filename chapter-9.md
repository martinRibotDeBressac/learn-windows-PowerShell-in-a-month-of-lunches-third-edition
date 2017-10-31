# The pipeline, deeper

1) Would the following command work to retrieve a list of installed hotfixes from all computers in the specified domain? Why or why not? Write an explanation, similar to the ones we provided earlier in this chapter.
```powershell
Get-Hotfix -computerName (get-adcomputer -filter * | Select-Object -expand name)
```

With Select-Object using the -Property parameter it will output a ADComputer object type which will not feed into Get-Hotfix,
Using -ExpandProperty will convert the type as String which will be accepted into Get-Hotfix and will work.

So yes this command will work.

---

2) Would this alternative command work to retrieve the list of hotfixes from the same computers? Why or why not? Write an explanation, similar to the ones we provided earlier in this chapter.
```powershell
    get-adcomputer -filter * | Get-HotFix
```
This will only work on the localhost but it will not get any servers from the first command since the object
type is ADComputer by default and that the ComputerName parameter must be named to get the value

---

3) Would this third version of the command work to retrieve the list of hotfixes from the domain computers? Why or why not? Write an explanation, similar to the ones we provided earlier in this chapter.
```powershell
get-adcomputer -filter * | Select-Object @{l='computername';e={$_.name}} | Get-Hotfix
```

This will work since name is being labeled as computername.

---

4) Write a command that uses pipeline parameter binding to retrieve a list of running processes from every computer in an Active Directory (AD) domain. Don’t use parentheses.
```powershell
get-adcomputer -filter * | Select-Object @{l='computername';e={$_.name}} | Get-Process
```
---

5) Write a command that retrieves a list of installed services from every computer in an AD domain. Don’t use pipeline input; instead, use a parenthetical command (a command in parentheses).
```powershell
Get-Service -ComputerName (get-adcomputer -filter *)
```
---

6) Sometimes Microsoft forgets to add a pipeline parameter binding to a cmdlet. For example, would the following command work to retrieve information from every computer in the domain? Write an explanation, similar to the ones we provided earlier in this chapter.
```powershell
get-adcomputer -filter * | Select-Object @{l='computername';e={$_.name}} | Get-WmiObject -class Win32_BIOS
```
This will not work due to Get-WmiObject not accepting pipeline parameter binding to the ComputerName parameter
