
A, C, and D are incorrect. Neither Wireshark nor tcpdump perform as a syslog aggregator, an intrusion detection system, or a port scanner. Although Wireshark could technically be set to alert if a particular packet or part of a packet was captured, that is far from its intended purpose.

16. Which of the following is not included when capturing packet headers but is provided with full packet capture?

-   A. Source address
-   B. Payload
-   C. Protocol flags
-   D. Destination address

-   B is correct. The payload is not captured when only the packet header is captured.

-   A, C, and D are incorrect. The header contains source and destination addresses, protocol flags, TTL, a header checksum, and protocol version—all dependent on the exact protocol in use.

17. Which of the following statements is not true when it comes to syslog?

-   A. Syslog supports a broad range of devices and events.
-   B. Messages can be aggregated into a single, non-hierarchical file.
-   C. Devices can be polled for messages, echoing back to a syslog server.
-   D. The syslog protocol and messaging core native in most firewalls and network devices as well as Unix systems.

-   C is correct. Syslog does not "poll" devices for event messages. Syslog messages are sent to a syslog server, with no prompting.

-   A, B, and D are incorrect. A is incorrect because a wide variety of devices and types of messages are supported by syslog. B is incorrect because syslog messages are collected and shown as a flat file. D is incorrect because such network devices and Unix systems support syslog.

18. A company is frustrated by its firewall's inability to catch higher-level malicious attacks, such as SQL injection and cross-site scripting (XSS). The firewall is unable to distinguish valid HTTP traffic and malicious attacks when traffic traverses the firewall on port 80. What do you see as the primary limitation of the firewall?

-   A. The firewall is an application-layer firewall, unable to identify the higher-layer data.
-   B. The firewall needs to be partnered with an IDS or IPS.
-   C. The firewall rules need to be reviewed and likely changed.
-   D. The firewall is a layer 3 or 4 device and should be replaced with an application-layer device.

-   D is correct. The problem described seems to point to a standard firewall that's unable to inspect application-layer traffic. It should be replaced with a capable, application-layer firewall.

-   A, B, and C are incorrect. A is incorrect because it is false to claim the application-layer firewall is unable to identify higher-layer data. B is incorrect because, although an IDS/IPS would help, the firewall's shortening is the primary issue here. C is incorrect because the rules are likely not able to address the application-layer issue.

19. If an attacker is using nmap to map the network topology, which of the returned states of the port scans provides the least information? 

-   A. Unfiltered
-   B. Filtered
-   C. Closed
-   D. Open

-   B is correct. Filtered state means the nmap probe scan was unable to reach the port, or hear back whether the port was open or closed. This would make the attacker’s efforts most difficult in mapping the network topology in order to understand the various network areas such as DMZ, perimeter devices, and other key network components.

-   A, C, and D are incorrect. A is incorrect because unfiltered nmap was able to reach the port but unable to determine conclusively whether it was open or closed. The unfiltered state only applies when an ACK scan is being performed, often to map firewall rules. C is incorrect because closed means the port was reached and decidedly closed. D is incorrect because open means the port was reached and concluded to be open or listening.

20. What would be an appropriate tool for performing service discovery on a large network?

-   A. An IDS (but no IPS) placed anywhere on the servers’ local subnet
-   B. A HIDS placed on a target server
-   C. Any tool to review firewall logs or router ACLs
-   D. A port scanner

-   D is correct. Port scanner would quickly reveal what ports (and the services behind them) are open and listening on devices on the scanned network.

A, B, and C are incorrect. A and B are incorrect because an IDS/HIDS (but not an IPS) should alert on valid services instead of only detected malware traffic. C is incorrect because reviewing firewall logs and router ACLs will tell about flagged traffic attempts and permitted traffic, but provides little information about services and the systems providing them.

21. When you're capturing packets on a wireless network versus a wired network, which of the following statements are true? (Choose all that apply.)

-   A. Using promiscuous mode to view all packets applies on both wired and wireless networks.
-   B. Being in monitor mode allows for the capture of all 802.11 activity, without connection to the access point.
-   C. Wireless signals can be relatively limited beyond a physical presence such as a fence.
-   D. Strong, secure encryption provides no protection against data exposed eavesdropping.

-   A and B are correct. A is correct because promiscuous mode, if supported by the wireless card, is what allows the card to process all 802.11 activity, not just traffic targeted to that card. B is correct because monitor mode allows the same visibility to all activity, even without being connected to an access point.

-   C and D are incorrect. C is incorrect because wireless signals are generally not affected by thin structures. D is incorrect because strong encryption does protect against eavesdropping.

# Analyzing the Results of Reconnaissance

This chapter includes questions on the following:
- Sources of data to consider in analysis
- Point-in-time data analysis
- Data correlation and analysis
- Common tools used in security

In the prior chapter, you applied tools and techniques to conduct reconnaissance. Benefiting from reconnaissance takes more than just collecting information. The analysis is what changes the collected data into something useful. Careful analysis involves a variety of sources. Sources include various logs, devices on the perimeter or within the network, and data you've personally collected. You might analyze data from a snapshot in time or across a period of time. Depending on what you're looking for, you have an assortment of tools at your disposal—and that is what this chapter is all.

1. Which of the following data sources would offer the most diverse, precise kind of information?

-   A. Syslogs
-   B. Firewalls
-   C. Packet captures
-   D. Nmap results

2. What device combines the functionality of a traditional firewall and an IPS?

-   A. Next-Generation Firewall
-   B. DSN firewall
-   C. Enterprise firewall
-   D. Discovery firewall

3. Which of the following are the two types of approaches to analyzing data?

-   A. Compare and contrast
-   B. Correlation
-   C. Patterned
-   D. Point-in-time

4. In an IP packet header, what field value is decremented with each interface the packet goes through?

-   A. Fragment offset
-   B. ToS
-   C. TTL
-   D. IHL

5. Which of the following is an example of point-in-time analysis?

-   A. Anomaly analysis
-   B. Behavioral analysis
-   C. Availability analysis
-   D. Traffic analysis

Use the following scenario to answer Questions 6–9:
Recently, a few users have been complaining that their workstations are exhibiting some strange behavior. However, you find no obvious events showing up in system logs, and the application logs show nothing out of the ordinary. You suspect the issue could be new malware and decide to delve deeper.

6. You inspect logs from multiple sources. Your hope is to find some odd behavior. What type of analysis are you performing now?

-   A. Trend
-   B. Heuristics
-   C. Packet count
-   D. Spatial trend

7. Based on your assumptions, how will you likely discover the malware?

-   A. The packet trace will reveal a port famous for malware.
-   B. The IDS log will show a matched signature.
