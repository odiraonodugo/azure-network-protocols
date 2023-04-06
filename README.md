<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
Welcome back! In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

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

- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic

<h2>Actions and Observations</h2>

1. For this demonstrations we will need to create two virtual machines using Microsoft Azure. One machine will use Ubuntu Linux, and the other will use Windows 10 as its operating system. Both will have should have a minimum of a two-core virtual cpu, personally I went with four-cores. Once both is set-up, go ahead and login to the Windows 10 version. Download and Install [WireShark](https://www.wireshark.org/download.html). 

![](https://github.com/odiraonodugo/image/blob/main/Screenshot%202023-04-06%20170249.png)


Open WireShark and for ICMP Traffic only. This traffic will display the relay request and deliver, also known as "ping". We will be able to see how many packets are requested and recieved. The cool thing is that we can inspect the data of the packets in WireShark. 

![](https://github.com/odiraonodugo/image/blob/main/Screenshot%202023-04-06%20154637.png)

2. Observe SSH Traffic, Back in Wireshark, filter for SSH traffic only
From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)
Type commands (username (labuser@10.0.0.5), pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark.   Exit the SSH connection by typing ‘exit’ and pressing [Enter]


![](https://github.com/odiraonodugo/image/blob/main/Screenshot%202023-04-06%20155237.png)


3. Observe DHCP Traffic, Back in Wireshark, filter for DHCP traffic only, From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew),  Observe the DHCP traffic appearing in WireShark
 

![](https://github.com/odiraonodugo/image/blob/main/Screenshot%202023-04-06%20155640.png)

4. Back in Wireshark, filter for DNS traffic only, From your Windows 10 VM within a command line, use "nslookup" to see what google.com and disney.com’s IP addresses are
  Observe the DNS traffic being show in WireShark
. 

![](https://github.com/odiraonodugo/image/blob/main/Screenshot%202023-04-06%20155726.png)

5. Observe RDP Traffic
Back in Wireshark, filter for RDP traffic only (tcp.port == 3389), Observe the immediate non-stop spam of traffic and because the RDP (protocol) is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted
 

![](https://github.com/odiraonodugo/image/blob/main/git.png)


