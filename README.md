<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1: Create Your Resources via Azure Portal
- Step 2: Install WireShark on the Windows VM using Remote Desktop Connection
- Step 3: Use PowerShell to Execute Various Command- Line Tools and Network Protocols 
- Step 4: Add New Rules to the Linux VM's Network Security Settings
- Step 5: Observe Raw Traffic Being Transmitted or Blocked via WireShark
  

<h2>Actions and Observations</h2>

<p>
<img width="503" alt="image" src="https://github.com/chandy619/azure-network-protocols/assets/144288806/63a5e804-8beb-4d81-b07b-9e513c90566e">
</p>
<p>
Witihin Azure Portal, you'll need to create a new Resource Group that can hold two Virtual Machines (VMs); one for Windows 10 Pro and the other for Linux (Ubuntu). However, both VMs will need to share the same Virtual Network (Vnet).
</p>
<br />

<p>
<img width="395" alt="image" src="https://github.com/chandy619/azure-network-protocols/assets/144288806/cac466f9-05f2-4ffc-a51d-126e7cd56f24">
<img width="365" alt="image" src="https://github.com/chandy619/azure-network-protocols/assets/144288806/ddbeb87f-d8c5-4613-a21c-4f8288e97f22">
</p>
<p>
Connect to the Windows VM by using Remote Desktop.  
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
