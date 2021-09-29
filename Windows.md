


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

## Проверка c AD


![image](https://user-images.githubusercontent.com/79700810/135084339-b734e3aa-8948-48ed-b21d-89450149fc36.png)


## Install AD

```powershell
Install-WindowsFeature -Name AD-Domain-Services -IncludeManagementTools
```

![image](https://user-images.githubusercontent.com/79700810/135089113-45590dc5-2691-435d-b07e-21dcc331a611.png)


```powershell
Install-ADDSForest -DomainName "ht2021.local" -InstallDNS
```
![image](https://user-images.githubusercontent.com/79700810/135086754-285e1bd2-59b4-45a0-adc9-79c4a574b083.png)


## DNS

```powershell
Add-DnsServerPrimaryZone -NetworkId 172.30.0.0/24 -ReplicationScope Domain
```

![image](https://user-images.githubusercontent.com/79700810/135089385-f9b18d69-4c0d-40d9-a100-4a3fc80be898.png)

```powershell
Add-DNSServerResourceRecordPTR -ZoneName 0.30.172.in-addr.arpa -PTRDomainName dc.ht2021.local -Name 1
```
![image](https://user-images.githubusercontent.com/79700810/135096456-2d31bd18-bbc2-4b55-b035-d9a0055ca8a2.png)

## Проверка AD DNS

![image](https://user-images.githubusercontent.com/79700810/135211673-ed82d9e5-0646-4672-be7e-c1f19d1fd47c.png)

## DHCP


```powershell
Install-WindowsFeature -Name DHCP -IncludeManagementTools
```
![image](https://user-images.githubusercontent.com/79700810/135211808-5c33709a-d592-4784-9f60-2bef6c36b92f.png)

Авторизуйте DHCP сервер в Active Directory (укажите DNS имя сервера и IP адрес, который будет использоваться DHCP клиентами):

```powershell
Add-DhcpServerInDC -DnsName ad.ht2021.local -IPAddress 172.30.0.1
```

![image](https://user-images.githubusercontent.com/79700810/135213223-c5d40c20-221a-4a3f-8787-ac3ce268cb41.png)


Чтобы Server Manager перестал показывать уведомление о том, что DHCP роль требует настройки, выполните команду:

```powershell
Set-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\ServerManager\Roles\12 -Name ConfigurationState -Value 2
```

Перезапустите службу DHCPServer:
```powershell
Restart-Service -Name DHCPServer -Force
```
![image](https://user-images.githubusercontent.com/79700810/135213462-a33e9765-4c95-4986-9067-fa81849374b3.png)


```powershell
Add-DhcpServerv4Scope -Name DHCPHT -StartRange 172.30.0.101 -EndRange 172.30.0.110 -SubnetMask 255.255.255.0 -State Active
```
![image](https://user-images.githubusercontent.com/79700810/135213584-b692175b-d318-40c5-afc4-c364b9b4b128.png)

```powershell
Set-DhcpServerv4OptionValue -ScopeId 172.30.0.0 -OptionId 6 -Value "172.30.0.1","8.8.8.8"
```

![image](https://user-images.githubusercontent.com/79700810/135213840-d0ec6b72-1e87-4c87-9df7-4c74fc8d4872.png)

```powershell
Set-DhcpServerv4OptionValue -ScopeId 172.30.0.0 -OptionId 3 -Value "172.30.0.254"
```
![image](https://user-images.githubusercontent.com/79700810/135214157-ee7d8f67-1408-4cef-8d7d-01883f8a61de.png)

```powershell
Set-DhcpServerv4OptionValue -ScopeId 172.30.0.0 -OptionId 15 -Value "ht2021.local"
```

![image](https://user-images.githubusercontent.com/79700810/135214354-7a77a647-5a7e-491e-b427-b2bc0acaf63d.png)

## Проверка DHCP

![image](https://user-images.githubusercontent.com/79700810/135214432-9e49bda1-c6ae-4810-afb0-353557790409.png)


## OU group user

```powershell
New-ADOrganizationalUnit -Name "OUBD" -Path "DC=ht2021, DC=local"
```

![image](https://user-images.githubusercontent.com/79700810/135214867-a588094d-20e4-405b-b0d2-259c5051b994.png)

```powershell
New-ADGroup -Name "BD" -Path "OU=OUBD, DC=ht2021, DC=local" -GroupScope Global -SamAccountName BD
```

![image](https://user-images.githubusercontent.com/79700810/135214997-fd4943f0-da1b-42ae-8830-64e1b7f051b8.png)

```powershell
New-ADUser -Name lorries -Enabled $true -Path 'OU=OUBD,DC=ht2021, DC=local' -AccountPassword (ConvertTo-SecureString -String 'Pa$$w0rd' -AsPlainText -Force) -UserPrincipalName lorries@ht2021.local -PasswordNeverExpires $true 
```
![image](https://user-images.githubusercontent.com/79700810/135218499-7ef57c02-0fc0-46cf-86e2-ca0fc21bb0b9.png)

```powershell
Add-ADGroupMember -Identity BD -Members lorries
```

![image](https://user-images.githubusercontent.com/79700810/135218611-74776adc-b0be-4922-8020-0d28507adf73.png)

## Проверка

![image](https://user-images.githubusercontent.com/79700810/135218683-492495ec-5bcb-426a-8897-0581915428d8.png)


