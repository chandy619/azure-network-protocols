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

- Step 1: Create your resources via Microsoft Azure.
- Step 2: Install WireShark on your Windows VM using Remote Desktop Connection.
- Step 3: Use PowerShell to execute various Command- Line Tools and Network Protocols. 
- Step 4: Edit your Linux VM's Network Security (Firewall) Settings.
- Step 5: Observe raw traffic being transmitted or blocked via WireShark.
  

<h2>Actions and Observations</h2>

<p>
<img width="503" alt="image" src="https://github.com/chandy619/azure-network-protocols/assets/144288806/63a5e804-8beb-4d81-b07b-9e513c90566e">
</p>
<p>
Witihin Azure, you'll need to create a new Resource Group that will house two Virtual Machines (VMs); one for Windows 10 Pro and the other for Linux (Ubuntu). Be sure that both VMs share the same Virtual Network (Vnet).
</p>
<br />

<p>
<img width="395" alt="image" src="https://github.com/chandy619/azure-network-protocols/assets/144288806/cac466f9-05f2-4ffc-a51d-126e7cd56f24">
<img width="365" alt="image" src="https://github.com/chandy619/azure-network-protocols/assets/144288806/ddbeb87f-d8c5-4613-a21c-4f8288e97f22">
</p>
<p>
Connect to the Windows VM by using Remote Desktop. You'll need the VM's public IP address to successfully login. From there, install WireShark (Traffic Analyzer Software) to be able to inspect traffic within your local computer.  
</p>
<br />

<p>
<img width="668" alt="image" src="https://github.com/chandy619/azure-network-protocols/assets/144288806/3eda45d8-5a81-458a-971d-70e146314cb3">
</p>
<p>
Within WireShark, filter the traffic for ICMP (Internet Control Message Protocol). Next, open PowerShell from the windows start menu so you can execute various Command-Line tools. In order to test the connectivity between both VMs, you'll need to obtain the private IP address of the Linux VM in Azure. Using PowerShell, type 'ping' followed by the IP address or a domain name like google.com to test reachability of the target host. For a successful 'ping', you will see 4 data packets sent out; 4 received and 0 losses. Before the next part of this tutorial, execute a continuous ping to you Linux VM. To do this, add '-t' at the end of the 'ping' command. 
</p>
<br />

<p>
<img width="773" alt="image" src="https://github.com/chandy619/azure-network-protocols/assets/144288806/2f950706-b2e3-4bcb-8673-6735d351d414">
</p>
<p>
In Azure, open the Network Security Group settings for your Linux VM so you can create a new rule. Edit the Inbound Security Rules to Deny ICMP traffic. Keep in mind, you can update a rule's priority level if you want it to take precedent over other rules. Can you guess what'll happen next when you return to WireShark and PowerShell?
</p>
<br />

<p>
<img width="724" alt="image" src="https://github.com/chandy619/azure-network-protocols/assets/144288806/1f9ab4f5-3092-466b-b48e-ba558212360e">
</p>
<p>
As you may have guessed, your Windows VM is unable to successfully connect with your Linux VM due to the rule created. The perpetual 'ping' being sent out by the Windows VM begins to return as "request timed out" via Powershell. Simultaneously, WireShark fails to show a reply back after each request made. This is an example of how Firewalls work. To allow the Linux VM to receive ICMP traffic again, simply delete the rule you've just created. 
</p>
<br />

<p>
<img width="724" alt="image" src="https://github.com/chandy619/azure-network-protocols/assets/144288806/1f9ab4f5-3092-466b-b48e-ba558212360e">
</p>
<p>
lkjdfhg.ldjgljfbkf
</p>
<br />
