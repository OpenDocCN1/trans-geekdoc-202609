
* The Office of Information Security is responsible for managing an annual user account audit of network accounts, local application accounts, and web application accounts.
* Data classification, regulatory requirements, the impact of unauthorized access, and the likelihood of a threat being exercised must all be considered when deciding upon the level of authentication required. The Office of Information Security will make this determination in conjunction with the information system owner.
* Operating systems and applications will at a minimum be configured to require single-factor complex password authentication:
* The inability to technically enforce this standard does not negate the requirement.
* Password length, complexity, and expiration will be defined in the company password standard.
* The password standard will be published, distributed, and included in the acceptable use agreement.
* Web applications that transmit, store, or process “protected” or “confidential” information must at a minimum be configured to require single-factor complex password authentication:
* The inability to technically enforce this standard does not negate the requirement.
* Password length, complexity, and expiration will be defined in the company password standard.
* If available, multifactor authentication must be implemented.
* Passwords and PINs must be unique to the application.
* Exceptions to this policy must be approved by the Office of Information Security.
* All passwords must be encrypted during transmission and storage. Applications that do not conform to this requirement may not be used.
* Any mechanism used for storing passwords must be approved by the Office of Information Security.
* If any authentication mechanism has been compromised or is suspected of being compromised, users must immediately contact the Office of Information Security and follow the instructions given.

### Infrastructure Access Controls
A ***network infrastructure*** is defined as an interconnected group of hosts and devices. The infrastructure can be confined to one location or, as often is the case, widely distributed, including branch locations and home offices. Access to the infrastructure enables the use of its resources. ***Infrastructure access controls*** include physical and logical network design, border devices, communication mechanisms, and host security settings. Because no system is foolproof, access must be continually monitored; if suspicious activity is detected, a response must be initiated.

#### Why Segment a Network?
***Network segmentation*** is the process of logically grouping network assets, resources, and applications. Segmentation provides the flexibility to implement a variety of services, authentication requirements, and security controls. Working from the inside out, network segments include the following types:
* **Enclave network:** A segment of an internal network that requires a higher degree of protection. Internal accessibility is further restricted through the use of firewalls, VPNs, VLANs, and network access control (NAC) devices.
* **Trusted network (wired or wireless):** The internal network that is accessible to authorized users. External accessibility is restricted through the use of firewalls, VPNs, and IDS/IPS devices. Internal accessibility may be restricted through the use of VLANs and NAC devices.
* **Semi-trusted network, perimeter network, or DMZ:** A network that is designed to be Internet accessible. Hosts such as web servers and email gateways are generally located in the DMZ. Internal and external accessibility is restricted through the use of firewalls, VPNs, and IDS/IPS devices.
* **Guest network (wired or wireless):** A network that is specifically designed for use by visitors to connect to the Internet. There is no access from the Guest network to the internal trusted network.
* **Untrusted network:** A network outside your security controls. The Internet is an untrusted network.

[Figure 9-2](#ch09.xhtml#ch09fig02) shows the topology of a network that has not been properly segmented.

![](graphics/09fig02.jpg)

The network topology in [Figure 9-2](#ch09.xhtml#ch09fig02) shows an enterprise that has a call center, a branch office, a warehouse, and a data center. The branch is a retail office where customers purchase their goods and the enterprise accepts credit cards. Users in the call center and the warehouse have access to the resources in the Branch office and vice versa. They also have access to resources in the data center. If any device is compromised, an attacker can pivot (or move laterally) in the network.

The topology in [Figure 9-3](#ch09.xhtml#ch09fig03) shows the same enterprise network topology, except that firewalls were installed to segment the network and to allow the traffic from the credit card readers to communicate only with specific servers in the data center.

![](graphics/09fig03.jpg)

Several other technologies can be used to segment a network:
* Virtual LANs (VLANs)
* Security Group Tagging (SGT)
* VPN Routing and Forwarding (VRF)
* vMicro-segmentation at the virtual machine level
* Micro-segmentation for containers

**In Practice**

**Network Segmentation Policy**

**Synopsis:** Directive to logically group network assets, resources, and applications for the purpose of applying security controls.

**Policy Statement:**
* The network infrastructure will be segregated into distinct segments according to security requirements and service function.
* The Office of Information Security and the Office of Information Technology are jointly responsible for conducting annual network segment risk assessments. The results of the assessments will be provided to the Chief Operating Officer (COO).
* Complete documentation of the network topology and architecture will be maintained by the Office of Information Technology, including an up-to-date network diagram showing all internal (wired and wireless) connections, external connections, and end points, including the Internet.

#### What Is Layered Border Security?
***Layered security*** is the term applied to having different types of security measures designed to work in tandem with a single focus. The focus of ***layered border security*** is protecting the internal network from external threats. Layered border security access controls include firewall devices, intrusion detection systems (IDSs), and intrusion prevention systems (IPSs). To be effective, these devices must be properly configured and expertly managed. Due to the complexity of and resource requirements associated with maintaining and monitoring border security devices, many organizations have chosen to outsource the function to ***managed security service providers*** (referred to as MSSPs). Oversight of in-house administration or of the MSSP is a critical risk management safeguard.

##### So, What Are Firewalls?
***Firewalls*** are devices or software that control the flow of traffic between networks. They are responsible for examining network entry and exit requests and enforcing organizational policy. Firewalls are a mandatory security control for any network connected to an untrusted network such as the Internet. Without a properly configured firewall, a network is completely exposed and could potentially be compromised within minutes, if not seconds. A firewall policy defines how the firewall should handle inbound and outbound network traffic for specific IP addresses and address ranges, protocols, ports, applications, and content types. The policy is codified in the rule set. The rule set is used by the firewall to evaluate ***ingress*** (incoming) and ***egress*** (outgoing) network traffic. In keeping with access control best practices, rule sets should be initially set to default deny (deny all) and then strict rules implemented that allow connectivity based on business need.
