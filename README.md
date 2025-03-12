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


<h2>Actions and Observations</h2>
First, we will start out using Microsoft azure to create two virtual machines. One machine will be windows-vm and the other will be a linux-vm. We make sure that both of these virtual machines are on the same virtual network. Using remote desktop, we log into the windows-vm and install wireshark. We will be using wireshark to observe traffic between the two virtual machines. Now that we have wireshark on the windows-vm, we will start a packet capture and filter for ICMP traffic. From the windows-vm, we will ping the linux-vm using powershell and you should be able to observe the traffic from wireshark. 

![image](https://github.com/user-attachments/assets/861390c3-059a-425c-9a9d-fce43e5e7dc3)

In the next portion of the lab we will nonstop ping the Linux machine with the command ping -t. It will keep pinging the linux machine until we want to stop it. Next, we will configure the linux-vm's firewall to block the incoming traffic from the windows-vm. 

![image](https://github.com/user-attachments/assets/a6e3c881-c4ea-4e98-a800-61a0057ca3a5)

Now that we added the inbound security rule for the linux-vm, all the requests from the windows-vm should start timing out. 

![image](https://github.com/user-attachments/assets/a63e0b47-bd2c-4b08-b7ab-2c9ef4807b02)

Next, we will use wireshark to observe SSH traffic only using the windows machine. In order ssh into the linux machine, we use powershell on the windows machine. 

![image](https://github.com/user-attachments/assets/1eaf7b8d-5515-4f2b-b35e-a57baf8bd17d)
![image](https://github.com/user-attachments/assets/85a1d76d-2424-4a5a-87a1-59db9f8b2045)

Now we will use wireshark to filter for DHCP. DHCP is the Dynamic Host Configuration Protocol this works on ports 67/68. It is used to assign IP addresses to machines. We will request a new ip address with the command "ipconfig /renew". Once we enter the command wireshark will capture DHCP traffic.

![image](https://github.com/user-attachments/assets/67117574-087e-4cd4-ae93-c2f5e2b011d2)




