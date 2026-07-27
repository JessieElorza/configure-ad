<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Virtual Machines Deployed in the Cloud (Azure)</h1>
This Demonstration outlines the Configuration of Azure Virtual Machines in preparation for Active Directory configuration.<br />

<h2>Environments and Technologies Used</h2>

<img src="https://skillicons.dev/icons?i=azure,windows,powershell" />

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2025 (x64 Gen2)
- Windows 11 pro Virtual Machine(25H2)(x64 Gen2)(2 vCPUs)

<h2>High-Level Deployment and Configuration Steps</h2>

- DC-1 = Domain Controller (DNS + AD DS)
- Client-1 = Domain-joined machine
- Both connected via VNet (same subnet)

<h2>Deployment and Configuration Steps</h2>

**1. Navigate to Azure Portal**
---
I began by signing in to the [Azure](https://portal.azure.com/) portal

<p>
<img width="800" height="400" alt="Screenshot" src="https://github.com/user-attachments/assets/40d0e594-0739-4183-a468-f8a8fec29f83" />
</p>

**2. Setup resources for Virtual machines in Azure**
---
***CREATE RESOURCE GROUP.***

Create a resource group to centrally organize and manage all Azure resources for the Active Directory lab. Search for “Resource Groups,” and select the service.
<p>
<img width="850" height="450" alt="Screenshot" src="https://github.com/user-attachments/assets/a08c87b2-d2f1-4ba6-b152-7f5b3305eabf" />
</p>

<h2></h2>

<p>
<img width="400" height="400" alt="Screenshot" src="https://github.com/user-attachments/assets/8168452b-56d4-4f14-9d64-4519e3603ebc" />
</p>
<p>
From there, Click create new resource group, assign the name “Active-Directory-Lab” and complete the setup by selecting “Review + Create,” followed by “Create.”
</p>
<br />

<h2></h2>

***CREATE VIRTUAL NETWORK.***

<p>
<img width="850" height="450" alt="Screenshot" src="https://github.com/user-attachments/assets/402ce1cc-bc73-41ec-853b-38147279764c" />
</p>
<p>
In the Azure Portal, I searched for “Virtual Networks,” selected the service, and clicked “+ Create.”
</p>

<h2></h2>

<p>
<img width="1000" height="450" alt="Screenshot" src="https://github.com/user-attachments/assets/c37fd05e-044c-4c47-87aa-eec27b16871f" />
</p>
<p>
During the setup process, I chose the previously created resource group “Active-Directory-Lab” and assigned the name “Active-Directory-VNet” to the virtual network. I then selected my region which is (US) East US 2 (Select for your specific region!). This virtual network provides a secure environment that will allow Our Azure virtual machines to communicate with one another on the same network later on.
</p>
<p>
<img width="400" height="400" alt="Screenshot" src="https://github.com/user-attachments/assets/004bc8bb-bd21-4b1c-b0db-52ed308785f9" />
</p>
<p>
Validate and click **create** Virtual Network.
</p>

<br />

<h2></h2>

**3. Create both Domain Controller/Client Virtual Machines**
---
***CREATE DOMAIN CONTROLLER VM***

In the Azure portal, I initiated Virtual Machine creation by searching for “Virtual Machine” in the search bar and selecting "+ Create".
<p>
<img width="850" height="450" alt="Screenshot" src="https://github.com/user-attachments/assets/e587a7c9-e466-4c61-8ac6-edeef03aa63a" />
</p>

<h2></h2>

<p>
<img width="1000" height="450" alt="Screenshot" src="https://github.com/user-attachments/assets/a339728c-afc5-45fe-93b0-8097ab3dd9e7" />
</p>
<p>
Choose the **Active-Directory-Lab** resource group, name the VM "dc-1". Set the region to **(US) East US 2** and Select **Availability Zone 1**.
</p>

<h2></h2>

<p>
<img width="1000" height="450" alt="Screenshot" src="https://github.com/user-attachments/assets/e3b940ad-c753-42aa-9d22-5d7338c45df4" />
</p>
<p>
Set the image to **Windows Server 2025 Datacenter: Azure Edition (x64 Gen2)**, and use the **Standard D2s_v3 (2 vCPUs, 8 GiB memory)** size.
</p>

<h2></h2>

<p>
<img width="1000" height="450" alt="Screenshot" src="https://github.com/user-attachments/assets/e3b940ad-c753-42aa-9d22-5d7338c45df4" />
</p>
<p>
configure the username and password under the Admin Account section in dc-1's virtual machine creation tabs. In my instance I used-
<p>
  -Username: labuser
</p>
<p>
  -Password: Cyberlab123!
</p>

<h2></h2>

<p>
<img width="400" height="300" alt="Screenshot" src="https://github.com/user-attachments/assets/446f8190-98e3-4b23-b0c7-e50ae3fd82d2" />
</p>
<p>
Ensure the licensing boxes and agreement boxes are checked and enabled at the bottom of the basics page. Click next and navigate to the **Networking** tab for the virtual network
</p>

<h2></h2>

<p>
<img width="1000" height="450" alt="Screenshot" src="https://github.com/user-attachments/assets/c0bd08cc-9dd8-464d-8653-1cec7c009d86" />
</p>
<p>
In the **Networking** tab I selected the previously created VNet "Active-Directory-VNet", assigned a public IP address, and selected 'default' for Subnet. Once the networking settings were configured, select "Review + Create".
</p>

<h2></h2>

<p>
<img width="400" height="400" alt="Screenshot"src="https://github.com/user-attachments/assets/684bd6d0-3bbe-48d9-a585-8af5d780be73" />  <img width="500" height="400" alt="Screenshot" src="https://github.com/user-attachments/assets/63d6f53e-3080-4fe6-b754-7f712288f9f0" />


</p>
<p>
then "Create" and Deploy the Domain Controller(dc-1) Virtual Machine.
</p>
<br />

<h2></h2>

***CREATE CLIENT-1 VM***

In the Azure portal, search for “Virtual Machine” in the search bar and select + Create the same way we did for the first virtual machine
<p>
<img width="1000" height="450" alt="Screenshot" src="https://github.com/user-attachments/assets/bdb1933d-d24c-462d-87bd-1646f6557135" />
</p>
<p>
Choose the Active-Directory-Lab resource group, named the VM client-1. 

In the Networking tab, I selected the previously created virtual network (rg-active-directory-lab) and kept the subnet as default. After completing the configuration, I clicked Review + Create, then selected Create to deploy the virtual machine.
</p>

<h2></h2>

<p>
<img width="1000" height="450" alt="Screenshot" src="https://github.com/user-attachments/assets/33c3a051-de10-431f-9611-7ca290f19c89" />
</p>
<p>
I set the region to (US) East US 2 with Availability Zone 1, selected the Windows 11 Pro, version 25H2 - x64 Gen2 image with x64 architecture, and used the Standard D2s_v3 (2 vCPUs, 8 GiB RAM) size.
</p>

<h2></h2>

<p>
<img width="1000" height="450" alt="Screenshot" src="https://github.com/user-attachments/assets/83786581-6c3b-401d-a12d-c0ebb4cf5ab1" />
</p>
<p>
Configured the administrator username and password under the Admin Account section.
</p>
<p>
  -Username: labuser
</p>
<p>
  -Password: Cyberlab123!
</p>
<p>
And of course, don't forget to click and mark yes to the licensing check box.
</p>
<br />

<h2></h2>

<p>
<img width="698" height="583" alt="Screenshot 2026-07-24 072121" src="https://github.com/user-attachments/assets/858078aa-9b2d-44e6-975a-2ed483d951de" />
</p>
<p>

</p>
<p>
Configured the administrator username and password under the Admin Account section.
<p>
</p>
<p>

<p>
