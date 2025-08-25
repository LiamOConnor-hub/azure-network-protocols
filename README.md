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

- Observe ICMP Traffic
- Configuring a Firewall [Network Security Group]
- Observe DNS Traffic

<h2>Actions and Observations</h2>

<p>
Observe ICMP Traffic
In Azure, ICMP traffic can be observed by monitoring network connectivity between virtual machines. By using tools like ping or Azure Network Watcher’s connection troubleshoot feature, you can verify whether packets are successfully reaching the destination VM. Observing ICMP responses helps confirm that VMs are correctly networked within the virtual network and that no network restrictions are blocking basic connectivity.
  
- Log in to both virtual machines in the Azure virtual network.
- Open a command prompt on one VM.
- Use the ping command to send ICMP requests to the other VM (e.g., ping <VM-IP>).
- Observe the responses to verify packet delivery.
- Record any failed requests and check network configuration if ICMP is blocked.

</p>
<br />

Configuring a Firewall [Network Security Group]
Network Security Groups (NSGs) in Azure act as virtual firewalls, controlling inbound and outbound traffic to resources within a subnet or network interface. By creating rules to allow or deny specific traffic (such as permitting TCP port 80 for web servers or blocking ICMP from external networks), you can observe how changes to the NSG immediately affect connectivity. Monitoring these effects shows the practical impact of firewall rules on VM communication and overall network security.

- Navigate to the Network Security Group (NSG) associated with your VM or subnet in the Azure Portal.
- Review existing inbound and outbound rules.
- Add a rule to allow or deny specific traffic, such as permitting TCP port 80 or blocking ICMP.
- Test connectivity from a VM to verify that the rule takes effect.
- Observe how changes in NSG rules immediately impact traffic flow and record results.

</p>
<br />

<p>
Observe DNS Traffic
DNS traffic in Azure can be observed by examining how domain name queries are resolved between VMs and DNS servers. Using tools like nslookup or Azure’s diagnostic logs, you can track requests to the configured DNS server and responses returned. Observing DNS traffic ensures that name resolution is functioning correctly, which is critical for both Active Directory services and general network communication within the Azure environment. And always rermeber to see the most up-to-date data use the ipconfig /flushdns to clear the DNS cache

- Log in to a VM in your virtual network.
- Open a command prompt and use nslookup to query domain names within the network (e.g., nslookup mydomain.local).
- Monitor responses to ensure queries are resolved correctly by the configured DNS server.
- Optionally, review Azure diagnostic logs to observe DNS request traffic.
- Record any failures or delays to confirm proper DNS functionality within the network.
</p>
<br />
