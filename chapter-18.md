# Variables: a place to store your stuff

1) Create a background job that queries the Win32_BIOS information from two computers (use localhost twice if you have only one computer to experiment with).
```powershell
start-job -ScriptBlock {Get-CimInstance -ClassName Win32_BIOS -ComputerName winserver,localhost}
```

2) When the job finishes running, receive the results of the job into a variable.
```powershell
$job = Receive-Job -Keep -Id 1
```

3) Display the contents of that variable.
```powershell
$job
```

4) Export the variable’s contents to a CliXML file.
```powershell
$job | Export-Clixml -Path C:\dev\biosfromvar.xml
```