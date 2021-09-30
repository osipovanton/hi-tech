


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

## All Config

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

```powershell
Add-DnsServerResourceRecordA -Name "lorrylogapi" -ZoneName "ht2021.local" -AllowUpdateAny -IPv4Address "172.30.0.3" -CreatePtr 
```
![image](https://user-images.githubusercontent.com/79700810/135402777-83c63a4d-2c80-4fe1-ab59-277ae025e17b.png)

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

 ## GPO 

![image](https://user-images.githubusercontent.com/79700810/135275861-4635c1a3-88dd-4dd5-82a5-d3641570cdcf.png)

![image](https://user-images.githubusercontent.com/79700810/135276156-4f3b6640-d595-4123-a67d-1ccc8920a17c.png)

![image](https://user-images.githubusercontent.com/79700810/135276221-6b3f8074-4ffa-4d80-9a2b-689abbe8d5a1.png)

![image](https://user-images.githubusercontent.com/79700810/135276374-c6686035-50bc-4b3e-873d-30e4489a9a9f.png)



  ## Проверка

![image](https://user-images.githubusercontent.com/79700810/135218683-492495ec-5bcb-426a-8897-0581915428d8.png)

## BD

```powershell
Add-Computer -DomainName "ht2021.local"
```
![image](https://user-images.githubusercontent.com/79700810/135219110-dd760bf4-ba07-4050-9898-df8f9af9a031.png)

```powershell
Restart-Computer
```
```powershell
New-NetFirewallRule -DisplayName "SQLServer default instance" -Direction Inbound -LocalPort 1433 -Protocol TCP -Action Allow
```
![image](https://user-images.githubusercontent.com/79700810/135220934-1c17e457-1931-411c-adce-e261e91349da.png)
```powershell
New-NetFirewallRule -DisplayName "SQLServer Browser service" -Direction Inbound -LocalPort 1434 -Protocol UDP -Action Allow
```
![image](https://user-images.githubusercontent.com/79700810/135221149-d182072d-f02d-4b25-a19d-5a7f57a7a91f.png)


## install MSSQL

![image](https://user-images.githubusercontent.com/79700810/135219676-8d2ca0e5-387d-4543-bfdc-a67505a1d84c.png)

![image](https://user-images.githubusercontent.com/79700810/135230606-251a4d2f-9142-40d9-a6a7-dbc5d5aacf97.png)

![image](https://user-images.githubusercontent.com/79700810/135231100-39d6c692-5a54-4690-afcd-81d165340494.png)

![image](https://user-images.githubusercontent.com/79700810/135231163-beb6ae0f-75c3-43a1-a5f2-54fb3eeff6df.png)

![image](https://user-images.githubusercontent.com/79700810/135231356-6f921110-783e-42f9-bd29-b9ef3271a795.png)

![image](https://user-images.githubusercontent.com/79700810/135232205-060c6a4c-f2c3-41a5-89c2-d92da5e3bb09.png)

![image](https://user-images.githubusercontent.com/79700810/135239938-ef82779f-0e26-412d-b4d8-57b7dfb11d2a.png)

## DEV1
```powershell
Add-Computer -NewName DEV1 -DomainName "ht2021.local"
```
```powershell
Restart-Computer
```
![image](https://user-images.githubusercontent.com/79700810/135234607-309ba498-1de5-40c6-a248-f663bf4b0c7f.png)

![image](https://user-images.githubusercontent.com/79700810/135240076-12049d3d-d476-4e78-9c1d-eaf42960cd3f.png)

```sql
create database lorrylog;

use lorrylog;

Create table [dbo].[Vehicle]([Id] [int] identity(1,1) not null,[Name] [nvarchar](50) not null,[License] [nvarchar](10) not null,[Make] [nvarchar](20) not null,[Model] [nvarchar](20) not null,[Year] [smallint] not null,Primary key CLUSTERED([Id] ASC))

Insert into Vehicle ([Name],[License], Make, Model,Year) Values ('Thunderdom', 'MADMAX','Ford', 'Falcon XB Coupe', 1974)

select * from Vehicle
```
## Проверка 

![image](https://user-images.githubusercontent.com/79700810/135242031-be0c3827-f9b8-44bf-b442-5a093f886208.png)

## DEV2
```
apt-get install vim
apt-get install sssd-ad sssd-tools realmd adcli
```

![image](https://user-images.githubusercontent.com/79700810/135448670-77bf4cad-09c9-47e4-bc29-b1d72658d54d.png)
```
vim /etc/systemd/timesyncd.conf
```
![image](https://user-images.githubusercontent.com/79700810/135449305-3a6cb4fc-6e93-4bcd-bd6f-592c69084355.png)
```
realm discover
```

![image](https://user-images.githubusercontent.com/79700810/135449383-40f7e1f8-b638-4e4f-9501-507992c885d8.png)
```
realm join ht2021.local
realm list
```
![image](https://user-images.githubusercontent.com/79700810/135449633-dcd64aae-b34b-48a2-9796-c5d93f7b9f06.png)
```
pam-auth-update --enable mkhomedir
reboot
```

![image](https://user-images.githubusercontent.com/79700810/135449675-1c4c951d-2e18-4537-ae61-aab39a8d3ff6.png)

## git 

![image](https://user-images.githubusercontent.com/79700810/135442198-80415828-b7bc-44b9-894d-f9e7c125df8f.png)

fork 

![image](https://user-images.githubusercontent.com/79700810/135442254-515d7fbd-653c-4355-b28a-c3c76e40f4a6.png)


### !!!!!!!! git clone
![image](https://user-images.githubusercontent.com/79700810/135442313-a2812500-9360-41ef-a53c-37bf25c3bb0e.png)

![image](https://user-images.githubusercontent.com/79700810/135442609-af82e04e-4af5-4c7a-8335-67cf48973ba0.png)

![image](https://user-images.githubusercontent.com/79700810/135436103-5cb74ffb-029d-46da-ae7c-5c4014dbfb53.png)


## connect url
```
"Server=bd.ht2021.local; Database=LorryLog; Trusted_Connection=True;"
```
![image](https://user-images.githubusercontent.com/79700810/135277610-4c0a60a8-5823-4fa6-80e8-7cf5b504a613.png)
```
http://172.30.0.3:5001;http://lorrylogapi.ht2021.local:5001
```
![image](https://user-images.githubusercontent.com/79700810/135402103-bb745ded-3a11-4e53-acc6-c3633fcc5951.png)


### !!!!!!!! git pull

![image](https://user-images.githubusercontent.com/79700810/135442971-30957656-bc59-487e-be7c-74077f042e6e.png)

![image](https://user-images.githubusercontent.com/79700810/135439193-330350b9-e33a-49b1-ae61-13c6aa6c9de6.png)

![image](https://user-images.githubusercontent.com/79700810/135439334-86d25d36-b72c-4d74-b22d-2db7339f1d0c.png)

![image](https://user-images.githubusercontent.com/79700810/135439403-f2e1a336-e2a6-4e84-a900-34e2d6b016fe.png)

![image](https://user-images.githubusercontent.com/79700810/135439423-74b80a48-844c-45e0-873a-e6beda1324d0.png)

![image](https://user-images.githubusercontent.com/79700810/135439641-ec0128ec-d877-49cd-9d2a-872cf462b2d3.png)

## APP

```powershell
Add-Computer -DomainName "ht2021.local"
```
![image](https://user-images.githubusercontent.com/79700810/135242823-ee8b488a-9acb-40fc-93e3-1870fefe9788.png)


```powershell
Restart-Computer
```
 ## GIT install

![image](https://user-images.githubusercontent.com/79700810/135251518-b528c6f5-6073-464c-a76a-745dff4fab15.png)

## install dotnet sdk




```powershell
Restart-Computer
```
```powershell
New-NetFirewallRule -DisplayName "WebApi default 5000" -Direction Inbound -LocalPort 5000 -Protocol TCP -Action Allow
New-NetFirewallRule -DisplayName "WebApi Browser 5000" -Direction Inbound -LocalPort 5000 -Protocol UDP -Action Allow

New-NetFirewallRule -DisplayName "WebApi default 5001" -Direction Inbound -LocalPort 5001 -Protocol TCP -Action Allow
New-NetFirewallRule -DisplayName "WebApi Browser 5001" -Direction Inbound -LocalPort 5001 -Protocol UDP -Action Allow
```
![image](https://user-images.githubusercontent.com/79700810/135277077-02202be5-a645-4a4e-af1a-f6981d3897b3.png)

![image](https://user-images.githubusercontent.com/79700810/135277044-6ae24bf0-92e6-45f3-b72f-8dfaa6b0037a.png)

![image](https://user-images.githubusercontent.com/79700810/135277119-4309f92b-9c51-4440-a5d4-820d5260c9ef.png)


![image](https://user-images.githubusercontent.com/79700810/135277151-ed91d74b-36ad-4fc8-90e4-8915ee9d2493.png)




### !!!!!!!! git clone

![image](https://user-images.githubusercontent.com/79700810/135443641-5231e289-c6f3-4bf8-ad47-2883c4badefd.png)

![image](https://user-images.githubusercontent.com/79700810/135443831-d574f526-3678-438b-8a33-f53a1f9c686f.png)

## dotnet run

![image](https://user-images.githubusercontent.com/79700810/135443926-8fe76615-6c31-4e85-835b-a8d3d8407964.png)


## Проверка DEV1

![image](https://user-images.githubusercontent.com/79700810/135402954-0514daf7-d9dd-418f-9e41-e1186d1c3a26.png)


## ADCS
```powershell
Install-WindowsFeature -Name AD-Certificate, ADCS-Web-Enrollment -IncludeManagementTools
```

![image](https://user-images.githubusercontent.com/79700810/135455898-04ff07b7-4416-48e4-beab-af2bd0527816.png)

```powershell
Install-AdcsCertificationAuthority -CAType EnterpriseRootCa -CryptoProviderName "ECDSA_P256#Microsoft Software Key Storage Provider" -KeyLength 256 -HashAlgorithmName SHA256 -CACommonName "RootHT" -force
```

![image](https://user-images.githubusercontent.com/79700810/135458156-bdcb4768-dc14-4dea-b575-ae81719e02d5.png)


![image](https://user-images.githubusercontent.com/79700810/135461720-6660d814-5aa9-401c-ba24-c00825918f2e.png)
![image](https://user-images.githubusercontent.com/79700810/135461761-d40bb5e5-fb6f-4299-9946-1e1111eef44b.png)
![image](https://user-images.githubusercontent.com/79700810/135461825-f5a79613-50cc-404d-acff-310a098182e9.png)



![image](https://user-images.githubusercontent.com/79700810/135458420-feb14739-510d-47f1-a45e-497cfeaa5f82.png)
