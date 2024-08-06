- [reg](#reg)
  - [query](#query)
  - [add](#add)
  - [delete](#delete)
- [Reboot/Shutdown](#rebootshutdown)
- [Invoke-WebRequest](#invoke-webrequest)
- [Configure IP Address](#configure-ip-address)


# reg
## query
```sh
reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v AutoAdminLogon
reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v DefaultUserName
reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v DefaultPassword
```

## add
```sh
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v AutoAdminLogon /t REG_SZ /d "1" /f
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v DefaultUserName /t REG_SZ /d "administrator" /f
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v DefaultPassword /t REG_SZ /d "Qwe123" /f
```

## delete
```sh
reg delete "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v AutoAdminLogon /f
reg delete "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v DefaultUserName /f
reg delete "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v DefaultPassword /f
```

# Reboot/Shutdown
```sh
shutdown -t -f 0 -r
```

```sh
shutdown -t -f 0 -s
```

# Invoke-WebRequest
```sh
iwr http://10.1.1.10/lab.zip -O lab.zip
iwr http://10.1.1.10:8000/lab.zip -O lab.zip
```

# Configure IP Address
```sh
netsh i i sh a "Ethernet"
netsh i i se a "Ethernet" s 10.1.1.1 255.255.255.0
```