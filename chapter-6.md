# The pipeline: connecting commands

1) Create two similar, but different, text files. Try comparing them by using Diff. Run something like this: Diff -reference (Get-Content File1.txt) -difference (Get-Content File2.txt). If the files have only one line of text that’s different, the command should work.
```powershell
diff -Reference (Get-Content .\File1.txt) -Difference (Get-Content .\File2.txt)
```
```
    InputObject SideIndicator
    
    4           =>
    5           =>
    6           =>
    1           <=
    2           <=
    3           <=
```
---

2) What happens (on Windows) if you run Get-Service | Export-CSV services .csv | Out-File from the console? Why does that happen?
```powershell
Get-Service | Export-CSV services.csv | Out-File
```
```
    Out-File : Cannot process argument because the value of argument "path" is null. Change the value of argument "path" to a non-null value.
    At line:1 char:41
    + Get-Service | Export-CSV services.csv | Out-File
    +                                         ~~~~~~~~
        + CategoryInfo          : InvalidArgument: (:) [Out-File], PSArgumentNullException
        + FullyQualifiedErrorId : ArgumentNull,Microsoft.PowerShell.Commands.OutFileCommand

    no path with out-file and also export-csv also creates the file without needing out-file
```
---

3) Apart from getting one or more services and piping them to Stop-Service, what other means does Stop-Service provide for you to specify the service or services you want to stop? Is it possible to stop a service without using Get-Service at all?
```powershell
Stop-Service -Name **
```
---

4) What if you want to create a pipe-delimited file instead of a comma-separated (CSV) file? You’d still use the Export-CSV command, but what parameters would you specify?
```powershell
Get-Process | Export-Csv process.csv -Delimiter `|
```
or
```powershell
    Get-Process | Export-Csv process.csv -Delimiter "|"
```
---

5) Is there a way to eliminate the # comment line from the top of an exported CSV file? That line typically contains type information, but what if you want to omit that from a particular file?
```powershell
Get-Process | Export-Csv process.csv -NoTypeInformation
```
---

6) Export-CliXML and Export-CSV both modify the system because they can create and overwrite files. What parameter would prevent them from overwriting an existing file? What parameter would ask whether you were sure before proceeding to write the output file?
```powershell
-NoClobber and -Confirm
```
---

7) Windows maintains several regional settings, which include a default list separator. On U.S. systems, that separator is a comma. How can you tell Export-CSV to use the system’s default separator rather than a comma?
```powershell
Get-Service | Export-Csv services.csv -UseCulture
```
