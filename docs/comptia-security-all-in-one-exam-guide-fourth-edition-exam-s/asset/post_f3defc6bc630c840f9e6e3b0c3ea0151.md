
4. Your colleague tells you that he has prepared a server for the production environment. He says that he has patched it, made sure all the accounts have strong passwords, and removed all the development code that was on it. When you scan the server, a large number of open ports respond. What did your colleague forget to do when securing this server?
A. Install antivirus software
B. Disable unnecessary services
C. Enable auditing
D. Disable MAC filtering

5. Your boss is trying to find more information about port-based network access control. Which of the following IEEE standards should she be looking at?
A. 802.1x
B. 802.11x
C. 802.x
D. 801.2x

6. Your organization is having a serious problem with people bringing in laptops and tablets from home and connecting them to the corporate network. The organization already has a policy against this, but it doesn’t seem to help. Which of the following mitigation techniques might help with this situation?
A. Disabling unnecessary services
B. Rogue machine detection
C. Syslog auditing
D. Password protection

7. Your boss wants a network device that will detect malicious network traffic as it happens and stop it from reaching systems inside your network. She has asked you to come up with several different options and present them to her in the morning. You should start researching which of the following?
A. Intrusion detection systems
B. Intrusion prevention systems
C. Firewalls
D. Continuous auditing systems

8. Which of the following is not a step you’d perform when hardening a production system?
A. Disable unnecessary services
B. Disable unnecessary accounts
C. Enable simple TCP services
D. Configure auditing

9. A buffer overflow attack was launched against one of your Windows-based web servers. You'd like to know what process was affected on the server itself. Where might you look for clues as to what process was affected?
A. Access log
B. Application log
C. Security log
D. Setup log

10. An intrusion detection system is most like which of the following physical security measures?
A. Locked door
B. Electrified fence
C. Security camera
D. Mantrap entry

11. Which of the following can be used to assist in hardening a network? (Choose all that apply.)
A. MAC limiting
B. 802.11
C. Rogue user detection
D. Disable unused ports

12. Your boss is considering outsourcing the network security tasks for your organization. There are several proposals to look at, many of which claim to “collect information from security controls and perform analysis based on pre-established metrics.” What capability are these vendors referring to?
A. Global monitoring service
B. Continuous security monitoring
C. Intrusion prevention system
D. Metrics-based security analysis

13. Which of the following types of log entries will you not find in Windows Security logs?
A. Account logon events
B. Object access events
C. Policy change events
D. System shutdown events

14. Which of the following are common logs associated with a system? (Choose all that apply.)
A. Security
B. Failure
C. System
D. Data integrity

15. A password policy should address the following questions: _______, _______, and _______.

## Answers

1. C. The best source of information for this situation is going to be the security logs. Because this is a domain account and most likely on a Windows system, you will want to look at all failed logins associated with this account. Those are stored in the security logs.

2. C. Your boss just asked you to create an initial baseline configuration. The configuration you develop will become the starting point for all Windows 8 desktops. While the desktops may look different as department-specific software packages are loaded, they will all start off with the same attributes and security configuration from that initial baseline.

3. A. MAC filtering techniques can control which MAC addresses are allowed to send or receive traffic across specific switch ports. If you were to lock down that network jack to the MAC address of the PC in the locked cabinet, that would help stop anyone else from using the network jack without permission.

4. B. If a server has a large number of active ports, it is likely running a large number of services. Disabling unnecessary services should be part of the system build process for all production (and development) systems. Disabling or removing unnecessary services can reduce the attack surface of the system.

5. A. If your boss is researching port-based network access control, then she should be looking at IEEE 802.1x.

6. B. Rogue machine detection is a mitigation technique to find unwanted, unauthorized devices and systems on your network. Once you've discovered the rogue machines, you can track them down and discipline those responsible for connecting them to the network.

7. B. Your boss is looking for an intrusion prevention system (IPS). An IPS is very similar to an intrusion detection system (IDS), with one marked difference: an IPS is designed to interact with and stop malicious traffic.

8. C. When hardening a system, one of the objectives is to remove or disable unnecessary services. The simple TCP services such as ECHO, CHARGEN, and so on should typically be disabled as part of any system hardening process.

9. B. On a Windows-based server, the best place to look for information about what processes were affected by a buffer overflow attack would be the application logs.

10. C. An intrusion detection system is most like a security camera. An IDS has the ability to monitor for suspicious activity and can record what it has “seen.”

11. A and D. MAC limiting and disabling unused ports are valuable security functions in setting up a network. 802.11 is the designation for Ethernet, and is not a direct issue (802.1x is, not 802.11). Rogue user detection is beyond the network function.

12. B. Continuous security monitoring is an attempt to answer that age-old question, “Are we secure?” By collecting data from implemented security controls such as firewalls, IDS/IPS, policies, and so forth and analyzing the data against established metrics, organizations hope to gain a better picture of the security state of their networks. For example, if the perimeter firewall records a sharp rise in outbound traffic on UDP port 33456, this could be an early indication of some type of botnet infection.

13. D. System shutdown events would be noted in the System event log, not the Security log.

14. A and C. Security and System logs are examples of common system logs.

15. A password policy should address: What is an acceptable level of risk? How secure does the system need to be? How often should users change their passwords? What account lockout policy should be used? What password composition rules should be enforced?

## Protocol Analyzer

As introduced in Chapter 1, a protocol analyzer is simply a tool (either hardware or software) that can be used to capture and analyze traffic passing over a communications channel, such as a network. Although protocol analyzers exist for many types of communication channels, such as telecommunications traffic and system buses, the most common use of a protocol analyzer is for the capture and examination of network traffic. In the networking world, this is most commonly referred to by a variety of names such as packet sniffer, network analyzer, or network sniffer. Sniffers can be used to capture and analyze wired or wireless traffic and can be software based (most common) or a dedicated hardware/software platform. An effective sniffer must have the ability to place a network interface in promiscuous mode, which tells the interface to accept and process every packet it sees—not just packets destined for this specific system or sent to a broadcast, multicast, or unicast address. On a switched network, sniffers are typically plugged into a SPAN (discussed in the next section) or monitor ports that are configured to receive copies of packets passing through one or more interfaces on the same switch. Capabilities of packet analyzers vary greatly—some do nothing more than simple packet capture, whereas others attempt to reconstruct entire TCP/IP sessions with decoded packets and color-coded traffic streams.

From a security perspective, protocol analyzers are very useful and effective tools. Want to see if any system on your network is transmitting traffic on a specific port? Want to see if any packets are being sent to an address at a rival company? Want to see which employees spend all day surfing eBay? Want to find the system that’s flooding the local network with broadcast traffic? A protocol analyzer can help you address all these issues and more—if you have the analyzer plugged into the right location of your network and can “see” the traffic you are concerned about. Most organizations will have multiple points in the network where traffic can be sniffed—in the core switch, between the user base and the server farm, between remote users and the core network, between the organization and any link to the Internet, and so on. Knowing how to ensure the sniffer can “see” the traffic you want to analyze, knowing where to place the analyzer, and knowing how to use the analyzer are all keys to getting the best results from a protocol analyzer.

## Switched Port Analyzer

The term Switched Port Analyzer (SPAN) is usually associated with Cisco switches—other vendors refer to the same capability as port mirroring or port monitoring. A SPAN has the ability to copy network traffic passing through one or more ports on a switch or one or more VLANs on a switch and forward that copied traffic to a port designated for traffic capture and analysis (as shown in Figure 16-1). A SPAN port or mirror port creates the collection point for traffic that will be fed into a protocol analyzer or IDS/IPS. SPAN or mirror ports can usually be configured to monitor traffic passing into interfaces, passing out of interfaces, or passing in both directions. When configuring port mirroring, you need to be aware of the capabilities of the switch you are working with. Can it handle the volume of traffic? Can it successfully mirror all the traffic, or will it end up dropping packets to the SPAN if traffic volume gets too high?
