


## Базова конфигурация

AD
![image](https://user-images.githubusercontent.com/79700810/135076082-526bacb5-788e-41e1-97b6-478b23334b2e.png)

```powershell
Rename-Computer -NewName AD
```

```powershell
Get-NetAdapter
```

![image](https://user-images.githubusercontent.com/79700810/135076517-7ec62953-499f-4821-8ac5-ffa8ef9d131b.png)

```powershell
New-NetIPAddress -InterfaceIndex 4 -IPAddress 172.30.0.1 -PrefixLength 24 -DefaultGateway 172.30.0.254
```

![image](https://user-images.githubusercontent.com/79700810/135076786-53aec8d7-1fc0-41e7-bb60-5debdc0b2e8c.png)

```powershell
Set-DnsClientServerAddress -InterfaceIndex 4 -ServerAddresses 172.30.0.1
```

![image](https://user-images.githubusercontent.com/79700810/135076895-e684a471-1788-4a92-9588-e7ad179784f4.png)

```powershell
Set-TimeZone -Id "Russian Standard Time"
```

![image](https://user-images.githubusercontent.com/79700810/135077137-a6b43163-7ea7-4fb2-9e33-c555f1d03037.png)


