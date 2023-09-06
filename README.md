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

- Create a resource group with two virtual machines in Microsoft Azure one should have Windows 10 and the other should run Ububtu.
- Connect to the Windows virtual machine and use it to install wireshark
- Use wireshark to observe ICMP traffic.
- Use wireshark to observe SSH traffic.
- Use wireshark to observe DHCP traffic.
- Use wireshark to observe DNS traffic
- Use wireshark to observe RDP traffic.

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/ck0r2pL.png"/>
</p>
<p>
Use Microsoft Azure to create two virtual machines. When creating the Ubuntu virtual machine set it to use a password as shown in the above screenshot.
</p>
<br />

<p>
<img src="https://i.imgur.com/VePiSNS.png"/>
</p>
There should be two virtual machines created as shown in the above screenshot. Conncect to the virtual machine running windows.
<p>
<br />
  
<p>
<img src="https://i.imgur.com/VePiSNS.png"/>
</p>
There should be two virtual machines created as shown in the above screenshot. Conncect to the virtual machine running windows.
<p>
<br />

<p>
<img src="https://i.imgur.com/poZlZkX.png"/>
</p>
<p>
Go to https://www.wireshark.org/download.html and install wireshark onto the windows virtual machine that was made in Azure.
</p>
<br />

<p>
<img src="https://i.imgur.com/AwMDD9g.png"/>
</p>
<p>
Once wireshark is installed click on ethernet to begin capturing the local traffic.
</p>
<br />

<p>
<img src="https://i.imgur.com/HwvIED8.png"/>
</p>
<p>
Type in icmp into the bar of wireshark to isolate traffic from the internet control message protocol (ICMP).
</p>
<br />

<p>
<img src="https://i.imgur.com/CMYlcUO.png"/>
</p>
<p>
Use the Azure portal to note the private IP of the Ubuntu virtual machine.
</p>
<br />

<p>
<img src="https://i.imgur.com/WVf7cK2.png"/>
</p>
<p>
Use command line to ping the Ubuntu virtual machine and note the traffic that appears in wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/JlUh17s.png"/>
</p>
<p>
Use ping -t to contiounously ping the ubuntu virtual machine.
</p>
<br />

<p>
<img src="https://i.imgur.com/2j1NCUz.png"/>
</p>
<p>
Use the Azure portal to block ICMP traffic in the network security group page create an inbound security rule to block ICMP traffic.
</p>
<br />

<p>
<img src="https://i.imgur.com/VwDMDc5.png"/>
</p>
<p>
Observe how the traffic changes when the security rule is implemented then disable the rule and observe how the traffic resumes as it did before.
</p>
<br />

<p>
<img src="https://i.imgur.com/aMwAFKd.png"/>
</p>
<p>
Type in Secure Shell (SSH) to isolate SSH traffic in wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/tPnpltK.png"/>
</p>
<p>
Open windows powershell and type SSH @labuser 10.0.0.5 to initiate the login process. This command uses the username and private IP address of your Ubuntu virtual machine. After you type in that command you will type in the word yes and then the password to your ubuntu virtual machine. This will generate SSH traffic that you can observe.
</p>
<br />

<p>
<img src="https://i.imgur.com/rPh7KM2.png"/>
</p>
<p>
Type dhcp into wireshark to isolate Dynamic Host Configuration Protocol (DHCP) traffic in wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/qGWavny.png"/>
</p>
<p>
Type ipconfig/renew into windows command line to generate DHCP traffic that can be observed in wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/mkuVSpw.png"/>
</p>
<p>
Type dns into wireshark to isolate Domain Naming System (DNS) traffic in wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/HSdcnNZ.png"/>
</p>
<p>
Type nslookup www.google.com to generate DNS traffic that can be observed.
</p>
<br />

<p>
<img src="https://i.imgur.com/3ZBxQ7H.png"/>
</p>
<p>
Type tcp.port==3389 into wireshark to observe Remote Desktop Protocol (RDP) traffic. Traffic is being generated because you are using RDP to connect to the virtual machine. This concludes 
</p>
<br />



