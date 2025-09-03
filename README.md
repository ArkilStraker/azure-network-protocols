# Azure-Network-Protocols
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

- Windows 11 Pro (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Install Wireshark and Observe Traffic
- Configuring a Firewall [Network Security Group]
- Step 3
- Step 4

<h2>Actions and Observations</h2>

<p>
<img width="464" height="375" alt="image" src="https://github.com/user-attachments/assets/5447c044-0d8f-408c-b3bb-104dc2b39742" />
<img width="1256" height="611" alt="image" src="https://github.com/user-attachments/assets/00e9749e-ad40-4561-aa25-88af116b3e07" />


</p>
<p>
In this task, we established a Remote Desktop connection to a Windows 11 Virtual Machine and verified network connectivity by successfully pinging a Linux Virtual Machine from within the Windows 11 environment. By installing Wireshark and capturing traffic, you can directly observe how data moves across the network. Wireshark provides deep insight into communication between hosts, helps troubleshoot problems, and teaches how different protocols operate. This makes it a valuable tool for both network administration and security analysis.
</p>
<br />

<p><img width="349" height="780" alt="image" src="https://github.com/user-attachments/assets/57084dd9-b524-46bc-8307-5cc6ae98d465" />
<img width="946" height="389" alt="image" src="https://github.com/user-attachments/assets/7abe1be0-702d-456a-8a0c-85f8286e23c2" />
<img width="1038" height="619" alt="image" src="https://github.com/user-attachments/assets/bec22a52-5145-4e55-af97-230a59fa1455" />
<img width="1209" height="615" alt="image" src="https://github.com/user-attachments/assets/8bbe07bb-e008-4739-8bc3-3e215dc7bea5" />




</p>
<p>
In this task, we initiated a continuous ping from the Windows 11 Virtual Machine to the Linux Virtual Machine and monitored the ICMP traffic using Wireshark. We then configured the Network Security Group (NSG) for the Linux Virtual Machine to deny all ICMP traffic and observed the resulting changes in Wireshark. We then removed the rule for the (NSG) and captured the rsults.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
