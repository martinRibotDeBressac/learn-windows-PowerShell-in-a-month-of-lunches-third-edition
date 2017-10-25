# Input and output

1) Use Write-Output to display the result of 100 multiplied by 10.
```powershell
Write-Output (100 * 10)
```
---
2) Use Write-Host to display the result of 100 multiplied by 10.
```powershell
Write-Host (100 * 10)
```
---
3) Prompt the user to enter a name, and then display that name in yellow text.
```powershell
Read-Host "Enter Name" | Write-Host -ForegroundColor Yellow
```
---
4) Prompt the user to enter a name, and then display that name only if it’s longer than five characters. Do this all with a single PowerShell expression—don’t use a variable.
```powershell
Read-Host "Enter Name" | Where-Object {$_.Length -gt 5}
```