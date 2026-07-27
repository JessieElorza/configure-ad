<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This Demonstration outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

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

**1. Setup Domain Controller VM in Azure**
---
<h2>Deployment and Configuration Steps</h2>

***CREATE RESOURCE GROUP.***

Created a resource group to centrally organize and manage all Azure resources for the Active Directory lab. I began by signing in to the [Azure](https://portal.azure.com/) portal, searching for “Resource Groups,” and selecting the service. From there, I initiated the creation process, assigned the name “rg-active-directory-lab,” and completed the setup by selecting “Review + Create,” followed by “Create.”

<p>
<img src="https://github.com/user-attachments/assets/ad9a5590-9851-4dee-9ab2-16773b365f71" width="1119" height="709" alt="Screenshot/>
</p>
<p>

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
