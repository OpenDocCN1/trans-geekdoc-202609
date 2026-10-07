
# CCSP Certified Cloud Security Professional All-in-One Exam Guide
202

iSCSI offers a lot of features that are ideal for a cloud environment and security; iSCSI traffic is recommended to be run over its own segregated networks for security reasons and protection of data privacy. However, iSCSI supports encrypted communications through protocols as IPsec, and encryption should be used wherever possible to protect communications between virtual machines and storage networks. iSCSI also supports a variety of authentication protocols, such as Kerberos and CHAP, for securing communications and confidentiality within networks.

> NOTE It is important to remember that iSCSI must be protected with technologies as those mentioned in this section, as iSCSI itself is not encrypted and must be protected through other means.

![](img/44bc0d6508f04646c7c3b07267095e71_222_0.png)

# Installation and Configuration of Virtualization Management Tools

With a cloud environment entirely dependent on virtualization, the proper installation and configuration of the management tools that control the virtualized environment form one of the key components of cloud data center security. Without proper controls in place with hypervisors and the management plane, the entire environment may be insecure and vulnerable to a wide array of attacks. With a compromise or attack at virtualization management tools, the underlying data center infrastructure, and thus hosts that reside within it, is vulnerable to threats and compromises.

With a variety of different virtualization platforms and software, each vendor will have their own utilities and guidelines for how best to secure their implementations. Overall, the vendor responsible for the virtualization software will know the best practices for securing their configurations. For a cloud provider, working as a partner with the virtualization vendor will promote the best understanding of security requirements. If possible, working with a vendor from the early planning stages will allow the cloud provider to secure their data center infrastructure in a way to meet the security requirements of the virtualization platform, and specific requirements for security ultimately have a significant influence on which virtualization platform is chosen by the cloud provider.

The process of securing the virtualization infrastructure will typically involve many different aspects of the data center and operations. The most obvious starting point involves the configuration and security options available within the virtualization platform itself. This involves role-based access, secure communication methods and APIs, and logging and monitoring of events and actions by privileged users within the software. However, outside of the actual configuration of the virtualization platform, using physical or logical methods of keeping the hyper and management plane isolated and separate from user traffic, and certainly from external network traffic, is also imperative for maintaining a secure environment.

# Chapter 6: Operations

With vendor-supplied software and tools to secure the virtualized environment's management tools, it is imperative for the Cloud Security Professional to ensure that these are updated and patched regularly. This will include regular patching cycles that most vendors use, as well as ensuring that a cloud service provider has a documented and tested procedure for rolling out patches with urgency when required by the type of exploit discovered. It is important to design systems with sufficient redundancy to enable patching processes to occur without overall downtime to the application. Without this redundancy in design, there will likely be considerable tension between the application teams and the systems or security teams in regard to patching urgency and patching schedules.

![](img/44bc0d6508f04646c7c3b07267095e71_223_0.png)

The main principles applied to the security of any system also apply to the security of the virtualization management tools. The combination of security protocols between the actual management devices with the use of network segregation and isolation is called defense in depth. By using role-based authentication and severely limiting the number of personnel who have access to the hypervisors and management plane, a strong access control prevents promotion within the system. As with any system, even with strong segregation and access control, active and thorough logging and monitoring are essential to ensuring that only the appropriate type of access and the appropriate system resources are being used by administrative personnel.

# Run the Physical Infrastructure for the Cloud Environment

Running the physical infrastructure of a cloud environment involves the access control systems, the networking configurations, the availability of systems and resources, and the hardening of operating systems by baselines and compliance.

# Configuration of Access Control for Local Access

Although a cloud data center may be based at the user level on virtual machines, which is where access control is typically focused, the same issues apply to access control for the underlying infrastructure and the components that form it. With a traditional data center, physical access to servers and hardware should be limited in a cloud data center as well. This includes personnel access to data centers where the hardware is housed, but also to local access through terminals to hardware components. The two main considerations from a security perspective for local access are physical access through KVM (keyboard, video, mouse) and console access through the hypervisor. Regardless of which type of local access is used, multifactor authentication should be employed whenever possible, and comprehensive logging and auditing programs should be in place as well, conforming to best practices for systems and security protection.

203

# CCSP Certified Cloud Security Professional All-in-One Exam Guide
204

With use of KVM for access, several best practices should be followed to ensure security protections. Much like with storage devices, KVM connectivity should be isolated on its own specific physical channels to prevent the leaking or exposure of communications packets. The KVM should have physical protections to prevent updating or compromise of firmware, as well as a physical housing that is tamperproof. The housing should have both alarms and notifications in place if the physical panel is opened or compromised, or if any cabling is being installed or tampered with, to prevent the possibility of installing components to steal credentials or gain access. The KVM should be configured to allow access to one host at a time and not allow any transfer of data between hosts through the KVM. Also, the KVM should be configured to not allow any USB devices to be connected to it and used, with the exception of any input devices such as a mouse or keyboard; no USB devices that allow storage or data transfers should be permitted access.

Console access to virtual machines is something that all hypervisor implementations offer, and it is crucial for administrators to be able to properly maintain their machines, especially in the event of a crash or for use in troubleshooting startup and shutdown problems. Console access, much like access through the management plane or administrative attacker, must be protected and highly restricted because it gives a potential attacker enough insight into and control over a virtual machine. Because console access is an integral part of the implementation from the hypervisor vendor, it typically allows for strong access control mechanisms as well as logging and auditing. All of these should be implemented and regularly audited to ensure appropriate use and regulatory compliance of the environment and administrative/privileged user access.

# Securing Network Configuration

The network is vital for overall system and data center security, and four main technologies are used for its security, as detailed next.

# VLANs

Within a cloud data center, the concept of network isolation and segregation is very important to ensure optimal security. Because physical network isolation is not possible within a cloud data center regard to virtual machines, the use of VLANs is essential. At the very least, all management and administrative networks should be completely isolated and segregated from other traffic. The same rule applies to networks and iSCSI traffic.

With regard to the actual machines, the same type of segregation in a traditional data center, where physical networks should be replicated with the use of VLANs. This includes the isolation of production and nonproduction systems, as well as the separation and isolation of application tiers—specifically the presentation, application, and data tiers or zones. With the proper configuration of machines grouped in a VLAN, they will only see the other servers in the same VLAN, so communication outside the VLAN can be more easily and greatly restricted, while allowing internal server-to-server communications.
