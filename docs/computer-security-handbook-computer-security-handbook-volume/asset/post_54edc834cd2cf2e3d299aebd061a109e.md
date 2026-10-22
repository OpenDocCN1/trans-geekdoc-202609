
## Employee Productivity.

Providing extranet services is not restricted to business partners and consumers. It is possible to enhance employees’ access to specific internal services and systems by allowing access without requiring a full VPN connection. Email is the universal business tool, and providing Webmail services can allow employees to access email from almost anywhere in the world on any device with an Internet browser. Employees may find it helpful to be able to access and change benefits information from home. This may also be an opportunity to allow access to intranet information through a content management system.

## Outsourced.

Enterprises not possessing the requisite internal human or technological expertise to achieve the organization’s IT goals have long looked to outsourced solutions to meet their needs. Software as a service (SAAS) provides offerings such as productivity applications, collaboration, and email (e.g., Microsoft Office365) and CRM (e.g., salesforce.com). Infrastructure and platform as a service (IAAS and PAAS, respectively) provide on-demand storage and computing (Amazon Web Services—S3/EC2 or Rackspace Open Cloud). Each of these outsourced offerings continues to mature and redefine how enterprises develop, manage, and present their information.

## 32.4.4 Information Assurance Considerations

### 32.4.4.1 Technical Security.

Securing an extranet is not possible at a single layer or point in the network. Each layer is interdependent and requires specific protections to ensure the security of the extranet network.

### 32.4.4.2 Infrastructure.

Since the extranet sits behind a GSD, network layer security measures are normally the protections encountered first.

### Traffic Inspection.

As reiterated in multiple parts of this and other chapters, some security devices have a distinct inability to evaluate encrypted network traffic. Extranets can create additional issues as the encrypted session may travel from the client directly to the extranet server. This potentially requires traffic inspection to occur on the extranet server. Although possible, this method will increase the processing requirements of the server.

Another option is to terminate the SSL connections on an upstream device. This device would then use unencrypted protocols on the downstream side when communicating with the actual extranet server. This method adds an additional layer of complexity when troubleshooting, but it can relieve the extranet server of the encryption and security inspection processing burdens.

### Internal Network Exposure.

Although the compromise of an extranet server is significant, it should not provide unfettered access to internal resources. Although the firewall policy allows access to specific extranet services from the Internet, the firewall policy must also granularly restrict access from the extranet server to internal systems.

### 32.4.4.3 Server.

Server-level protections are the true first line of defense. It is difficult for network-layer security mechanisms to protect a server that is advertising a vulnerable service. System hardening is an approach to reducing the overall risk profile of the server. Nonessential protocols and services are shutdown. The operating system (OS) may have additional parameters such as file and account permissions that further reduce the risk profile. A script can help to ensure these changes occur in a consistent manner. One well-known system-hardening script is Bastille Linux.

Due to the complexities of operating systems and applications, vulnerabilities will occur. The simplest method of remediating vulnerabilities is to update the server with a patch. It is important to test patches for adverse effects before deployment to the production environment. This practice will help to reduce the potential for unexpected results and downtime.

Vendors can take weeks and months to develop and release a patch. In certain cases, third-party patches will become available for unpatched, actively exploited vulnerabilities. Although the ability to use these patches is an option, it is inadvisable due to the inability to verify their integrity and safety.

Even though the goal is to minimize the risk profile of the server through all of these means, it may also be necessary to provide additional server-level protections, including host-based firewall and intrusion-prevention software. These protections have the advantage of being contextually aware of operating systems and application functions, unlike those residing at the network layer.

Virtualization is already a deeply entrenched aspect of internal server infrastructures and on the extranet. Although virtualization provides economies of scale by allowing multiple extranet systems to run on a single server or cluster, there are many security implications. Without clustering, a single point of failure exists if the physical server goes down. Since the virtual switch directs most of the layer 2 traffic generated by the VMs, there is minimal native visibility and security enforcement of the network traffic generated between the VMs. VM-embedded security enforcement is continuing to become more readily available to protect at the hypervisor level. There are also ongoing concerns of escaping virtual sessions and allowing unauthorized access to another virtual session.

### 32.4.4.4 Application.

Some common application layer vulnerabilities include buffer overflows, Structured Query Language (SQL) injection, and cross-site scripting (XSS). Buffer overflows existed decades ago but continue to be a favorite amongst malicious code developers. This condition exists because the application does not do proper bounds checking on input fields, or uses functions that fail to do the same. SQL injection is a malicious attempt to insert an SQL query into server-side requests. By failing to check for and protect against this type of attack, the back-end server may return the information the malicious query requests. XSS is a type of code injection commonly used for phishing. A malicious actor may send an unsuspecting person a link that redirects some or all content elsewhere.

Vulnerabilities at the application layer can easily defeat even the most secure network layer configurations. Applications developed by multibillion-dollar organizations can be just as vulnerable as something developed internally in a small facility. Developers must understand and follow secure coding practices to help minimize the number and severity of application vulnerabilities. See Chapters 38, 39, and 52 in this Handbook for discussions of programming and application security, and Chapters 30 and 31 for Web-based security.

### 32.4.4.5 Policies.

Since extranets provide external entities access to internal information and systems, it is advisable to have a policy that governs the use of these systems. The policy may include information about requirements such as needing a confidentiality agreement before allowing a business partner access to the extranet or mandating the use of TLS/SSL encryption for all extranet communications. Policies do not provide an active protection mechanism but do establish expectations when using extranet systems and consequences of not following those requirements.

## 32.5 CONCLUDING REMARKS.

VPNs and extranets have many powerful features that can enhance an organization’s ability to conduct and improve employee mobility and business functionality. Support and input must come from all levels of the organization to ensure that the secure remote access systems meet the organization’s specific needs and expectations. Most important, these systems must adhere to and enhance, not diminish, the organization’s overall security profile.

## 32.6 FURTHER READING

Stewart, J. Michael. Network Security, Firewalls, and VPNs. Jones & Bartlett Learning, 2010.

Whitman, Michael E., Herbert J. Mattord, and Andrew Green. Guide to Firewalls and VPNs, 3rd ed. Delmar Cengage Learning, 2011.

## 32.7 NOTES

- 1. Tom Kaneshige, “BYOD Planning and Costs: Everything You Need to Know,” CIO, December 13, 2012, www.cio.com/article/723864/BYOD_Planning_and_Costs_Everything_You_Need_to_Know
- 2. Caroline Baldwin, “BYOD Increases Productivity, but IT Departments Need To Be Prepared.” ComputerWeekly, August 2, 2012. www.computerweekly.com/news/2240160757/BYOD-increases-productivity-but-IT-departments-need-to-be-prepared
- 3. Nasim Z. Hosein, “Internet Banking: Understanding Consumer Adoption Rates among Community Banks,” Academic and Business Research Institute Website, January 25, 2010, www.aabri.com/LV2010Manuscripts/LV10038.pdf
- 4. C. Kaufman, P. Hoffman, Y. Nir, and P. Eronen. “Internet Key Exchange Protocol Version 2 (IKEv2): Request for Comments 5996.” Internet Engineering Task Force, September 2010, http://tools.ietf.org/html/rfc5996
- 5. S. Frankel, K. Kent, R. Lewkowski, A. Orebaugh, R. W. Ritchey, and S. R. Sharma, “Guide to IPSEC VPNs: SP 800-77,” NIST Special Publications, December 2005, http://csrc.nist.gov/publications/nistpubs/800-77/sp800-77.pdf
- 6. S. Kelly and S. Frankel, “Using HMAC-SHA-256, HMAC-SHA-384, and HMAC-SHA-512 with IPsec: Request for Comments 4868,” Internet Engineering Task Force Datatracker, May 2007, http://datatracker.ietf.org/doc/rfc4868
- 7. M. Friedl, N. Provos, and W. Simpson, “Diffie-Hellman Group Exchange for the Secure Shell (SSH) Transport Layer Protocol: Request for Comments 4419,” Internet Engineering Task Force, March 2006, http://tools.ietf.org/html/rfc4419
- 8. D. Black and D. McGrew, “Using Authenticated Encryption Algorithms with the Encrypted Payload of the Internet Key Exchange Version 2 (IKEv2) Protocol: Request for Comments 5282,” Internet Engineering Task Force, August 2008, http://tools.ietf.org/html/rfc5282
- 9. Internet Engineering Task Force, “Network Address Translators (NAT)—Description of Working Group,” Internet Engineering Task Force Datatracker, November 2001, http://datatracker.ietf.org/wg/nat/charter
