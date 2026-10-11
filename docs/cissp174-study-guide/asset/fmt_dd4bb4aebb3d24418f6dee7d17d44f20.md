
## Inline NIPS Architecture

[Fig. 8.13](#Ch008_361-457_B9780443187346000064_1.xhtml#B-f0070) Inline NIPS architecture.

Note that a NIPS provides defense-in-depth protection in addition to a firewall; it is not typically used as a replacement. Also, a false positive by a NIPS is more damaging than one by a NIDS: legitimate traffic is denied, which may cause production problems. A NIPS usually has a smaller set of rules compared to a NIDS. For this reason, only the most trustworthy rules are used in a NIPS. A NIPS is not a replacement for a NIDS; many networks use both a NIDS and a NIPS.

### HIDS and HIPS

Host-based Intrusion Detection Systems (HIDS) and Host-based Intrusion Prevention Systems (HIPS) are host-based cousins to NIDS and NIPS. They process information within the host. They may process network traffic as it enters the host, but the exam’s focus is usually on files and processes.

A well-known HIDS is Open Source Tripwire®, which was previously just called Tripwire before the company expanded its commercial offerings (see [https://github.com/Tripwire/tripwire-open-source](https://github.com/Tripwire/tripwire-open-source)). Open Source Tripwire® protects system integrity by detecting changes to critical operating system files. Changes are detected through a variety of methods, including comparison of cryptographic hashes.

### Pattern Matching

A Pattern Matching IDS works by comparing events to static signatures. Regarding the previously mentioned Log4Shell vulnerability, Crowdstrike notes “exploitation attempts can be detected by inspecting log files for the characteristic URL pattern `${jndi:ldap://`” [\[7\]](#Ch008_361-457_B9780443187346000064_2.xhtml#bb0040). Based on that information, the following pattern can be used to detect this type of attempted Log4Shell Log4j2 exploitation. If the string `${jndi:ldap://` appears in traffic to the organizations’ web servers: alert.

Pattern Matching works well for detecting known attacks, but usually fares poorly against new attacks.

### Protocol Behavior

A Protocol Behavior IDS models the way protocols should work, often by analyzing RFCs (Request for Comments). RFC 793 (TCP, see [https://datatracker.ietf.org/doc/html/rfc793](https://datatracker.ietf.org/doc/html/rfc793)) describes the TCP flags. A SYN means synchronize, and FIN means finish. One flag is used to create a connection, the other to end one.

Based on analysis of RFC 793, a resulting protocol behavior rule could be “if both SYN/FIN flags set in one packet: alert.” Based on the RFC, it makes no sense for a single segment to attempt to begin and end a connection.

Attackers craft such “broken” segments, so Protocol Behavior does detect malicious traffic. The issue is Hanlon’s Razor, a maxim that reads: “Never attribute to malice that which is adequately explained by stupidity” [\[8\]](#Ch008_361-457_B9780443187346000064_2.xhtml#bb0045). Protocol Behavior also detects “stupid” (broken) traffic: applications designed by developers who do not read or follow RFCs. This is fairly common: the application “works” (traffic flows), but violates the intent of the RFCs.

> **Note**
>
> All Information Security Professionals should understand Hanlon’s Razor. There is plenty of malice in our world: worms, phishing attacks, identity theft, etc. But there is more brokenness and stupidity: most disasters are caused by user error.

### Anomaly Detection

An Anomaly Detection IDS works by establishing a baseline of normal traffic. The Anomaly Detection IDS then ignores that traffic, reporting on traffic that fails to meet the baseline.

Unlike Pattern Matching, Anomaly Detection can detect new attacks. The challenge is establishing a baseline of “normal”: this is often straightforward on small predictable networks, but can be quite difficult (if not impossible) on large complex networks.

## Egress Monitoring

Historically, detection of compromises and adversary activity has focused rather exclusively on attack traffic coming into our more trusted internal networks; Intrusion Detection Systems (IDS) naturally fit this paradigm. Egress monitoring takes the opposite approach and focuses on detection via watching what leaves our networks. Much post-exploitation activity including both command and control (C2) and data exfiltration naturally will necessarily result in traffic patterns that might be discernable via monitoring of traffic egressing our networks. A classic example of egress monitoring for successful adversary detection is identification of a compromised host sending spam by observing traffic destined for TCP port 25 originating from systems other than the expected internal email servers.

## Security Information and Event Management

Intrusion Detection Systems (IDS) have long been the primary technical detective control wielded by organizations. Though the importance of IDS has not waned, organizations now appreciate that many more sources of data beyond the IDS can provide valuable information. These disparate sources of information can provide their own data of value; organizations increasingly see value in being able to more efficiently correlate data from multiple sources.

Security Information and Event Management (SIEM) is the primary tool used to ease the correlation of data across disparate sources. Correlation of security relevant data is the primary utility provided by SIEM. The goal of data correlation is to better understand the context to arrive at a greater understanding of risk within the organization due to activities being noted across various security platforms. While SIEMs typically come with some built-in alerts that look for particular correlated data, custom correlation rules can be created to augment the built-in capabilities.

To be able to successfully gain intelligence through the correlation of data necessarily implies access to multiple data sources. While the threat detection use case of a SIEM can be viable, the collection of data required for correlation can be vast. Due to the volume of data being consolidated in most SIEMs, there are often use cases for SIEM associated with more easily or better demonstrating regulatory compliance.

## User and Entity Behavior Analytics (UEBA)

Compromising legitimate end user systems and accounts represents a common goal of adversaries. Even the most limited user account possesses substantially greater access to our information systems than does the external adversary. While adversaries will employ exploitation, when necessary, a common theme of almost every intrusion includes adversaries abusing legitimate users. Even though detecting exploitation might seem rather difficult, historically this challenge pales in comparison to detecting an adversary wielding legitimate user accounts against our own information systems. User and Entity Behavior Analytics (UEBA) specifically tries to solve the problem of identifying suspicious activity coming from our “trusted” users or systems.

UEBA attempts to discern normal behavior profiles for users and systems within our organization and then proactively alert us to suspicious deviations from the expected patterns of behavior. While conceptually simple, this approach to behavior analysis has proven a difficult challenge over the years. However, with advances in both level of visibility into end user facing systems and security-oriented applications of data science and machine learning, these systems have improved drastically.

## Machine Learning and Artificial Intelligence (AI) Based Tools
