
![](img/3be1e4f35d99b14a974b22ecf8355b5e_425_0.png)

Figure 3.22 - One example of ring protection in action

The x86 architecture defines four rings (numbered 0 through 3) where more privileged functions, usually limited to kernel functions and some device drivers, are assigned to Ring 0 while less privileged applications are assigned to outer rings. Functions assigned to lower rings can access all other higher rings, but applications assigned to Ring 3 can only access functions outside their own ring through very restricted gates or interfaces.

## Data Hiding

Data hiding maintains activities at different security levels to separate these levels from each other. This assists in preventing data at one security level from being seen by processes operating at other security levels.

## Abstraction

Abstraction involves the removal of characteristics from an entity in order to easily represent its essential properties. For example, it is easier for a system administrator to grant group rights to a group of 25 people called "Human Resources" than to grant 25 individual rights to each HR member. Abstraction negates the need for users to know the particulars of how an object functions. They only need to be familiar with the correct syntax for using an object and the nature of the information that will be presented as a result.

## Cryptographic Protections

Cryptography can be used in a variety of ways to protect sensitive system functions and data. By encrypting sensitive information and limiting the availability of key material, data can be hidden from less privileged parts of the system. For example, secure file systems make heavy use of cryptography to encrypt large amounts of data in storage to prevent it from being disclosed inappropriately. A Trusted Platform Module (TPM) is an example of a specialized cryptoprocessor that provides for the secure generation, use, and storage of cryptographic keys.37 Because each TPM is unique, it may also be used to provide hardware authentication using its keys.

## Host Firewalls and Intrusion Prevention

While firewalls and IPS are normally associated with network partitioning and the enforcement of security zones of control, they are also frequently used to protect individual hosts from attack. Software or hardware-based firewalls can be implemented within individual hosts to control traffic to and from a particular system. Similarly, host intrusion prevention can be used to validate network traffic directed at a host and block it from executing if it is found to be malicious.

## Audit and Monitoring Controls

Secure systems must also have the ability to provide administrators with evidence of their correct operation. This is performed using logging subsystems that allow for important system, security, and application messages to be recorded for analysis. More secure systems will provide considerable protection to ensure that these logs cannot be tampered with, including secure export of such logs to external systems.

Host Intrusion Detection Systems (HIDS) and Network Intrusion Detection Systems (NIDS) may also be considered as types of audit and monitoring controls. HIDS subsystems examine the operation of the system to detect anomalous events and alert security administrators accordingly. They will frequently analyze logs, running processes, and common services/daemons that may come under attack to determine if the system continues to be secure. NIDS performs similar functions but at the network layer.

## Virtualization

Virtualization offers numerous advantages from a security perspective. Virtual machines are typically isolated in a sandbox environment and if infected can quickly be removed or shut down and replaced by another virtual machine. Virtual machines also have limited access to hardware resources and therefore help protect the host system and other virtual machines. Virtual machines do require strong configuration management control and versioning to ensure known good copies are available for restoration if needed. They are also subject to all the typical requirements of hardware-based systems including anti-malware software, encryption, HIDS, firewalls, and patching. Given the existing requirements, plus the required overhead for the VM host, systems with consistent high resource utilization may not benefit through virtualization. Additionally, more malware and viruses are becoming virtual machine aware.38 They are able to detect when they are in a virtual machine and "break out" to the host system. The security architect must be aware of these tradeoffs and plan accordingly for the system and enterprise security architecture.

## Vulnerabilities of Security Architectures

While every system is different, insecure systems tend to suffer from the same sorts of threats and vulnerabilities. Common vulnerabilities include poor memory management, the existence of covert channels, insufficient system redundancy, poor access control, and poor protection for key system components such as hardware resources and core OS functions. Common threats to system availability, integrity, and confidentiality include hardware failure, misuse of system privileges, buffer overflows and other memory attacks, denial of service, reverse engineering, and system hacking.

Because many vulnerabilities result from insecure design and most threats are well known, it is the responsibility of the security architects to ensure that their designs are addressing security requirements appropriately while also ensuring that the system can continue to perform its intended function. A look at the Verizon Data Breach Investigations Report for 2014 will help to frame this conversation for the security architect.39

Web applications were associated with 3,937 security incidents and 490 confirmed data breaches in 2013. Many of the attacks analyzed by Verizon were targeting popular blogging platforms or content management systems from Joomla, Wordpress, and Drupal. In order to address some of these concerns, the security architect would need to have knowledge of blog sites and content management systems being deployed throughout the enterprise. The "shadow IT" phenomenon that allows many IT functions to devolve into the hands of non-IT practitioners has to be of concern to the security architect in this regard. If there are systems being maintained in production environments without the knowledge of the IT function within the enterprise and more importantly without the appropriate controls that the IT function would implement, then these kind of attacks can become a significant threat for the enterprise.

Verizon said human error was at the core of 412 confirmed data breaches in 2013 and associated with more than 16,000 security incidents. Process failures, a lack of communication, and poor controls mitigating business partner risk were associated with many of the incidents. Public sector organizations, administrative, and healthcare firms were the most affected by human error, according to the analysis. The top three errors were mis-delivery of information, publishing mistakes, and disposal errors. Properly implemented and configured data loss prevention technology may be the best way to proactively address employee mistakes. Security architects should implement more efficient processes and set enforceable security policies to control them.

Cyber-espionage activity was associated with 511 security incidents and 306 confirmed data breaches, according to the Verizon report. Basic security best practices are the key to successfully repelling these attacks. Network segmentation, proactive log management, and two-factor authentication could help stop lateral movement if an attacker is already inside and attempting to get to sensitive systems. The security architect should ensure that the foundation of the defense in depth strategy used to secure the enterprise is built on a solid architecture, one that incorporates best practices and accomplishes the basics of a well-defined security architecture first and foremost in order to ensure that as many threats as possible may be mitigated through the use of time proven strategies and techniques.

Point-of-sale (POS) systems suffered 198 data breaches in 2013 according to Verizon. Weak and default passwords on point-of-sale systems were consistently targeted by attackers. BlackPOS, a common memory-scraping malware, was a top technique used by credit card data thieves, Verizon said. Security architects need to lock down their POS systems and should consider application whitelisting and the use of updated antivirus solutions on these systems to counteract these threats.

Lost or stolen devices are consistently ranked as a top concern of IT security pros and chief information security officers. Lost laptops and other devices accounted for more than 9,000 security incidents and 116 confirmed data breaches in 2013 according to the Verizon report. Information assets are lost much more than they are stolen, by a 15-to-1 difference, Verizon said. Security architects need to implement device encryption, encourage users to keep devices with them at all times and implement an effective backup strategy to address these threats.

The abuse of privileges by an employee, contractor, or partner was associated with more than 11,600 security incidents and 112 confirmed data breaches in 2013. Verizon said it is watching a trend of insider espionage targeting internal data and trade secrets. Because most insider attacks happened within the office network, security architects should build additional controls around systems containing sensitive data. They also must review user account activity and quickly disable former employees’ user accounts as part
