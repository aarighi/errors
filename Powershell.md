## Check if you are running as Administrator
```Powershell
PS> [bool](([System.Security.Principal.WindowsIdentity]::GetCurrent()).groups -match "S-1-5-32-544")

True
```
