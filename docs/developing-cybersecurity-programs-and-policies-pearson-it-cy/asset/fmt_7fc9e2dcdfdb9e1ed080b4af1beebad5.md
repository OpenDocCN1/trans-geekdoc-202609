
Cisco also releases bundles of Cisco IOS and IOS XE Software Security Advisories at 1600 GMT on the fourth Wednesday in March and September each year. Additional information can be found on Cisco’s Security Vulnerability Policy at: [https://www.cisco.com/c/en/us/about/security-center/security-vulnerability-policy.html](https://www.cisco.com/c/en/us/about/security-center/security-vulnerability-policy.html).

## Understanding Patch Management

Timely patching of security issues is generally recognized as critical to maintaining the operational CIA of information systems. ***Patch management*** is the process of scheduling, testing, approving, and applying security patches. Vendors who maintain information systems within a company network should be required to adhere to the organizational patch management process.

The patching process can be unpredictable and disruptive. Users should be notified of potential downtime due to patch installation. Whenever possible, patches should be tested prior to enterprise deployment. However, there may be situations where it is prudent to waive testing based on the severity and applicability of the identified vulnerability. If a critical patch cannot be applied in a timely manner, senior management should be notified of the risk to the organization.

Today’s cybersecurity environment and patching dependencies call for substantial improvements in the area of vulnerability coordination. Open source software vulnerabilities like Heartbleed, protocol vulnerabilities like the WPA KRACK attacks, and others highlight coordination challenges among software and hardware providers.

The Industry Consortium for Advancement of Security on the Internet (ICASI) proposed to the FIRST Board of Directors that a Special Interest Group (SIG) be considered on vulnerability disclosure to review and update vulnerability coordination guidelines. Later, the National Telecommunications and Information Association (NTIA) convened a multistakeholder process to investigate cybersecurity vulnerabilities. The NTIA multiparty effort joined the similar effort underway within the FIRST Vulnerability Coordination SIG. Stakeholders created a document that derives multiparty disclosure guidelines and practices from common coordination scenarios and variations. This document can be found at [https://first.org/global/sigs/vulnerability-coordination/multiparty/guidelines-v1.0](https://first.org/global/sigs/vulnerability-coordination/multiparty/guidelines-v1.0).

[Figure 8-6](#ch08.xhtml#ch08fig06) shows the FIRST Vulnerability Coordination stakeholder roles and communication paths.

![](graphics/08fig06.jpg)

The definitions of the different stakeholders used in the FIRST “Guidelines and Practices for Multi-Party Vulnerability Coordination and Disclosure” document are based on the definitions available in ISO/IEC 29147:2014 and used with minimal modification.

NIST Special Publication 800-40 Revision 3, *Guide to Enterprise Patch Management Technologies*, published July 2013, is designed to assist organizations in understanding the basics of enterprise patch management technologies. It explains the importance of patch management and examines the challenges inherent in performing patch management. The publication also provides an overview of enterprise patch management technologies and discusses metrics for measuring the technologies’ effectiveness and for comparing the relative importance of patches.

### In Practice

#### Security Patch Management Policy

**Synopsis:** The timely deployment of security patches will reduce or eliminate the potential for exploitation.

**Policy Statement:**
*   Implementations of security patches are exempt from the organizational change management process as long as they follow the approved patch management process.
*   The Office of Information Security is responsible for maintaining a documented patch management process.
*   The Office of Information Technology is responsible for the deployment of all operating system, application, and device security patches.
*   Security patches will be reviewed and deployed according to applicability of the security vulnerability and/or identified risk associated with the patch or hotfix.
*   Security patches will be tested prior to deployment in the production environment. The CIO and the CTO have authority to waive testing based on the severity and applicability of the identified vulnerability.
*   Vendors who maintain company systems are required to adhere to the company patch management process.
*   If a security patch cannot be successfully applied, the COO must be notified. Notification must detail the risk to the organization.

## Malware Protection

***Malware***, short for “malicious software,” is software (or script or code) designed to disrupt computer operation, gather sensitive information, or gain unauthorized access to computer systems and mobile devices. Malware is operating-system agnostic. Malware can infect systems by being bundled with other programs or self-replicating; however, the vast majority of malware requires user interaction, such as clicking an email attachment or downloading a file from the Internet. It is critical that **s*ecurity awareness*** programs articulate individual responsibility in fighting malware.

Malware has become the tool of choice for cybercriminals, hackers, and hacktivists. It has become easy for attackers to create their own malware by acquiring malware toolkits, such as Zeus, Shadow Brokers leaked exploits, and many more, and then customizing the malware produced by those toolkits to meet their individual needs. Examples are ransomware such as WannaCry, Nyetya, Bad Rabbit, and many others. Many of these toolkits are available for purchase, whereas others are open source, and most have user-friendly interfaces that make it simple for unskilled attackers to create customized, high-capability malware. Unlike most malware several years ago, which tended to be easy to notice, much of today’s malware is specifically designed to quietly and slowly spread to other hosts, gathering information over extended periods of time and eventually leading to exfiltration of sensitive data and other negative impacts. The term ***advanced persistent threats (APTs)*** is generally used to refer to this approach.

NIST Special Publication 800-83, Revision 1, *Guide to Malware Incident Prevention and Handling for Desktops and Laptops*, published in July 2012, provides recommendations for improving an organization’s malware incident prevention measures. It also gives extensive recommendations for enhancing an organization’s existing incident response capability so that it is better prepared to handle malware incidents, particularly widespread ones.

### Are There Different Types of Malware?

Malware categorization is based on infection and propagation characteristics. The categories of malware include viruses, worms, Trojans, bots, ransomware, rootkits, and spyware/adware. ***Hybrid malware*** is code that combines characteristics of multiple categories—for example, combining a virus’s ability to alter program code with a worm’s ability to reside in live memory and to propagate without any action on the part of the user.

A ***virus*** is malicious code that attaches to and becomes part of another program. Generally, viruses are destructive. Almost all viruses attach themselves to executable files. They then execute in tandem with the host file. Viruses spread when the software or document they are attached to is transferred from one computer to another using the network, a disk, file sharing, or infected email attachments.
