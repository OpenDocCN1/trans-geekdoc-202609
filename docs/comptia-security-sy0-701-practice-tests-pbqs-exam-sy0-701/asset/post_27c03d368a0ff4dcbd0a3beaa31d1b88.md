
as staff need to be trained on the new system. The primary benefits of platform diversity are resilience, redundancy, and diversifying the attack surface.

**Option B is incorrect.** This is one of the benefits of platform diversity. If a vulnerability or threat targets UNIX-based systems, having a backup on a different platform ensures that the backup isn't compromised by the same threat.

**Option C is incorrect.** This is a benefit of platform diversity. Platform-specific outages or issues would only affect systems on that platform, so having a backup on a different platform adds resilience.

**Question 377.** After a recent security incident, Sarah, a network security analyst, wants to analyze the flow data of network traffic to identify patterns and potential threats. She wants to collect metadata about IP traffic flow and gather details like addresses, ports, and protocols used. Which tool should Sarah employ to obtain this information?

- (A) Intrusion Detection System (IDS)
- (B) Syslog server
- (C) NetFlow collector
- (D) Simple Network Management Protocol (SNMP) traps

**Explanation 377.** **Correct Answer: C. NetFlow collector.**
NetFlow is a network protocol developed by Cisco for collecting IP traffic information and monitoring network traffic. A NetFlow collector can provide insights into traffic flow patterns and volume, making it suitable for Sarah’s requirements.

Option A is incorrect. While an IDS can provide alerts on malicious activities based on specific signatures or heuristics, it does not provide detailed flow data analysis like NetFlow.

Option B is incorrect. A Syslog server is mainly used for collecting and storing log data from various devices. It does not focus on detailed network traffic flow like NetFlow.

Option D is incorrect. SNMP traps are for sending unsolicited alert messages from a device to a management station regarding specific events. They don’t provide traffic flow analysis.

**Question 378.** A large financial institution recently experienced a security breach where an attacker was able to bypass its intrusion detection system (IDS). Upon investigation, the security team found out that the attacker utilized a zero-day exploit. In the aftermath, what should the institution do to enhance the capability of its IDS?

- (A) Switch from a signature-based IDS to a behavior-based IDS
- (B) Disable the IDS and rely solely on firewall rules
- (C) Update the IDS with the latest threat intelligence feeds and signatures
- (D) Reduce the frequency of IDS signature updates

**Explanation 378.** **Correct Answer: A. Switch from a signature-based IDS to a behavior-based IDS.** Behavior-based IDS (or anomaly-based IDS) monitors network traffic and compares it against an established baseline, allowing it to potentially detect zero-day exploits and other novel attacks that signature-based systems might miss.

Option B is incorrect. Relying solely on firewall rules without IDS would lessen the security depth and expose the institution to more risks.

Option C is incorrect. While updating the IDS with the latest signatures is important, it wouldn’t necessarily detect zero-day exploits until a signature for that exploit has been created and disseminated.

Option D is incorrect. Reducing the frequency of IDS signature updates would make the system even more vulnerable to recent threats.

**Question 379.** After a major power outage, TechWave Corp. wants to ensure their primary data center’s operations can be swiftly and seamlessly shifted to another facility. The company wants this process to be automated and immediate to prevent any service interruption. What type of test should TechWave Corp. conduct to validate this functionality?

- (A) Conduct a vulnerability assessment on both data centers
- (B) Execute a failover test
- (C) Engage in a tabletop exercise
- (D) Perform a routine backup test

**Explanation 379.** **Correct Answer: B. Execute a failover test.**
A failover test involves simulating a failure in the primary system to ensure that the backup system can seamlessly take over without any service interruption. It helps in verifying the resilience and recovery capabilities of an organization’s infrastructure.

**Option A incorrect.** A vulnerability assessment identifies potential weaknesses in systems but does not test the seamless transition between primary and backup systems.

**Option C is incorrect.** A tabletop exercise is a discussion-based session and does not involve the live testing of systems or processes.

**Option D is incorrect.** A routine backup test ensures that backups can be restored successfully but does not test the immediate switchover capability between systems.

**Question 380.** Sarah, a security administrator, is implementing a monitoring solution for her organization’s server infrastructure. She wants a solution that does not require any additional software to be installed on the servers themselves. Which type of monitoring approach should Sarah choose?

- (A) Agent-based monitoring
- (B) Intrusion Detection System (IDS)
- (C) Agentless monitoring
- (D) Network-based Application Performance Monitoring (APM)

**Explanation 380.** **Correct Answer: C. Agentless monitoring.** Agentless monitoring solutions do not require any software agents to be installed on the servers they monitor. They typically rely on standard protocols and interfaces to collect performance and other data.

Option A incorrect. Agent-based monitoring requires the installation of software agents on each server or device that is to be monitored.

Option B is incorrect. While an Intrusion Detection System (IDS) is a security tool, it is not specifically designed for agentless infrastructure monitoring.

Option D is incorrect. Network-based Application Performance Monitoring (APM) is focused on monitoring application performance on the network, not on agentless server monitoring.

**Question 381.** Alice, a cybersecurity analyst, is tasked with identifying potential weaknesses in a newly deployed web application’s infrastructure before it goes live. She wants a tool that can proactively discover and report on system vulnerabilities, missing patches, and misconfigurations. Which of the following should Alice utilize?

- (A) Intrusion Detection System (IDS)
- (B) Network sniffer
- (C) Vulnerability scanner
- (D) Security Information and Event Management (SIEM) system

**Explanation 381.** **Correct Answer: C. Vulnerability scanner.** Vulnerability scanners are designed to discover and report potential vulnerabilities by probing and analyzing them. They can detect issues such as missing patches, misconfigurations.

Option A is incorrect. An IDS detects and alerts on potential malicious activities based on specific signatures or heuristics but does not proactively scan for vulnerabilities.

Option B is incorrect. A network sniffer captures and analyzes network traffic but does not perform vulnerability assessments on infrastructure components.

Option D is incorrect. While a SIEM system can aggregate and analyze log and event data from various sources, it does not proactively scan for vulnerabilities like a vulnerability scanner

**Question 382.** After conducting a business impact analysis, a local library determined that they could afford several days of downtime without a significant impact on their operations. They want a disaster recovery solution that offers a balance between cost and recovery capabilities. Which site consideration is the most suitable for the library’s needs?

- (A) Mobile site with a full set of IT equipment
- (B) Hot site with daily data replication
- (C) Cold site
- (D) Warm site with weekly backups

**Explanation 382.** **Correct Answer: C. Cold site.** A cold site is an offsite facility that is pre-configured to accept equipment and data backups but doesn’t have any of its own. Given the library’s tolerance for several days of downtime, a cold site would be a cost-effective solution that aligns with their recovery capabilities.
