


## Базова конфигурация

## AD

Powershell

![image](https://user-images.githubusercontent.com/79700810/135076082-526bacb5-788e-41e1-97b6-478b23334b2e.png)


```powershell
Rename-Computer -NewName AD
```

![image](https://user-images.githubusercontent.com/79700810/135077764-128c6a5b-8b49-4233-ab01-28a4adff3ca7.png)


```powershell
Get-NetAdapter
```

![image](https://user-images.githubusercontent.com/79700810/135076517-7ec62953-499f-4821-8ac5-ffa8ef9d131b.png)

```powershell
New-NetIPAddress -InterfaceIndex 4 -IPAddress 172.30.0.1 -PrefixLength 24 -DefaultGateway 172.30.0.254
```

![image](https://user-images.githubusercontent.com/79700810/135076786-53aec8d7-1fc0-41e7-bb60-5debdc0b2e8c.png)

```powershell
Set-DnsClientServerAddress -InterfaceIndex 4 -ServerAddresses ("172.30.0.1","8.8.8.8")
```

![image](https://user-images.githubusercontent.com/79700810/135077615-686de7e6-d3d2-4b27-9e3d-59abc1705324.png)

```powershell
Set-TimeZone -Id "Russian Standard Time"
```

![image](https://user-images.githubusercontent.com/79700810/135077137-a6b43163-7ea7-4fb2-9e33-c555f1d03037.png)


```powershell
Set-NetFirewallRule -DisplayGroup "File And Printer Sharing" -Enabled True -Profile Any
```
![image](https://user-images.githubusercontent.com/79700810/135084032-127b3938-8887-43af-b922-407d02f7f7e0.png)


```powershell
Restart-Computer
```

## BD

```powershell
Rename-Computer -NewName BD
```
![image](https://user-images.githubusercontent.com/79700810/135078689-e391018d-d787-46c0-b9a0-099bd68d2488.png)

```powershell
$GetIndex = Get-NetAdapter 
New-NetIPAddress -InterfaceIndex $GetIndex.ifIndex -IPAddress 172.30.0.2 -PrefixLength 24 -DefaultGateway 172.30.0.254
```

![image](https://user-images.githubusercontent.com/79700810/135078577-974c7ced-0520-4c8b-abf4-086b6e8099a4.png)

```powershell
Set-DnsClientServerAddress -InterfaceIndex $GetIndex.ifIndex -ServerAddresses ("172.30.0.1","8.8.8.8")
```

![image](https://user-images.githubusercontent.com/79700810/135078826-7608a631-22a0-4d47-b7d4-d3aa392dcb35.png)


```powershell
Set-TimeZone -Id "Russian Standard Time"
```

![image](https://user-images.githubusercontent.com/79700810/135079028-814169e5-4aa6-49a4-9004-0ed185bce153.png)

```powershell
Set-NetFirewallRule -DisplayGroup "File And Printer Sharing" -Enabled True -Profile Any
```

![image](https://user-images.githubusercontent.com/79700810/135084143-03aec0f0-07a3-4919-b70f-d9c7d3bf1400.png)


```powershell
Restart-Computer
```
## APP

![image](https://user-images.githubusercontent.com/79700810/135079269-d193157f-3d1c-4bdf-b12e-c9a29c51ad52.png)

```powershell
Rename-Computer -NewName APP
$GetIndex = Get-NetAdapter 
New-NetIPAddress -InterfaceIndex $GetIndex.ifIndex -IPAddress 172.30.0.3 -PrefixLength 24 -DefaultGateway 172.30.0.254
Set-DnsClientServerAddress -InterfaceIndex $GetIndex.ifIndex -ServerAddresses ("172.30.0.1","8.8.8.8")
Set-TimeZone -Id "Russian Standard Time"
Set-NetFirewallRule -DisplayGroup "File And Printer Sharing" -Enabled True -Profile Any
Restart-Computer
```

## Config

AD

```powershell
Rename-Computer -NewName AD
$GetIndex = Get-NetAdapter 
New-NetIPAddress -InterfaceIndex $GetIndex.ifIndex -IPAddress 172.30.0.1 -PrefixLength 24 -DefaultGateway 172.30.0.254
Set-DnsClientServerAddress -InterfaceIndex $GetIndex.ifIndex -ServerAddresses ("172.30.0.1","8.8.8.8")
Set-TimeZone -Id "Russian Standard Time"
Set-NetFirewallRule -DisplayGroup "File And Printer Sharing" -Enabled True -Profile Any
Restart-Computer
```
BD

```powershell
Rename-Computer -NewName BD
$GetIndex = Get-NetAdapter 
New-NetIPAddress -InterfaceIndex $GetIndex.ifIndex -IPAddress 172.30.0.2 -PrefixLength 24 -DefaultGateway 172.30.0.254
Set-DnsClientServerAddress -InterfaceIndex $GetIndex.ifIndex -ServerAddresses ("172.30.0.1","8.8.8.8")
Set-TimeZone -Id "Russian Standard Time"
Set-NetFirewallRule -DisplayGroup "File And Printer Sharing" -Enabled True -Profile Any
Restart-Computer
```
APP

```powershell
Rename-Computer -NewName APP
$GetIndex = Get-NetAdapter 
New-NetIPAddress -InterfaceIndex $GetIndex.ifIndex -IPAddress 172.30.0.3 -PrefixLength 24 -DefaultGateway 172.30.0.254
Set-DnsClientServerAddress -InterfaceIndex $GetIndex.ifIndex -ServerAddresses ("172.30.0.1","8.8.8.8")
Set-TimeZone -Id "Russian Standard Time"
Set-NetFirewallRule -DisplayGroup "File And Printer Sharing" -Enabled True -Profile Any
Restart-Computer
```

## Проверка AD


![image](https://user-images.githubusercontent.com/79700810/135084339-b734e3aa-8948-48ed-b21d-89450149fc36.png)


