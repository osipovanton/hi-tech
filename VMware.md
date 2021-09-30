
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

![image](https://user-images.githubusercontent.com/79700810/135414383-b5d1b48c-e824-443a-a498-7fa76ec8b813.png)

![image](https://user-images.githubusercontent.com/79700810/135414539-cc414ffd-62a5-4828-bb27-b842005cd905.png)

![image](https://user-images.githubusercontent.com/79700810/135414591-3fb60e05-bd09-4d39-baee-aa0850dd5932.png)

## join domen
![image](https://user-images.githubusercontent.com/79700810/135414702-873b227e-e2ca-4b7d-8fcf-b91ca597822c.png)

![image](https://user-images.githubusercontent.com/79700810/135414774-9d158875-918c-48e7-a47e-8337ac243c45.png)

![image](https://user-images.githubusercontent.com/79700810/135415042-cd48f4c9-cb0d-4ae7-bc20-6532a7ee8b0c.png)

![image](https://user-images.githubusercontent.com/79700810/135415142-aea9af3f-526c-4056-a70d-e0a14d8ad472.png)

![image](https://user-images.githubusercontent.com/79700810/135416603-83f0247a-5e4d-46aa-9af4-1de417cf4d21.png)
![image](https://user-images.githubusercontent.com/79700810/135416679-df40adf2-090e-4df7-a8a7-c471870b5917.png)

## add identyty 
![image](https://user-images.githubusercontent.com/79700810/135416696-277ff07d-b2c0-4730-aa3a-3a6129630d06.png)

![image](https://user-images.githubusercontent.com/79700810/135416779-513d68ec-e22d-4300-8af4-3c2696ad82a4.png)

![image](https://user-images.githubusercontent.com/79700810/135416873-ee606086-dff7-4f8c-8206-60bf0e18a094.png)


## admin group

![image](https://user-images.githubusercontent.com/79700810/135417144-e1c18168-8163-4639-86b2-541e3f0a3c4d.png)

![image](https://user-images.githubusercontent.com/79700810/135417075-890fb75f-d344-481d-afca-6fcf3e79cf07.png)

![image](https://user-images.githubusercontent.com/79700810/135418208-fa92b8af-7630-4046-9dc0-5e8bb750860f.png)

## host config 

```powershell
Add-DnsServerResourceRecordA -Name "esxi1" -ZoneName "ht2021.local" -AllowUpdateAny -IPv4Address "172.30.0.6" -CreatePtr

Add-DnsServerResourceRecordA -Name "esxi2" -ZoneName "ht2021.local" -AllowUpdateAny -IPv4Address "172.30.0.7" -CreatePtr
```

ESXi1

![image](https://user-images.githubusercontent.com/79700810/135413309-84959e81-8e3e-4c13-87c5-759e8d7e27f6.png)

![image](https://user-images.githubusercontent.com/79700810/135414107-1c936869-0241-49aa-92a2-d34a484e6e48.png)

ESXi2

![image](https://user-images.githubusercontent.com/79700810/135414229-6f95de7c-153e-4053-a1e1-d872b878a2e2.png)

![image](https://user-images.githubusercontent.com/79700810/135414423-8a1ff8fd-413a-47d0-810b-d13a04da93ef.png)


## datacenter

![image](https://user-images.githubusercontent.com/79700810/135418065-f2ed6bb9-b991-4f41-94b5-68ce66819e90.png)

![image](https://user-images.githubusercontent.com/79700810/135418349-564c76b0-86ed-4804-a63d-22687b68f943.png)


## cluster

![image](https://user-images.githubusercontent.com/79700810/135418408-b9fe568f-aca6-4161-8baf-9346e3caba1e.png)

![image](https://user-images.githubusercontent.com/79700810/135418479-ab912d91-6484-4f11-b4f0-5c4c5090a7e5.png)

![image](https://user-images.githubusercontent.com/79700810/135418557-6e576f50-c97d-4296-9a36-abd301c09a82.png)

![image](https://user-images.githubusercontent.com/79700810/135418739-5239bafe-4eac-4a53-9ae6-836423b68696.png)

![image](https://user-images.githubusercontent.com/79700810/135418775-18cd39bd-1aec-4623-a40c-4d120c86c725.png)

## network

![image](https://user-images.githubusercontent.com/79700810/135418985-291690d8-417b-47ee-b865-fe2f522f0580.png)

![image](https://user-images.githubusercontent.com/79700810/135419126-ef91ef9f-eaad-47dd-9da7-876b25bf22b1.png)

## замена
![image](https://user-images.githubusercontent.com/79700810/135419255-3f395c59-b38a-42d3-9b2b-55b1ae537412.png)

## замена

![image](https://user-images.githubusercontent.com/79700810/135419385-5fbedbdb-29f9-4181-90dd-f3b6bf355417.png)


## DS 
esix1
![image](https://user-images.githubusercontent.com/79700810/135424654-b13ce591-277f-4497-b5b7-506383f8ff88.png)
![image](https://user-images.githubusercontent.com/79700810/135425020-48bee611-c3f8-4321-9465-6139ddf2f4e1.png)
![image](https://user-images.githubusercontent.com/79700810/135425245-3673b0f8-9517-4d71-83cc-8ba99079b6c8.png)
![image](https://user-images.githubusercontent.com/79700810/135425308-e9f5cae8-5e18-49b9-93a8-b5053a74e116.png)

esix2
![image](https://user-images.githubusercontent.com/79700810/135425552-335f8a01-67db-4db6-b359-26c636d20cf0.png)
![image](https://user-images.githubusercontent.com/79700810/135425598-ca1e9de5-dd03-4599-ac46-70fa1652e556.png)


## ds cluster

![image](https://user-images.githubusercontent.com/79700810/135425651-8e1dff4a-cc65-4058-b78d-bf1a625cff8d.png)

![image](https://user-images.githubusercontent.com/79700810/135424715-476f138e-9981-4ba2-b2af-34326947fe0f.png)

![image](https://user-images.githubusercontent.com/79700810/135424825-963eaff1-0a83-4e81-b5cf-89e3a8f44e6d.png)


