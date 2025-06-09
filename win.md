- [1. reg](#1-reg)
  - [1.1. query](#11-query)
  - [1.2. add](#12-add)
  - [1.3. delete](#13-delete)
- [2. Reboot/Shutdown](#2-rebootshutdown)
- [3. Invoke-WebRequest](#3-invoke-webrequest)
- [4. Configure IP Address](#4-configure-ip-address)
- [5. Chocolatey](#5-chocolatey)


# 1. reg
## 1.1. query
```sh
reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v AutoAdminLogon
reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v DefaultUserName
reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v DefaultPassword
```

## 1.2. add
```sh
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v AutoAdminLogon /t REG_SZ /d "1" /f
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v DefaultUserName /t REG_SZ /d "administrator" /f
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v DefaultPassword /t REG_SZ /d "Qwe123" /f
```

## 1.3. delete
```sh
reg delete "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v AutoAdminLogon /f
reg delete "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v DefaultUserName /f
reg delete "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v DefaultPassword /f
```

# 2. Reboot/Shutdown
```sh
shutdown -t -f 0 -r
```

```sh
shutdown -t -f 0 -s
```

# 3. Invoke-WebRequest
```sh
iwr http://10.1.1.10/lab.zip -O lab.zip
iwr http://10.1.1.10:8000/lab.zip -O lab.zip
```

# 4. Configure IP Address
```sh
netsh i i sh con Ethernet
netsh i i sh a Ethernet
netsh i i se a Ethernet s 10.1.1.1/24
```

# 5. Chocolatey
```sh   PowerShell
Set-ExecutionPolicy Bypass -Scope Process -Force
[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072
iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

choco install notepadplusplus everything 7zip xplorer2 bginfo psexec
```