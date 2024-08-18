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

<h2>Simple list and visualization of the process</h2>

Step 1: Create 2 virtual machines in the Azure portal within one resource group. One virtual machine should be Windows 10 and the other one should be Linux (ubuntu 24.04). Make sure that both virtual machines are on the same network.

![image](https://github.com/user-attachments/assets/8350af70-f914-403e-bee5-7bc6a88554f1)

Step 2: Download WireShark in VM-1 and filter for ICMP traffic. ping VM-2 using Windows Powershell

![image](https://github.com/user-attachments/assets/d95d2270-d706-43c3-9c33-cc96bb7eefa3)

Step 3: Perpetually ping VM-2 by using the ping command, and then typing the private ip-address of VM-2 and, then the -t command into powershell

![image](https://github.com/user-attachments/assets/641cc265-1143-48b1-b7b8-6045216a041d)

Step 4: In the Azure portal, open up the Network Security Group in the Ubuntu VM and create an inbound security rule that disables incoming ICMP traffic. Go back to powershell in VM-1. You should see Request timed out message within Powershell.

![image](https://github.com/user-attachments/assets/0c24583d-32b3-477e-acb7-27c048cb0243)
![image](https://github.com/user-attachments/assets/e8af99a9-6c90-4e58-98aa-3eb87c954d82)
![image](https://github.com/user-attachments/assets/d944a07a-6778-46ee-853d-ec01ee361982)

Step 5: Now filter for SSH traffic. From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address).Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark. Exit the SSH connection by typing ‘exit’ and pressing [Enter]

![image](https://github.com/user-attachments/assets/9f577794-0c0f-4ec3-9ec1-3af61a4e18cb)

Step 6: Now filter for DHCP traffic from your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew). Observe the DHCP traffc appearing in WireShark


Step 7: Now filter for DNS traffic. From your Windows 10 VM within a command line, use nslookup to see google.com IP addresses. Observe the DNS traffic being show in WireShark.

![image](https://github.com/user-attachments/assets/a036bc76-8aa3-4f06-b811-7a663e56adb0)










