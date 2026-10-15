
| Privileged Access Management (PAM) || PAM involves techniques and technologies to manage access privileges and prevent unauthorized permissions to be allocated for accounts, processes, devices, and systems in the infrastructure. PAM helps organizations reduce their attack surface and prevent or contain damage caused by cyberattacks as well as from insider threats. PAM is sometimes referred to as privileged identity management (PIM). |

It is most common to see systems of record (SORs), databases, and other protected/sensitive systems in this zone. This zone is usually air-gapped, meaning it is completely, physically disconnected from the Internet. That is why it is also the most highly valued insider target, and not surprisingly why it has restrictive access policies. It’s worth noting that developers/programmers may sometimes become frustrated with security controls because they can slow their work down, and sometimes people in these roles will find creative ways to bypass the intended security measures. Automation is the best defense in this case. Having a good automated continuous integration and continuous deployment (CI/CD) process that allows for the orchestrated deployment of software between these zones is the best compromise between safety and speed.

#### 3.2.1.4 Overlay

An Overlay network is a specialty network that allows for containerized systems such as Docker® to run. An overlay network can reside within any security zone, but usually, we find these networks either in an intranet or DMZ, or spanned across both, which makes them great targets for an adversary. Overlays are also purely software-defined networks (SDNs) , meaning the network is overlaid across many different systems, effectively creating a network within a network. In a cloud architecture, this is sometimes referred to as a horizontal virtual private cloud (VPC). Kubernetes® is a container orchestration technology that has gained notoriety in this realm because it uses a pluggable network architecture, commonly called the Container Networking Interface (CNI), and works as follows:

1.  The CNI interacts with a compatible CNI (overlay network) implementation.

2.  The provider/implementation is responsible for assigning subnets to the nodes (i.e., the virtual machines, or VMs, that make up the Kubernetes Cluster) and IP addresses for the containers (called Pods) running within the cluster.

3.  The overlay network is a flat network where every pod can communicate with other pods regardless of the node or VM they are running on.

These functions provide for scalability and, given the pluggable CNI, flexibility on the particular implementation, but there are trade-offs. Because they are software defined, overlay network implementations can layover physical networks in either network layer-2 or layer-3 of the TCP/IP stack (layer-4 in the OSI model). TCP/IP layer-2 providers do not allow the capture of TCP-based data because TCP operates at layer-3, but it is easier to configure. Conversely, layer-3 technologies are more complicated, but they do allow for the implementation of more sophisticated overlay network security policies, such as enabling transport layer encryption and TCP-based access policies, which make them a better fit when hosting Internet-facing applications.

### 3.2.2 Zero Trust Networks

Zero trust networks are flat networks, meaning that they do not have a DMZ or intranet. All users, systems, and devices in this type of network follow a no-trust, least-privileged access control model, which means one must establish trust using other identity provider systems every time access is requested. This is a good approach for cloud-based and decentralized network hosting architecture. Unfortunately, this also creates a lot of overhead by having to re-authenticate and validate users with each of these requests, and zero trust networks tend to be expensive and complicated to implement. The most successful implementations are those that start with this model first, rather than trying to alter an existing network architecture. Finally, as automation becomes more prevalent, networks become more software defined and data centers become decentralized and moved to the cloud, we will see this type of architecture become a new standard, so as a security professional it is a good idea for us to at least become familiarized with the concept.

## 3.3 Some Cybersecurity Attacks and Countermeasures

Now that we understand some of the adversarial postures taken and our attack surface, let’s explore some of the attack vectors and countermeasures. Attack vectors are specific ways in which an adversary can compromise an entity, whether that is to gain unauthorized access to steal information, sabotage our infrastructure, or some other sort of malicious activity. Conversely, a countermeasure involves controls used to protect the confidentiality, integrity, and availability (C-I-A) of data and information systems and also are important for negating, deterring, and countering cyberattacks. While the number of attack vectors are increasing exponentially, we will review some of the more common vectors conducted against today’s enterprises and some of the countermeasures used to defend against them.

### 3.3.1 DDoS (Distributed Denial of Service)

DoS/DDoS, as it’s commonly referred to, is a form of attack on the network fabric and the connected systems and devices in the network in order to slow or deny access to the target. DoS is the singular form of the attack, whereas, DDoS is the distributed form. DDoS is the most difficult to address because it requires several different and usually compromised machines and/or processes to perform the attack. DDoS attacks are usually automated in that a series of programmed scripts or bots perform the attack so that it cannot be traced back to the adversary. There are many ways to perform a DDoS attack, but broadly speaking, they fall under three categories: (1) volumetric attacks, (2) protocol attacks, and (3) application layer attacks. Let’s examine these.

#### 3.3.1.1 Volumetric Attacks

Volumetric attacks are those designed to flood the network and networked devices with traffic, with the goal of saturating the bandwidth so much that legitimate users will not be able to access the targeted systems. Also, this attack is known to heat up network appliances and cause hardware failures and in some cases fires. One of the largest known attacks of this type was reported by Akamai in 2020[⁹](#9781284211658_CH03_08.xhtml#c3-bib0009) in which a recorded volume of 2.3 terabytes per second was clocked. To put this into perspective, that is equivalent to streaming over 750 Netflix high-quality movies per hour, only this attack reached peak volume in a matter of minutes instead of hours. The attack was very sophisticated and was intended to overwhelm DDoS mitigating devices.

Configuring firewalls and traditional intrusion detection and prevention devices are not enough because these types of attacks are becoming so automated and robust that we are looking to new solutions emerging from the field research, such as in deep machine learning, semantic technologies, biologically inspired self-healing capabilities, and automated failover systems to combat them. In the meantime, we implement a series of multilayered automated defensive capabilities that are designed to:

*   Detect—abnormal traffic flows or anomalies (e.g., spikes) in traffic.

*   Divert—using modern routing protocols to divert or in some cases deflect the network traffic.

*   Filter—using a separate series of devices put in place to filter out bad traffic from good traffic.

*   Analyze/prevent—using automated analytical tools, artificial immune systems and machine learning (AI/ML) capabilities to analyze the anomalies and make automated adjustments.

