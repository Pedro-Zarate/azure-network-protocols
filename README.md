# azure-network-protocols
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
  
- Step 1 (Create our Virtual Machines)

- Step 2 (Observe ICMP Traffic)

- Step 3 (Configuring a Firewall [Network Security Group])

- Step 4 (Observe SSH Traffic)

- Step 5 (Observe DHCP Traffic)

- Step 6 Observe DNS Traffic)

- Step 7 (Observe RDP Traffic)


<h2>(Create our Virtual Machines)</h2>

<p>
  <li> Create the resource group </li>
  <img src="https://i.imgur.com/pIjSMay.png" >
  
  
  <h3> Create both VMs</h3>
  
  <p>
  Create a Windows 10 Virtual Machine (VM) -
While creating the VM, select the previously created Resource Group
While creating the VM, allow it to create a new Virtual Network (Vnet) and Subnet
  </p>

 <p>Create a Linux (Ubuntu) VM -
While creating the VM, select the previously created Resource Group and Virtual Network—the Virtual Network MUST BE THE SAME.
Authentication type: Username/Password
Ensure both VMs are in the same Virtual Network / Subnet </p>

  <img src="https://i.imgur.com/muBE49k.png " >



<br />

<h2>(Observe ICMP Traffic) </h2>


<ul>
  <li>Use Remote Desktop to connect to your Windows 10 Virtual Machine </li>
  <li> Within your Windows 10 Virtual Machine, Install Wireshark</li>
  <img src="https://i.imgur.com/ux9SogQ.png "> 
  <li>Open Wireshark and start packet capture</li>
    <img src="https://i.imgur.com/iwyGq4E.png"> 
  <li>Within Wireshark, filter for ICMP traffic only</li>
  <img src="https://i.imgur.com/a0mxUyJ.png">
  <li>Retrieve the private IP address of the Ubuntu VM (linux-vm) and attempt to ping it from within the Windows 10 VM <ul> <li> Observe ping requests and replies within WireShark </li> </ul> </li>
  <img src="https://i.imgur.com/IIGtOXe.png">
</ul>


<!-- 

<ul>
  <li> </li>
   <img src="">
  <li> </li>
   <img src="">
  <li> </li>
   <img src="">
  <li> </li>
   <img src="">
  <li> </li>
   <img src="">
  <li> </li>

</ul>

 --> 

<h2>(Configuring a Firewall [Network Security Group]) </h2>

<ul>
  <li> Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM 
      <ul> 
        <li>Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic </li> <img src="https://i.imgur.com/I0O3t5z.png">
        <li>Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity </li>    <img src="https://i.imgur.com/oPMj6Hd.png">
        <li>Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is (delete the rule) </li> <img src="https://i.imgur.com/fMh3QWs.png">
        <li>Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)</li> <img src="https://i.imgur.com/W1jIhn6.png">
         <li> Stop the ping activity </li> </li> 
      </ul>
 </li>
</ul>

<h2>(Observe SSH Traffic)</h2>

<ul>
  <li> Log back into the windows-vm </li>
  <li>Back in Wireshark, start a packet capture up </li>
   <img src="https://i.imgur.com/VkI2XJj.png">
  <li> Filter for SSH traffic only</li>
   <img src="https://i.imgur.com/zbbMsJj.png">
  <li>From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address) </li>
  <li> Open PowerShell, and type: ssh labuser@<private IP address> <img src="https://i.imgur.com/9jRehp7.png">
 <ul> 
    <li>Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark </li> <img src="https://i.imgur.com/NasU3il.png">
    <li>Exit the SSH connection by typing ‘exit’ and pressing [Enter] </li> 
  </ul> </li>
    
</ul>















































































