
### 9.
Your intrusion detection software uses a baseline, and any activity outside that baseline is considered suspicious traffic. What type of analysis is being performed?

A. Anomaly
B. Heuristic
C. Passive
D. Signature

### 10.
John has implemented an intrusion detection system that has identified suspicious traffic without the use of signatures. While responding to the event, John notices that the IDS has falsely identified the traffic as being suspicious. Which of the following devices does John need to configure to prevent additional false alarms?

A. Signature-based IDS
B. Anomaly-based IDS
C. Anomaly-based IPS
D. Host-based IDS

### 11.
The information system security officer (ISSO) for the organization is concerned that attacks against the web server will be successful if the hacker has an unlimited number of attempts. Which of the following is designed to stop attacks on a specific server?

A. HIDS
B. NIDS
C. NIPS
D. HIPS

### Network Design and Administration Principles

### 12.
You have a small network with all servers and workstations connected to a single switch. Your manager would like to ensure that no system outside the systems in the accounting department can communicate with the accounting server. What would you do?

A. Get another switch and connect the accounting systems to that switch.
B. Get a router and create two networks.
C. Get a proxy server to control communication.
D. Use VLANs on the switch.

### 13.
When a system tries to connect to a network, the system is checked to ensure that it has recent patches and virus definitions before being allowed to communicate on the network. What service can be used to do this?

A. NAT
B. Proxy
C. NAC
D. VLAN

### 14.
What type of system is typically used to monitor and control which web sites a user visits and can block content based on information in the content being accessed?

A. NAT
B. Proxy
C. NAC
D. VLAN

### 15.
You are monitoring network traffic on the LAN and notice a large number of packets that use the SIP and RTP protocols. Which of the following actions would you take to segment that traffic on the LAN?

A. Create a DMZ.
B. Configure NAT.
C. Implement an NIPS.
D. Create a voice VLAN.

### 16.
You are looking to use IPSec to provide encryption, authentication, and data integrity services. Which IPSec protocol would you use?

A. AH
B. IKE
C. ESP
D. PPTP

### 17.
Your manager would like to implement a VPN solution that encrypts all communication that travels across the Internet between the two office locations with minimal configuration on each client. What would you recommend?

A. Full tunnel
B. Site-to-site VPN
C. Remote access VPN
D. Split tunnel

### 18.
You are the security administrator for your company and you would like to prevent employees from e-mailing sensitive data to their personal e-mail accounts. How would you do this?

A. DLP
B. NAC
C. VPN
D. NAT

### Securing Devices

### 19.
Which of the following represents the first thing you should do after purchasing a wireless router?

A. Disable DHCP.
B. Configure proxy rules.
C. Configure VLANs.
D. Set a password on the device.

### 20.
Your manager is concerned about the vulnerabilities that may exist with a specific switch that was purchased for the office network. What can you do to ensure that you are protected from known vulnerabilities?

A. Enable the firewall.
B. Configure logon hours.
C. Update the firmware.
D. Configure VLANs.

### Performance-Based Questions

### 21.
You are responsible for configuring the company firewall. Using the network diagram as a guide, choose the firewall rules you would configure using these requirements:

- Only accounting systems can communicate with `12.0.0.10` using HTTPS.
- Only accounting systems can communicate with `12.0.0.10` using SMTP.
- All systems can communicate with `12.0.0.11` with any type of traffic.

![Image](f0383-01.jpg)

### 22.
Match the term on the left with the description on the right.

![Image](f0384-01.jpg)

### SELF TEST ANSWERS

#### Understanding Firewalls

### 1.
![Image](boxt.jpg) **D.** A stateful packet inspection firewall understands the state of the conversation and what packets it should expect to receive. If a packet is received that is out of the context of the conversation, then the firewall does not allow the packet, even though it may be destined for a port that is open on the firewall.

![Image](boxx.jpg) **A, B,** and **C** are incorrect. Although a stateful packet inspection firewall can filter traffic based on source/destination IP address and source/destination port number (packet-filtering firewalls can do that as well), what makes it unique is understanding the context of the conversation. An application-layer firewall can filter traffic based on the application data (also known as the payload).

### 2.
![Image](boxt.jpg) **B.** An application-layer firewall can inspect the application data and allow or disallow certain functions of an application through the firewall. This is more advanced than simply opening a port. For example, port 80 may be opened on the firewall, but the application firewall can also restrict the traffic to allow only HTTP `get` commands and not HTTP `put` commands.

![Image](boxx.jpg) **A, C,** and **D** are incorrect. A packet-filtering router filters traffic based on the source/destination IP address and the source/destination port number. A stateful packet inspection firewall can filter traffic based on the IP address and port information, but it also understands if a packet is received out of context. A screened-host firewall is a topology and not a type of firewall.

### 3.
![Image](boxt.jpg) **D.** A screened-host firewall is a firewall that has a packet-filtering router placed in front of it that filters the traffic based on the layer-3 header or layer-4 header. The information that passes through the packet-filtering router then hits the firewall and must meet the firewall rules in order to reach the internal network.

![Image](boxx.jpg) **A, B,** and **C** are incorrect. Packet-filtering and application-layer firewalls are types of firewalls and not topologies. A dual-homed firewall is a system that has two network cards installed and firewall software installed on the system.

### 4.
![Image](boxt.jpg) **B.** In order to control traffic to a specific system, Emily should use a host-based firewall. A host-based firewall is typically software installed on a system that allows you to control traffic to that specific system.

![Image](boxx.jpg) **A, C,** and **D** are incorrect. A network firewall can control communication, but it controls communication to the network, not a specific system. In this case, an IDS and IPS are not used, as the goal is to control communication, not monitor it.

### 5.
![Image](boxt.jpg) **D.** In order to block DNS zone transfers, you will deny TCP 53 traffic.

![Image](boxx.jpg) **A, B,** and **C** are incorrect. Answer A is a rule that would block all TCP/IP traffic, whereas answer B would block DNS queries from clients. Answer C would block SMTP traffic.

### 6.
![Image](boxt.jpg) **B.** In this scenario you should recommend that the wireless guest network be in a separate zone from the corporate network, which would be the intranet zone. Using a firewall to create zones allows you to control whether communication can occur between the two zones, which in this case you do not want to occur.
