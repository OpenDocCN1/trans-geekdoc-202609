
| DOS/DDOS attack || Data packet forwarding ||  ||  || ✓ |

| Spoofing attack || Network devices || ✓ || ✓ ||  |

| Intrusion attack || Packet processing engines || ✓ || ✓ ||  |

| Scanning attack || MAC layer || ✓ ||  ||  |

| Tampering attack || Forwarding tables || ✓ ||  ||  |

| Hijack attack || Network devices ||  ||  ||  |

| Side channel attack || Packet buffer || ✓ || ✓ ||  |

| Anomaly attack || Traffic classification and filtering || ✓ || ✓ ||  |

It’s important to note that attacks can often fall into multiple categories, and the classification of attacks may vary depending on the specific context and perspective of the analysis. This categorization provides a high-level overview of how attacks can be classified based on different factors, but it is not an exhaustive list. The evolving nature of SDN technol-ogy may introduce new attack vectors and techniques that may require further categorization and analy-sis. There are some attacks which are affecting mul-tiple planes (Abd Elazim et al., 2018; [Hegazy et al. 2021](#ch33.xhtml#ref33_14); [Alhaj et al., 2022](#ch33.xhtml#ref33_13)) simultaneously.[Table 33.4](#ch33.xhtml#tab33_4) is giving the view of these types of attacks with their attacked area, plane and affected functionality. For better understanding of these attacks,[Table 33.4](#ch33.xhtml#tab33_4) is also giving brief view about these attacks with one example.

[Table 33.4 Categorization of attacks, affecting multiple planes](#ch33.xhtml#R_tab33_4)

| Attack || Plane attacked || Attacked area || Affected functionalities || Example |
| --- | --- | --- | --- | --- |
| Man-in-the-middle (MitM) (Anusuya, 2021) attacks || Control plane || SDN controller || Manipulate flow rule, unauthorized control || An attacker intercepts communication between the SDN controller and a switch, modifies the flow rules being installed, and redirects traffic to their own malicious network |
|  || Data plane || Switches || Inject malicious content, impersonate network devices || An attacker performs ARP spoofing to intercept traffic between two SDN switches, allowing them to intercept and modify the traffic exchanged between the switches |
| Protocol-level attacks (Sjoholmsierchio et al., 2021) || Control plane || OpenFlow protocol || Manipulate northbound API || An attacker sends forged OpenFlow control messages to manipulate flow rules or inject malicious commands into the SDN network |
|  || Data plane || Routing protocols e.g., OSPF (Rego et al., 2019), BGP (Manzoor et al., 2020) || Traffic manipulation, network misconfigurations || An attacker injects false OSPF routing updates to redirect traffic to a compromised network segment under their control, enabling them to intercept or manipulate the traffic |
| DDoS attacks (Yue et al., 2020) || Control plane || SDN controller || Disrupt its operation, render it unavailable || An attacker overwhelms the SDN controller resources by initiating a flood of flow setup request which leads to make unable to establish or modify flows as intended, causing a denial of service |
|  || Data plane || Switches Router || Performance degradation, unavailability || The attacker’s goal is to exhaust the flow tables’ capacity in SDN switches by overwhelming them with a large number of flow entries |
| Information disclosure attacks (Patwardhan et al., 2019) || Control plane || Northbound API || Revealing network, vulnerabilities || The attacker collects sensitive information about the network, flow tables, traffic patterns, or topology and analyzes the gathered information to identify potential weaknesses or vulnerabilities in the SDN infrastructure |
|  || Data plane || Flow tables || Revealing network configuration, revealing policy details || An unauthorized user or a malicious actor attempting to exploit vulnerabilities in the SDN switches |
| Time-of-check to Time-of-use (TOCTTOU) attacks (Xu et al., 2017) || All planes || Network resources || Unauthorized manipulation, interception of traffic || TOCTTOU attacks take advantage of the window of opportunity that exists between the checking of a resource’s state and the utilization of that resource, allowing an attacker to manipulate or abuse it during that interval |

These examples illustrate how each attack type can be carried out in an SDN environment. Attackers can employ variations and combinations of these attacks, and the specific techniques used may vary depending on the attacker’s goals and the vulnerabilities present in the SDN infrastructure.

## Attack vectors and techniques

Attack vectors and techniques is a pathway or method used by the attackers for illegal access of network and launch attacks in SDN ([Mahajan et al., 2020](#ch33.xhtml#ref33_23); [Hegazy et al., 2021](#ch33.xhtml#ref33_14)). Knowledge of these vectors and techniques helps to improve security of the system.[Table 33.5](#ch33.xhtml#tab33_5) is giving summary about these attack vectors with their method and technique. For better understanding of this,[Table 33.5](#ch33.xhtml#tab33_5) is also giving brief about their effect and latest tools used by the attacker. Disease may be transferred from patients to doctors and vice-a-versa.

[Table 33.5 Attack vectors with their tools and techniques](#ch33.xhtml#R_tab33_5)

| Attack vector and techniques || Techniques || Consequences in SDN || Used tools |
| --- | --- | --- | --- |
| Network reconnaissance || 

*   Network scanning

*   Enumeration

*   Probing

 || 

*   Reveal potential vulnerabilities

*   Reveal potential entry points

 || 

*   Nmap,

*   Zmap

*   Masscan

 |
| Social Engineering (Gallegos- Segovia et al., 2017) || 

*   Phishing

*   Impersonation

*   Deception

 || 

*   Unauthorized access

*   Network manipulation

 || 

*   Maltego

*   Social engineering kit (SET)

*   Wifiphisher

*   MetaSploit MSF

*   MSFPC

 |
| Malware injection || 

*   Inject malicious code

*   Inject malicious SQL

 || 

*   Data exfiltration

*   Traffic interception

*   Unauthorized flow rule modification

 || 

*   SQL injection

*   Cross-site scripting (XSS)

 |
| Exploiting weak authentication || 

*   Brute-forcing passwords

*   Exploiting weak encryption

*   Leveraging insecure authentication protocols

 || 

*   Unauthorized access

 || 

*   OpenDaylight exploitation framework (ODEF)

*   Floodlight exploit framework (FEF)

 |
| Zero-day exploits || Target unknown vulnerabilities or weaknesses before they are discovered and patched by vendors || 

*   Unauthorized access

*   Compromise systems

*   Manipulate network behavior

 || 

*   Metasploit

*   ExploitDB

 |
| Forged or faked traffic || Flooding the network resources || 

*   Unavailability

*   Performance degradation

*   SYN floods

*   UDP floods

*   ICMP floods

 || 

*   Hping

*   LOIC (Low Orbit Ion Cannon)

*   Xerxes

 |
| Man-in-the-middle (MitM) attacks || 

*   Interception

*   Manipulation

*   Altering

*   Eavesdropping

*   ARP spoofing

*   DNS spoofing

*   SSL/TLS interception

 || 

*   Modify traffic

*   Inject malicious content

*   Unauthorized control

 || 

*   Ettercap

*   Wireshark

*   Tcpdump

 |
| Packet sniffing and Eavesdropping || 

*   Tapped transmission link

*   Monitor open network

*   Hack weak password

*   Eavesdrop pickup devices

 || 

*   Unauthorized access

*   Network manipulation

 || 

*   Scapy

*   Hping

*   Ostinato

 |
| Protocol manipulation || 

*   Inject malicious commands

*   Modify flow rules

*   Redirect traffic to unauthorized destinations

 || 

*   Manipulate network behavior

*   Bypass security controls

*   Disrupt communication

 || 

*   Sulley

*   Peach

*   AFL (American Fuzzy Lop)

 |
| Backdoor installation || Deploy malware || 

*   Manipulate network behavior

*   Bypass security measures

 || 

*   Botnets

 |
| Physical attacks || Tampering with SDN devices or infrastructure || 

