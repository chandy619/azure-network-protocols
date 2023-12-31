<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups and Inspecting Traffic Between Azure Virtual Machines</h1>
In this lab, we observe various network traffic to and from Azure Virtual Machines (VMs) with Wireshark as well as experiment with Network Security Groups (NSGs). <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- PowerShell
- Various Network Protocols (ICMP, SSH, DHCP, DNS, RDP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1: Create your resources via Microsoft Azure.
- Step 2: Install Wireshark on your Windows VM using Remote Desktop Connection.
- Step 3: Use PowerShell to execute various network commands and protocols. 
- Step 4: Edit your Linux VM's NSG (Firewall) Settings.
- Step 5: Observe raw traffic being transmitted or blocked via WireShark.
  

<h2>Actions and Observations</h2>

<p>
<img width="854" alt="image" src="https://github.com/chandy619/azure-network-protocols/assets/144288806/2d2c2f35-03de-4d85-849a-471b58a1f701">
</p>
<p>
Within Azure, you'll need to create a new Resource Group that will house two VMs; one for Windows 10 Pro and the other for Linux (Ubuntu). Be sure that both VMs share the same Virtual Network (vnet).
</p>
<br />

<p>
<img width="758" alt="image" src="https://github.com/chandy619/azure-network-protocols/assets/144288806/a452652a-1135-4ee6-bd51-1626c338e550">
</p>
<p>
Connect to the Windows VM by using Remote Desktop. You'll need the VM's public IP address, username and password to successfully login. From there, install Wireshark (a Protocol Analyzer Software) to be able to inspect traffic within your local computer.  
</p>
<br />

<p>
<img width="960" alt="image" src="https://github.com/chandy619/azure-network-protocols/assets/144288806/6982f53f-ac9c-4140-8c6a-0ebcba27ebc1">
</p>
<p>
Within Wireshark, click on the 'Ethernet' and click on the blue shark fin in the top left corner. Filter the traffic for ICMP (Internet Control Message Protocol). Next, open PowerShell from the windows start menu so you can execute various network commands and protocols. In order to test the connectivity between both VMs, you'll need to obtain the private IP address of the Linux VM in Azure. Using PowerShell, type 'ping' followed by the IP address or a domain name like google.com to test reachability of the target host. For a successful 'ping', you will see 4 data packets sent out; 4 received and 0 losses. Before the next part of this tutorial, execute a continuous ping to you Linux VM. To do this, add '-t' at the end of the 'ping' command. 
</p>
<br />

<p>
<img width="820" alt="image" src="https://github.com/chandy619/azure-network-protocols/assets/144288806/5efcbafb-1a5b-4b53-a1a6-8d7b94509c2b">
</p>
<p>
In Azure, open the NSG settings for your Linux VM so you can create a new rule. Edit the Inbound Security Rules to Deny ICMP traffic. Keep in mind, you can update a rule's priority level if you want it to take precedent over other rules. Can you guess what'll happen next via Wireshark and PowerShell?
</p>
<br />

<p>
<img width="960" alt="image" src="https://github.com/chandy619/azure-network-protocols/assets/144288806/14865b7e-9beb-4fab-aced-5d6a24aa08ec">
</p>
<p>
As you may have guessed, your Windows VM is unable to successfully 'ping' your Linux VM due to the rule created. The perpetual 'ping' being sent out by the Windows VM begins to return as "request timed out" via Powershell. Simultaneously, Wireshark fails to show a reply back after each request is made. This is an example of how Firewalls work. To allow the Linux VM to receive ICMP traffic again, simply delete the rule you've just created. 
</p>
<br />

<p>
<img width="960" alt="image" src="https://github.com/chandy619/azure-network-protocols/assets/144288806/0ba25a15-ee0f-4e47-b994-c92e7b9d15ee">
</p>
<p>
In the next part of the tutorial, filter the traffic in Wireshark from ICMP to SSH (Secure Shell). SSH is another protocol similar to Remote Desktop without the visual display. To login to the Linux VM, use command 'ssh' following its username@IP address and, when prompted, enter its password. Once you're logged in, you can use Linux commands like 'id', 'uname -a', 'pwd', etc. to examine the SSH traffic being created via Wireshark. To close the SSH connection, type 'exit' into the PowerShell command line.
</p>
<br />

<p>
<img width="960" alt="image" src="https://github.com/chandy619/azure-network-protocols/assets/144288806/3a3e2b91-6f9d-4618-a8c0-efe984334f57">
</p>
<p>
To examine DHCP (Dynamic Host Configuration Protocol) traffic in Wireshark, change the filter from SSH to DHCP. To issue a new IP address to the Windows VM, enter 'ipconfig /renew' into PowerShell. This may cause a temporary disconnection as your device may be assigned a new IP address within the newtork. 
</p>
<br />

<p>
<img width="960" alt="image" src="https://github.com/chandy619/azure-network-protocols/assets/144288806/cade5699-596f-43f2-b03e-700ab9005337">
</p>
<p>
Next up, we will observe DNS (Domain Name System) traffic. Filter for DNS traffic in Wireshark. Instead of typing in DNS into the filter, you can also filter traffic if you know the port associated with the protocol. For instance, DNS uses both TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) with port 53. Enter 'udp.port==53' and it will filter for DNS traffic as well. In PowerShell, use command 'nslookup' following the Domain Name you wish to learn the public IP address for.
</p>
<br />

<p>
<img width="960" alt="image" src="https://github.com/chandy619/azure-network-protocols/assets/144288806/e2ac6df1-232b-469c-aa25-68b29f5a3d44">
</p>
<p>
The last protocol we will observe is RDP (Remote Desktop Protocol). You can filter the traffic in Wireshark by typing in 'RDP' or 'tcp.port==3389'. Remember that we are already using Remote Desktop to interact with the Windows VM, so when you hit enter, you can expect a constant spam of RDP traffic via Wireshark. To close out of your Remote Desktop session, enter 'logoff' into the PowerShell command line.
</p>
<br />
