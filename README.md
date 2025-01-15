<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

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

- Step 1: Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM
- Step 2: Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic
- Step 3: Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity
- Step 4: Re-enable ICMP traffic for the Network Security Group your Ubuntu VM , back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working). 

<h2>Actions and Observations</h2>

<p>
<img src="https://github.com/user-attachments/assets/1e2f8f56-ec7a-4b69-80e2-f63e83892ece" height="80%" width="80%" />
</p>
<p>
  During a comprehensive network analysis, I utilized Wireshark on a Windows VM to capture and examine ICMP traffic between two virtual machines, applying an ICMP protocol filter to focus on precise network communication details. By executing an infinite ping command to the Linux VM's private IP address, I generated continuous network traffic for detailed inspection of protocol interactions. The packet capture revealed critical OSI model layer details, including the Ethernet II frame at the Data Link Layer, Internet Protocol handling logical addressing at the Network Layer, and ICMP packets facilitating communication between virtual machines. This methodical approach allowed for in-depth visualization of network packet traversal, demonstrating how different protocol layers interact during basic network communication. The analysis not only verified inter-VM connectivity but also provided insights into network diagnostic techniques using industry-standard tools like Wireshark. 
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/3183a3b4-84fc-4e9f-bdec-e0426deb94fe" height="80%" width="80%" />
</p>
<p>
 As part of our network security project, I set up a firewall rule in Microsoft Azure to control traffic between our virtual machines. I accessed the Linux VM's settings in Azure and went to its Network Security Group, where I added a new inbound security rule. This rule was designed to block incoming ping requests from our Windows VM. I carefully set the rule's priority to ensure it would be applied before other rules, effectively stopping the pings we observed earlier. This process demonstrates how we can use cloud platform tools to manage network traffic and improve security between virtual machines.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/a072971d-7629-48d0-8fdb-551f90367255" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After implementing the firewall rule to block incoming ICMP traffic on the Linux VM, I verified its effectiveness by observing the network behavior from the Windows VM. Using both PowerShell and Wireshark on the Windows VM, I noticed that ping requests were sent but no replies were received, confirming that the rule successfully blocked incoming pings. PowerShell displayed timeout messages, indicating no response from the Linux VM, while Wireshark showed outgoing requests without corresponding replies. We prefer PowerShell for this task due to its advanced features and automation capabilities, making it more suitable for complex system administration tasks compared to the simpler Command Prompt. When using the ping command in a virtual environment, it's best practice to use the private IP address of the target VM, as this ensures proper routing within the internal network and maintains security by not exposing public IP addresses unnecessarily. 
</p>
<br />
