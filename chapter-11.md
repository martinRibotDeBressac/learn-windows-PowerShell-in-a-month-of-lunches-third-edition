1. Import the NetAdapter module (available in the latest version of Windows, both client and server). Using the Get-NetAdapter cmdlet, display a list of nonvirtual network adapters (adapters whose Virtual property is False, which PowerShell represents with the special $False constant).

    Import-Module NetAdapter

    Get-NetAdapter | gm

    Get-NetAdapter -Physical

##############################

2. Import the DnsClient module (available in the latest version of Windows, both client and server). Using the Get-DnsClientCache cmdlet, display a list of A and AAAA records from the cache. Hint: if your cache comes up empty, try visiting a few web pages first to force some items into the cache.

    Import-Module DnsClient

    Get-DnsClientCache | gm

    Get-DnsClientCache -Type A,AAAA

##############################

3. Display all EXE files under C:\Windows\System32 that are larger than 5 MB.

    Get-ChildItem C:\Windows\System32 -Filter *.exe | where {$_.length -gt 5MB}

##############################

4. Display a list of hotfixes that are security updates.

    Get-HotFix -Description *Security*

##############################

5. Display a list of hotfixes that were installed by the Administrator, and which are updates. If you don’t have any, try finding hotfixes installed by the System account. Note that some hotfixes won’t have an “installed by” value—that’s OK.

    Get-HotFix | Where-Object {$_.installedby -eq "Administrator" -and $_.Description -eq "Update"}

##############################

6. Display a list of all processes running with either the name Conhost or the name Svchost.

    Get-Process -Name Conhost,Svchost
