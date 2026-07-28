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
- DNS

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
<img width="400" height="400" alt="Screenshot" src="https://github.com/user-attachments/assets/bdb1933d-d24c-462d-87bd-1646f6557135" />
</p>
<p>
Choose the Active-Directory-Lab resource group, name the Virtual Machine client-1.
</p>

<h2></h2>

<p>
<img width="400" height="400" alt="Screenshot" src="https://github.com/user-attachments/assets/33c3a051-de10-431f-9611-7ca290f19c89" />
</p>
<p>
I set the region to (US) East US 2 with Availability Zone 1, selected the Windows 11 Pro, version 25H2 - x64 Gen2 image with x64 architecture, and used the Standard D2s_v3 (2 vCPUs, 8 GiB RAM) size.
</p>

<h2></h2>

<p>
<img width="400" height="400" alt="Screenshot" src="https://github.com/user-attachments/assets/83786581-6c3b-401d-a12d-c0ebb4cf5ab1" />
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
<img width="400" height="400" alt="Screenshot" src="https://github.com/user-attachments/assets/858078aa-9b2d-44e6-975a-2ed483d951de" />
</p>
<p>
In the Networking tab, select the previously created virtual network (Active-Directory-VNet) and keep the subnet as default and keep everything else as is. After completing the configuration, click, Review + Create, then, select ***Create*** to deploy the Virtual Machine just like the first VM.
</p>

<h2></h2>

<p>
<img width="1000" height="450" alt="Screenshot" src="https://github.com/user-attachments/assets/c98719b7-00fd-488d-80ea-31fac652f99b" />
</p>
<p>
Both Virtual Machines are now Created and deployed! After creating the dc-1/client-1 virtual machines, access them by searching “Virtual Machines” in the Azure Portal and navigating to **Virtual Machines > dc-1** or client-1**.
</p>

<h2></h2>

***Domain Controller VM IP Configuration***

<p>
<img width="1000" height="450" alt="Screenshot" src="https://github.com/user-attachments/assets/0db8fd96-3cd4-42c1-98f4-f5fa4dcc81dd" />
</p>
<p>
<img width="500" height="400" alt="Screenshot" src="https://github.com/user-attachments/assets/2361b7eb-04d8-4eec-83f5-1d9b0574a5ba" />
</p>
<p>
From the left-hand menu, select **Networking > Network Settings**, then click on the VM’s **Network Interface** listed under **Essentials**.
</p>

<h2></h2>

<p>
<img width="1000" height="450" alt="Screenshot" src="https://github.com/user-attachments/assets/4fee9f07-6caf-419c-ae86-523b91e07bff" />
</p>
<p>
Within the network interface settings, navigate to Settings > IP Configurations > ipconfig1, change the Private IP allocation from dynamic to Static, and save the configuration.

Configuring the Domain Controller with a static private IP ensures consistent and reliable network communication. This is critical because client machines depend on the Domain Controller for DNS resolution and authentication services, which require a fixed IP address to function properly.
</p>

<h2></h2>

***DISABLE FIREWALL ON DC-1 VM (Temporary for Testing)***

<p>
<img width="1000" height="450" alt="Screenshot" src="https://github.com/user-attachments/assets/0b32630e-a8e7-453f-8336-a83fad01717e" />
</p>
<p>
Return to the DC-1 VM overview page to locate and copy the Domain Controller’s public IP address.
</p>

<h2></h2>

<p>
<img width="500" height="600" alt="Screenshot" src="https://github.com/user-attachments/assets/b2319ff1-b926-4cbd-b75b-dac0954f8964" />
</p>
<p>
<img width="300" height="250" alt="Screenshot" src="https://github.com/user-attachments/assets/80b306b4-8c81-4465-ac74-fb4d13b0265f" />
</p>
<p>
<img width="300" height="300" alt="Screenshot" src="https://github.com/user-attachments/assets/beec6271-1c3f-476e-8831-04adf63d25bd" />
<p>
On my local computer, I used Remote Desktop to connect to DC-1 VM using its public IP address (20.94.42.226) and entered the username and password that were created when creating the Virtual Machine. Next, I selected **Yes** to proceed, which initiated the Domain Controller’s boot process.
</p>

<h2></h2>

<p>
<img width="150" height="450" alt="Screenshot" src="https://github.com/user-attachments/assets/611a2fad-3817-4b17-af87-df2fb167cd85" />
</p>
<p>
<img width="300" height="250" alt="Screenshot" src="https://github.com/user-attachments/assets/1b0f7b5d-ac33-4f49-8e96-2d4d73dad8f7" />
</p>
<p>
Once the system was fully up and running, I opened **Windows Defender Firewall with Advanced Security** by right clicking the windows logo and selecting **Run** and typing **wf.msc**.
</p>

<h2></h2>

<p>
<img width="1000" height="450" alt="Screenshot" src="https://github.com/user-attachments/assets/93e211ed-9259-433f-a070-e7accdeb9961" />
</p>
<p>
After gaining access to **Windows Defender Firewall with Advanced Security on Local Computer**. Select **Windows Defender Firewall Properties**.
</p>

<h2></h2>

<p>
<img width="400" height="450" alt="Screenshot" src="https://github.com/user-attachments/assets/8b10f98b-571b-4f3f-94b6-68dcf9a07b87" />
</p>
<p>
From there, disable the firewall by setting the Firewall State to **Off** for the Domain, Public, and Private profiles, then click **Apply** to save the changes. dc-1 has been successfully deployed, connected to the correct Virtual Network and subnet, and is now ready for further Active Directory configuration and role installation.

**Reason:**

The firewall is temporarily disabled to allow connectivity testing between virtual machines, permitting `ICMP` ping traffic. 
</p>

> [!NOTE]
> In a production environment, firewall rules would be properly configured rather than disabled.

<h2></h2>

***client-1 Virtual Machine Configuration***

<p>
<img width="950" height="500" alt="Screenshot" src="https://github.com/user-attachments/assets/40810a94-3162-44fd-b4ea-2ae2857bf43a" />
</p>
<p>
Navigate back to the **Virtual Machines** list, select the **dc-1** VM, and open **Network Settings** from the left-hand panel. From there, locate and copy the private IP address (10.0.0.4) 
</p>

<h2></h2>

<p>
<img width="550" height="400" alt="Screenshot" src="https://github.com/user-attachments/assets/ae6af5a8-ee69-4419-9a76-a6aad2eb2251" />
</p>
<p>
Return to the Virtual Machines list and select **client-1**. Navigate to **Network > Network Settings**, then select the **Network Interface/IP configuration**
</p>

<h2></h2>

<p>
<img width="900" height="500" alt="Screenshot" src="https://github.com/user-attachments/assets/cd0fede1-93e2-4d09-b2f8-de5fdd182398" />
</p>
<p>
In the network interface settings, open **DNS servers**, switch the option to **Custom**, and enter the **dc-1 private IP address**. Click **Save** to apply the configuration.
</p>

<h2></h2>

<p>
<img width="900" height="500" alt="Screenshot" src="https://github.com/user-attachments/assets/cd0fede1-93e2-4d09-b2f8-de5fdd182398" />
</p>
<p>
In the network interface settings, open **DNS servers**, switch the option to **Custom**, and enter the **dc-1 private IP address**. Click **Save** to apply the configuration.
</p>

<h2></h2>

<p>
<img width="900" height="500" alt="Screenshot" src="https://github.com/user-attachments/assets/1728250a-927f-4466-95cd-b0cfdd2d6337" />
</p>
<p>
To apply the updated DNS settings, restart client-1 directly from the Azure Portal. After the reboot, the machine will successfully configure to use dc-1 for DNS resolution and is ready for domain connectivity.
</p>

<h2></h2>

***Validate Connectivity and Configuration***

<p>
<img width="900" height="500" alt="Screenshot" src="https://github.com/user-attachments/assets/b7158c25-2687-4ec3-a2ea-d16eac6b60e5" />
</p>
<p>
To validate connectivity to **dc-1**, I used **Remote Desktop** on my local computer to connect to the **client-1** VM using its public IP address (172.200.210.160) using the username and password created during deployment.
</p>

<h2></h2>

<p>
<img width="900" height="500" alt="Screenshot" src="https://github.com/user-attachments/assets/002842ec-9fc9-4dc0-aa20-b5cebeecb1ef" />
</p>
<p>
<img width="900" height="500" alt="Screenshot" src="https://github.com/user-attachments/assets/a8638097-1d5c-425b-b0e4-438671b6e942" />
</p>
<p>
After successfully logging in, open **PowerShell** and run `ping` to the Domain Controller’s private IP address (**10.0.0.4**) to confirm network connectivity. Finally, I executed `ipconfig /all` to verify that the **DNS server** is set to the private IP address of **dC-1**.

**Successful replies confirm:**
  * Network connectivity is functioning properly
  * The firewall is not blocking ICMP traffic
  * Both **DC-1** and **Client-1** VMs are on the same Virtual Network and subnet
</p>

<h2></h2>

<p>
<img width="900" height="500" alt="Screenshot" src="https://github.com/user-attachments/assets/4459b01e-55b5-4ea2-884c-ffc84c049d96" />
</p>
<p>
Finally, I executed `ipconfig /all` to verify that the **DNS server** is set to the private IP address of **dc-1**.

**Successful replies confirm:**
  * Network connectivity is functioning properly
  * The firewall is not blocking ICMP traffic
  * Both **dc-1** and **client-1** VMs are on the same Virtual Network and subnet
</p>
<h2></h2>
