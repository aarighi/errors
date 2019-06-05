## Check if you are running as Administrator
```cmd
net session >nul 2>&1 && echo Admin || echo User
Admin
```
