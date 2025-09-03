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
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic

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
In this task, we initiated a continuous ping from the Windows 11 Virtual Machine to the Linux Virtual Machine and monitored the ICMP traffic using Wireshark. We then configured the Network Security Group (NSG) for the Linux Virtual Machine to deny all ICMP traffic and observed the resulting changes in Wireshark. We then removed the rule from the Linux Virtual Machine NSG and captured the rsults.
</p>
<br />

<p>
<img width="1120" height="739" alt="image" src="https://github.com/user-attachments/assets/fde57f7a-217b-477b-b5bb-79a7dc4509e4" />

</p>
<p>
In this task, we established an SSH connection from the Windows 11 Virtual Machine to the Linux Virtual Machine and monitored the communication using Wireshark. By applying a filter for SSH traffic, we were able to observe the encrypted session packets in real time. By using Wireshark to observe SSH traffic, you can confirm that encrypted sessions are being established between client and server. Although you can’t see the commands due to encryption, you can analyze session handshakes, packet flow, and connectivity. This validates both the security of SSH and the ability to monitor its presence on the network.
</p>
<br />

<p>
<img width="1234" height="489" alt="image" src="https://github.com/user-attachments/assets/d5adec09-8962-40f2-8849-bc9a3995f382" />

</p>
<p>
In this task, we used PowerShell on a Windows 11 Virtual Machine to release and renew the IP address with the following commands:

- ipconfig /release
- ipconfig /renew

While performing this operation, we captured the traffic in Wireshark to analyze the DHCP transaction. The capture showed the standard DORA process:


- Discover – the client broadcasts a request for an IP address.
- Offer – the DHCP server responds with an available IP.
- Request – the client requests to use the offered IP.
- Acknowledge – the server confirms and assigns the IP lease.

By observing these packets in Wireshark, we verified that the client successfully obtained a new IP address from the DHCP server and confirmed proper communication between client and server.
</p>
<br />

<p>
<img width="1009" height="618" alt="image" src="https://github.com/user-attachments/assets/a89adf35-3953-498b-9271-fd2b48e42cbd" />
</p>
<p>
  Wireshark captured and displayed the following activity:

- DNS Query (Standard Query Request) – the Windows client sent a request packet to the configured DNS server asking for the IP address of www.netflix.com.
- DNS Response (Standard Query Response) – the DNS server replied with the resolved IP address.

By applying the dns display filter in Wireshark, we were able to isolate and analyze only DNS-related packets. We observed:

- The source IP of the Windows 11 VM and the destination IP of the DNS server.
- The protocol (UDP over port 53) used for the query.
- The transaction ID that links the request and response.
- The response section showing the resolved IP address for the domain.
  
This lab confirmed how DNS queries and responses flow over the network and demonstrated how Wireshark can be used to validate and troubleshoot name resolution.
</p>
<br />

<p>
<img width="947" height="618" alt="image" src="https://github.com/user-attachments/assets/a6ddd82d-12ad-4455-8d9b-16b808b7b1ac" />

</p>
<p>
In this task, we used Wireshark to analyze Remote Desktop Protocol (RDP) traffic between a Windows 11 Virtual Machine and another system. By applying the filter:

- tcp.port == 3389

We immediately observed a constant, non-stop stream of packets. This behavior is expected because RDP is an interactive protocol that continuously transmits data to keep the remote session active.
This lab highlighted the difference between on-demand protocols and continuous streaming protocols. RDP falls into the latter, which explains why filtering for TCP port 3389 shows what appears to be “spam” traffic; it is in fact the ongoing live session between the client and server.
</p>
<br />
