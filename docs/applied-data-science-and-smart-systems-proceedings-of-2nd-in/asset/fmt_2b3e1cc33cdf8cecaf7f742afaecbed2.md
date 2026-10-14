
The northbound interface allows for communication between higher-level network applications or orchestration systems and the SDN controller. Applications can use it to set network policies, ask the controller for network state information, and request network services. The northbound interface allows application developers to connect programmatically with the network infrastructure by abstracting away the underlying network complexity.

## Security challenges in SDN

Analysis of security attacks will become easier if the objective of that attack is clear. Intention of the attacker is key point for detecting and preventing network system from these attacks. Just like flooding of false messages, shows the intention of attacker to affect the performance of system and also the availability of the resources. Understanding the security issues makes it easier to spot and address these problems. This section is describing the issues and threats of network security in SDN context ([Chica et al., 2020](#ch33.xhtml#ref33_5)).

Data privacy and confidentiality: Massive amounts of sensitive data are handled in SDN setups. This includes user data, financial information, medical information, and intellectual property. It is essential to protect this data’s privacy and confidentiality in order to adhere to legal requirements, keep users’ trust, and stop illicit use or data breaches.

Distributed denial-of-service (DDoS) attacks: DDoS assaults, which can obstruct network activity and impair the performance of vital services, can target SDN. DDoS attacks on SDN infrastructure can be prevented and their effects reduced by being aware of the attack vectors and creating practical mitigation measures.

Malicious control plane manipulation: A prime target for attackers in SDN is the centralized control plane. Unauthorized flow rule updates, network mis- configurations, or unauthorized network access can all result from unauthorized access, manipulation, or compromise of the control plane. Implementing measures to safeguard the control plane from malicious activity is made easier by having a better understanding of the security challenges.

Insider threats and privilege abuse: To combat insider threats, where authorized workers may abuse their credentials to compromise the network infrastructure or get unauthorized access, it is crucial to understand the security difficulties in SDN. Effectively detecting and mitigating insider risks can be achieved by putting in place access controls, monitoring systems, and user behavior analytics.

Compliance and regulatory requirements: Organizations that engage in regulated sectors are required to abide by a number of compliance and legal requirements for network security, data protection, and privacy. In order to ensure compliance with these standards and implement the requisite security controls and auditing methods, it is helpful to understand the security difficulties in SDN.

Trust and adoption: The trust of stakeholders, including end users, organizations, and service providers, is increased when security issues in SDN are addressed. A wider use of SDN technology, more user confidence in the technology, and a faster pace of value realization are all facilitated by improved security measures.

## Purpose and scope of paper

The purpose of this paper on attacks in SDN is to provide a panoramic analysis and synthesis of existing research, literature, and knowledge related to all possible attacks in SDN environments and their impact. This paper’s focus covers a range of topics, including attack paths ([Yoon et al., 2015](#ch33.xhtml#ref33_7); [Chica et al., 2020](#ch33.xhtml#ref33_5); [Rahouti et al., 2022](#ch33.xhtml#ref33_6)), attack types (Abd Elazim et al., 2018; [Iqbal et al., 2019](#ch33.xhtml#ref33_9)), attack vector along with their tools, vulnerabilities ([Lin et al., 2017](#ch33.xhtml#ref33_10); Deb et al., 2020; [Pradhan et al., 2020](#ch33.xhtml#ref33_11)) and the effects of attacks on SDN infrastructure.

The review paper aims to serve the consolidate knowledge about different attacks that pose threats to SDN, classify attacks in terms of attacked plane, techniques, target and impact on SDN environment. This paper will also identify possible vulnerabilities and exploitable weaknesses which can make it susceptible to attacks. [Figure 33.4](#ch33.xhtml#fig33_4) is defining the flow of analysis which aims to explain attacks vectors with their tools and technique to get the knowledge of network limitations. It also highlights the impact and consequences these attacks including disruption of network services and compromised security mechanism.

![Figure 33.4 Flow of analysis](images/fig33_4_C.jpg)

[Figure 33.4 Flow of analysis](#ch33.xhtml#R_fig33_4)

This study intends to provide researchers, practitio- ners, and policymakers with a useful tool for understanding the security environment of SDN, spotting possible threats, and putting in place the necessary defenses. It adds to the body of knowledge by com- piling and analyzing prior studies, highlighting gaps, and offering predictions about the direction of SDN security.

## Taxonomy of attacks in SDN

Attacks are categorized in SDN taxonomy according to their target, effect, method, or position within the SDN architecture. Although the precise taxonomy may change according on the viewpoint and focus of the analysis. In this paper attacks are classified in terms of their targeted plane (Abd Elazim et al., 2018; Iqbal et. al., 2019; [Arya et al., 2021](#ch33.xhtml#ref33_24)). Tables 33.1–33.3 are defining attacks according to their targeted planes i.e., application plane, control plane and data plane, respectively. Tables are also giving a view of affected security aspects with target compo-nent of each plane (as defined in [Figure 33.1](#ch33.xhtml#fig33_1)). Some attacks directly aim to particular component of SDN architecture to get unauthorized access and disrupt the operations. Some attackers focus on maximum impact on network, where as some attackers use pre- defined techniques which are also useful in other net- work also.

Table 33.1 Attacks in application plane 

| Attack  | | Target component | | Affected security aspects |
| --- | --- | --- | --- | --- |
| | | | Confidentiality | Integrity | Availability |
| Intrusion attack | | Network services | ✓ | ✓ | |
| --- | --- | --- | --- | --- | --- |
| Anomaly attack | | Services and application | ✓ | ✓ | |
| Illegal attack | | Programmable control | ✓ | | ✓ |
| Trust model | | Network application | | | ✓ |
| Chained application | | Orchestration and service chaining | | ✓ | ✓ |
| Altering SDN database | | Network application | ✓ | ✓ | |
| Third party application | | Policy enforcement | ✓ | | |
| Misuse of resources | | Services and application | | | ✓ |

Table 33.2 Attacks in control plane 

| Attack  | | Target component | | Affected security aspects |
| --- | --- | --- | --- | --- |
| | | | Confidentiality | Integrity | Availability |
| DOS/DDOS attack | | Controller | | | ✓ |
| --- | --- | --- | --- | --- | --- |
| Intrusion attack | | Northbound API | ✓ | ✓ | |
| Anomaly attack | | Network abstraction | ✓ | ✓ | |
| Threats on distributed multi-controller | | Controller | ✓ | | ✓ |
| Threats from application | | Control application | ✓ | ✓ | |
| Packet in attack | | Northbound API | | | ✓ |
| Side channel attack | | Control protocol | ✓ | | |
| Scanning attack | | Controller | ✓ | | |
| Spoofing attack | | Flow table | ✓ | ✓ | |
| Hijacking attack | | Network state database | ✓ | ✓ | |
| Tampering attack | | Southbound API | | ✓ | |

Table 33.3 Attacks in data plane 

| Attack  | | Target component | | Affected security aspects |
| --- | --- | --- | --- | --- |
| | | | Confidentiality | Integrity | Availability |
| Man in the middle attack | | Forwarding tables | ✓ | ✓ | |

