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

- Windows Server 2026
- Windows 11 (25H2)

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
<img width="1000" height="450" alt="Screenshot" src="https://github.com/user-attachments/assets/a08c87b2-d2f1-4ba6-b152-7f5b3305eabf" />
</p>
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
<img width="1000" height="450" alt="Screenshot" src="https://github.com/user-attachments/assets/402ce1cc-bc73-41ec-853b-38147279764c" />
</p>
<p>
In the Azure Portal, I searched for “Virtual Networks,” selected the service, and clicked “+ Create.”
</p>
<p>
<img width="1000" height="450" alt="Screenshot" src="https://github.com/user-attachments/assets/c37fd05e-044c-4c47-87aa-eec27b16871f" />
</p>
<p>
During the setup process, I chose the previously created resource group “Active-Directory-Lab” and assigned the name “Active-Directory-VNet” to the virtual network. I then selected my region which is (US) East US 2 (Select for your specific region!). This virtual network provides a secure environment that will allow Our Azure virtual machines to communicate with one another on the same network later on.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
