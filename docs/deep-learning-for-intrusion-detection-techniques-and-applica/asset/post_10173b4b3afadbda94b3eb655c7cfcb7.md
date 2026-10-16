
## Intrusion Detection in the Age of Deep Learning: An Introduction

Faheem Syed Masoodi

School of ICT, Bahrain Polytechnic, Isa Town, Kingdom of Bahrain

The exponential growth of mobile-driven internet traffic is closely tied to the evolving demands of society, particularly with the increased mobility of applications such as e-learning, e-banking, and e-health. This surge in internet usage has created a dynamic landscape where over 55% of website traffic globally originates from mobile devices, and a staggering 92.3% of internet users access the internet using mobile phones. This transformative shift, as of November 2023, reflects a substantial increase from levels as low as 6.1% (less than one-third) in 2011 and 37.2% in 2015 [1].

However, this surge in mobile connectivity is accompanied by a corresponding rise in cybersecurity threats. The widespread use of Internet of Things (IoT) devices has intensified the prevalence of cyberattacks. According to the Mobile and Wireless Communications Enablers for the Twenty-Twenty Information Society (METIS) report, common threats include brute-force attacks, malvertising, phishing, SQL injection, Distributed Denial of Service (DDoS) attacks, and malware. Notably, ransomware constitutes a significant portion of malware, accounting for 85% of observed instances in a given year [2].

As the world becomes increasingly reliant on internet connectivity for various aspects of daily life, the parallel increase in cybersecurity threats highlights the need for robust security measures to safeguard sensitive data and ensure the uninterrupted operation of essential services. This dual trend emphasizes the importance of addressing both the opportunities and challenges presented by the evolution of internet usage.

In this context, the integration of effective intrusion detection mechanisms becomes crucial for maintaining the security and resilience of digital ecosystems.

The continual evolution of intrusion detection technology is vital to staying one step ahead of the evolving threat landscape and ensuring the ongoing safety of internet interactions [3]. Before the advent of sophisticated intrusion detection systems (IDSs), network security relied on a patchwork of conventional measures that provided a degree of protection but were fraught with limitations [4]. To understand the significance of IDSs, we must first delve into the challenges posed by earlier security practices and the compelling reasons that drove the evolution of network security [5].

### 1.1.1 The Pioneers of Network Security

Before IDSs, several traditional security approaches were employed to safeguard networks and systems:

- 1. **Firewalls:** Firewalls acted as the initial line of defense by filtering outgoing and incoming traffic based on predefined rules. While effective at blocking unauthorized access by controlling ports and IP addresses, they were static and lacked the ability to detect complex attacks.
- 2. **Antivirus Software:** Antivirus programs were our trusted guardians against known malware threats. However, they struggled when confronted with new, previously unseen viruses and could not identify sophisticated, behavior-based attacks.
- 3. **Access Control Lists (ACLs):** Access control lists governed user access to network resources. Though vital for user management, they could not actively detect threats or unusual activities within the network.
- 4. **Security Policies:** Organizations established comprehensive security policies, outlining best practices and guidelines. While important, these policies could not actively monitor the network for threats or deviations from normal behavior.

### 1.1.1.1 Limitations of the Existing System

Despite their significance, these conventional security measures revealed glaring limitations:

- **Blind to the Unknown:** They excelled at countering known threats but remained oblivious to the emerging, novel attacks known as “zero-day” threats. This made them reactive, not proactive.
- **Lack of Behavioral Analysis:** Traditional security practices relied on predefined rules and signatures, missing the capacity to analyze network and user behavior. They could not identify deviations from normal patterns.
- **Limited Visibility:** With a focus on perimeter security, they had a restricted view of internal network activities. Attacks originating from within often went undetected.
- **False Alarms and Missed Threats:** These measures frequently produced false alarms, diverting attention away from real threats. Simultaneously, they missed subtle yet malicious activities, creating a trust deficit in security alerts.
- **Evolving Attack Techniques:** Cybercriminals were quick to adapt, employing advanced tactics such as polymorphic malware and evasion strategies that circumvented static security defenses.

It was against this backdrop of limitations and ever-evolving threats that IDSs emerged as a game-changer. IDSs introduced dynamic, behavior-based analysis, actively monitoring network traffic and system activities. They could identify anomalies, generate real-time alerts, and even take preventive actions.

As we journey through the world of IDSs, we will explore their various types, techniques, and their pivotal role in fortifying our digital landscapes against an ever-growing spectrum of threats. The story of IDS is not just a narrative of technological progress but also a testament to our unwavering commitment to securing the digital domain.

### 1.1.2 How Firewalls Are Different from IDS

Firewalls are primarily created to serve as a protective barrier or gatekeeper separating a secure internal network from potentially insecure external networks, such as the internet [1]. They enforce access control policies and decide which network traffic is allowed or blocked based on predefined rules. Firewalls are focused on preventing unauthorized access and traffic filtering. IDSs, on the other hand, are designed to monitor network traffic and system activities for signs of suspicious or malicious behavior. IDSs are intended for detection and notification of potential security threats or intrusions rather than actively blocking traffic. IDSs are valuable for detecting unknown or zero-day threats because they can identify unusual patterns or anomalies in network traffic by performing deep inspection of packets. Firewalls rely on predefined rules, so they may not detect new and evolving threats effectively. IDSs offer comprehensive data on security events and occurrences, encompassing details about the intrusion's characteristics, the IP addresses of both the source and target, the tactics employed, and additional information. This information is crucial for incident response and forensic analysis. Firewalls typically provide limited information beyond whether a connection was allowed or blocked. For comprehensive network security, it is advisable to use both firewalls and IDSs. Firewalls establish the first line of defense by controlling traffic and blocking known threats, while the IDS provides a second layer of defense by monitoring for unusual or suspicious activities that may bypass the firewall.

In summary, IDSs and firewalls have distinct roles in network security. Firewalls are primarily focused on access control and traffic filtering and cannot detect advanced attacks like Denial of Service (DoS), while IDSs are focused on monitoring and detecting potential advanced intrusions and security threats. To achieve a robust and layered security posture, organizations often deploy both IDSs and firewalls to provide proactive prevention and effective detection and response capabilities.

### 1.1.3 Need for Intrusion Detection Systems

When a private network or a system is connected to the internet, it becomes vulnerable to certain attacks and must be protected from such attacks. Any attempt that aims to get unauthorized access to the system resources and information that creates threat to confidentiality, integrity, availability, and authentication is called intrusion [2]. The private network or system’s ability to process, transfer, and store information has more value than the computer system it operates on. The network carries secret information, e.g., financial and personal data. It is desirable to protect the information transmission from an opponent and it becomes necessary to provide enough security to the system resources. Intrusion detection plays an important role in detecting the intrusions and preserving the security services. The security services are the actions taken by the security mechanism to provide sufficient security to the system and data transfers [3]. The goals of the security mechanism are to understand the attacks clearly and to find adequate solutions to tackle such problems. The four main principles of network security services are as follows:

- **Confidentiality:** Ensures that only authorized parties with sufficient privileges may view the sensitive and secret information. The transmitted data must be meaningless during the transmission and should be meaningful only to the intended user.
- **Authentication:** Authentication is a process of verifying the identity of the user, which assures the communication party, is one as it claimed. It ensures that the origin of the message or host is correctly identified.
- **Integrity:** Ensures that the data received is correct and no unauthorized person or malicious software has changed the data. Integrity is more than confidentiality and availability. Mechanisms used to protect the integrity of data include checksum and file hashing.
- **Non-Repudiation:** Non-repudiation prevents both the receiver and sender from denying that he/she has not sent or received the message.
- **Access Control:** This is a process of controlling and managing the necessary access to host systems and applications through communications links. Access control ensures specific access to particular users and prevents unauthorized use of system resources.
