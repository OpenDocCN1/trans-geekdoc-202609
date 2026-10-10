
# CERTIFICATION SUMMARY

In this chapter you learned about common network components that can be used to help increase security in your network environment. Be sure to know the content of this chapter well because you are sure to get questions on firewalls, NAT, NAC, and other security devices on the Security+ exam. The following are some key points to remember regarding this chapter:

- **DoS** A variety of denial of service attacks can be performed against network systems and devices. Implementing a flood guard on your firewall should protect your system from most DoS attacks, because most involve the hacker attempting to flood your system with so much information that it crashes your system. A flood guard blocks the flood messages from entering your network.
- Know the difference between a packet-filtering firewall (stateless), a stateful packet inspection firewall, and an application-layer firewall.
- Different firewall topologies include a dual-homed firewall, screened-host firewall, and screened-subnet firewall. Your firewall design should create different zones on the network, such as the private zone and the public zone.
- Proxy servers are popular devices that allow you to control the type of content and applications users on the network can use when accessing the Internet.
- Know the difference between a host-based IDS and a network-based IDS. Also know that an IDS detects an intrusion, whereas an IPS detects and prevents an intrusion.
- Use network design principles to help create a secure network environment, such as creating multiple network segments and controlling what traffic can pass from one segment to another.
- Don't confuse NAT and NAC. NAT is a feature that is used for Internet access and translates the private address information to a public address. NAC is used to check the state of the system connecting to the network, and if it does not pass the requirements, then the system is not connected to the network.
- Common security practices with regard to network devices include ensuring that complex passwords are used, renaming or disabling default accounts, and keeping the system up to date with patches, to name a few.

## ✓ TWO-MINUTE DRILL

### Understanding Firewalls

- A packet-filtering firewall allows you to filter traffic by the layer-3 header (IP) and the layer-4 header (TCP or UDP). A stateful packet inspection firewall can do packet filtering, but also knows about the context of the conversation. An application-layer firewall can look at the application data in the packet and make decisions.
- The DMZ is a zone that allows selected traffic from the Internet to reach public servers such as DNS, FTP, and HTTP servers.
- A proxy server typically incorporates firewall features with content control features. For example, you can restrict what sites a user can visit or the types of applications they can use to access the Internet.

### Using Intrusion Detection Systems

- A network-based intrusion detection system analyzes network traffic to identify suspicious activity.
- An intrusion detection system (IDS) logs suspicious activity and notifies the administrator, but an intrusion prevention system (IPS) takes corrective action. For example, an IPS may disconnect the person responsible for the suspicious traffic from the network.
- For the exam, know that IDSs can detect suspicious traffic based on signatures (signature-based IDS) or can identify suspicious traffic based on the traffic being outside the parameters of normal activity (anomaly-based IDS). Also know that heuristic monitoring involves detecting suspicious traffic based on past experience.

### Network Design and Administration Principles

- Create communication boundaries within the network by using VLANs on a network switch.
- You can also create different network segments by placing routers on the network and controlling what traffic can enter different network segments using access control lists on the router (for example, separating your wireless network for visitors from the corporate network).
- Data loss prevention (DLP) technologies can be used to prevent someone from stealing or sharing sensitive company data.
- Network access control (NAC) allows you to check the state of the system before a system is granted access to the wired or wireless network.
- Implement spam filtering features and antivirus software on your mail gateway to keep employee mailboxes clean of spam messages and messages containing viruses.

### Securing Devices

- Ensure that network devices have strong passwords.
- Be sure to patch devices to eliminate vulnerabilities on them.
- Rename or disable default accounts on the devices if possible.

## SELF TEST

The following questions will help you measure your understanding of the material presented in this chapter. As indicated, some questions may have more than one correct answer, so be sure to read all the answer choices carefully.

### Understanding Firewalls

**[1.]** Which of the following identifies the benefit of a stateful packet inspection firewall?

A. Can filter traffic based on the source and destination IP address
B. Can filter traffic based on the source and destination port number
C. Can filter traffic based on the application data
D. Can filter traffic based on the context of the conversation

**[2.]** Which type of firewall has the capabilities to inspect the payload of a packet to determine if the content is allowed to pass through the firewall?

A. Packet-filtering firewall
B. Application-layer firewall
C. Stateful packet inspection firewall
D. Screened-host firewall

**[3.]** What firewall topology typically involves having a router placed between the firewall and the Internet?

A. Packet-filtering firewall
B. Application-layer firewall
C. Dual-homed firewall
D. Screened-host firewall

**[4.]** Emily, a senior security officer for Company XYZ, is responsible for ensuring systems meet certain security requirements. Emily needs to ensure the security of the accounting systems by making sure that any systems running the accounting software have specific ports closed down. Which of the following should Emily use?

A. A host-based IDS
B. A host-based firewall
C. A network firewall
D. A host-based IPS

**[5.]** You are the firewall administrator for Company XYZ and need to ensure that DNS zone transfers are blocked at the firewall. Which of the following rules would you use?

A. deny ip any any
B. deny udp any any port 53
C. deny tcp any any port 25
D. deny tcp any any port 53

**[6.]** Your manager approaches you and is concerned that customers who visit and connect to the wireless guests SSID will be able to access corporate data and assets. What security solution would you recommend?

A. Implement network access control.
B. Segment into different zones.
C. Install network address translation.
D. Use data loss prevention policies.

### Using Intrusion Detection Systems

**[7.]** Which network-based IDS component is responsible for analyzing the traffic against the signatures?

A. Sensor
B. Notification
C. Engine
D. Signature database

**[8.]** You have intrusion detection software that can monitor activity and identify suspicious activity based on past experience. What type of analysis is being performed?

A. Anomaly
B. Heuristic
C. Passive
D. Signature
