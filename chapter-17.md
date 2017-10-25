# Security alert!

1) Use the Set-ExecutionPolicy cmdlet, and we suggest using the RemoteSigned policy setting. You’re welcome to use AllSigned, but it’ll be impractical for the purposes of this book’s remaining labs. You could also choose -Unrestricted.
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```
```powershell
Get-ExecutionPolicy -list
```
`output:`
```
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       Undefined
 LocalMachine    RemoteSigned
```