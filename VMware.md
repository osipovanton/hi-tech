
## Базовая конфигурация

## AD 
```powershell
Add-DnsServerResourceRecordA -Name "esxivcsa1" -ZoneName "ht2021.local" -AllowUpdateAny -IPv4Address "172.30.0.4" -CreatePtr 

Add-DnsServerResourceRecordA -Name "vcsa1" -ZoneName "ht2021.local" -AllowUpdateAny -IPv4Address "172.30.0.5" -CreatePtr
```
![image](https://user-images.githubusercontent.com/79700810/135412898-0ae8a226-cd6a-4fc0-8d8f-fe5f27c9289f.png)

## ESXiVCSA1

![image](https://user-images.githubusercontent.com/79700810/135403164-84049686-a6a1-422b-9b34-adedb037b642.png)

![image](https://user-images.githubusercontent.com/79700810/135403249-bfc792ef-74dd-4851-9969-245f9c145769.png)

![image](https://user-images.githubusercontent.com/79700810/135403300-f2039560-351d-4ff0-81dd-7fb362ec718c.png)

![image](https://user-images.githubusercontent.com/79700810/135403423-606b27c7-eada-4179-a9e4-fd179dfa0d45.png)

![image](https://user-images.githubusercontent.com/79700810/135403468-cd30c045-466c-4223-a4b4-99e1a95e7c11.png)



## install vcsa in DEV1


![image](https://user-images.githubusercontent.com/79700810/135404545-c901b91b-2212-4a1d-b06c-1fa552eed92b.png)

![image](https://user-images.githubusercontent.com/79700810/135404630-71ce1e7f-df5a-4b08-b459-ac3e1671c45c.png)

![image](https://user-images.githubusercontent.com/79700810/135404686-ae80a019-cd10-4523-a058-8708afbfcf1a.png)

![image](https://user-images.githubusercontent.com/79700810/135404742-d5798125-a7b8-4aeb-b0a6-ffbe87006b07.png)

![image](https://user-images.githubusercontent.com/79700810/135404962-025505a2-88df-4377-9e36-15aab143448d.png)


## config vcsa 

![image](https://user-images.githubusercontent.com/79700810/135412166-16ebc16e-a0b2-4944-ae92-0d307ecd7ae4.png)


![image](https://user-images.githubusercontent.com/79700810/135412101-ca8c0ea6-a94f-4a48-865d-c86c4b16153c.png)


![image](https://user-images.githubusercontent.com/79700810/135412335-a0e1a285-dd9d-4a45-8701-fdc6cb6b78ee.png)


