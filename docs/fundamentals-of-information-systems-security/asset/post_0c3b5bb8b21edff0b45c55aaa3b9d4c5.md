
intentional downtime in advance. For example, when servers need operating system upgrades or patches, administrators take them offline intentionally so they can perform the necessary work without problems. When administrators schedule intentional downtime, they try to do it so that it has little impact on the rest of the organization. Administrators carefully manage any impact that downtime does have so that it does not disrupt critical business operations. You might be familiar with intentional downtime scenarios such as weekend upgrades of critical software or overnight application of patches to such things as email systems.

Unintentional downtime is usually the result of technical failure, human error, or attack. Technical failure and human error are the most common causes of unintentional downtime. Although downtime caused by malicious attacks is less common, research indicates that it is growing rapidly. Malicious attacks can occur and cause downtime in any of the seven domains of an IT infrastructure. Typically, malicious attacks are targeted on the User, Workstation, LAN, and LAN-to-WAN domains.

**Opportunity cost** is the amount of money a company loses due to downtime. Downtime can be either intentional or unintentional, but either kind directly affects system availability. Some organizations refer to opportunity cost as **true downtime cost**. Opportunity cost usually measures the loss of productivity experienced by an organization due to downtime. For example, suppose a major airline’s reservation servers fail. While the servers are down, no customers can book flights. You can measure the opportunity cost of that downtime in the dollar amount of the unsold tickets. The opportunity cost of unintentional downtime is usually much higher than the opportunity cost of intentional downtime. Opportunity cost is a serious concern for information security professionals. It comprises a large portion of the $1 trillion estimated yearly cost of dealing with cybercrime and malicious attacks.

### NOTE

A data breach policy and procedure will prepare your organization for handling a data breach. This includes communicating to the customers, regulatory bodies, and insurance underwriters. If your organization is under regulatory compliance requirements, you may be subject to legal requirements for data breach notification. Executive management, including legal staff, are typically involved in making specific recommendations regarding a data breach to the organization’s board of directors. Proper handling of a data breach must be done with relevant legal advice.

## Reputation

One of the most important things that information security professionals try to protect is their organization’s reputation and brand image. Companies that suffer from security breaches and malicious attacks that expose any assets are likely to face serious negative consequences in the public eye. For example, a security breach that allows attackers to steal customer credit card data and distribute those data internationally would do significant harm to that company’s reputation and brand image. Even if the company’s response were swift and solved the problem effectively, the negative public perception of the company and its brands could remain for the long term. Among other consequences, this could lead to a decline in the organization’s revenue, net worth, and market capitalization.

## Whom Are You Trying to Catch?

In popular usage and in the media, the term **hacker** often describes someone who breaks into a computer system without authorization. In most cases that means the hacker tries to take control of a remote computer through a network or by software cracking. The media and the general public also use the word *hacker* to describe anyone accused of using technology for terrorism, vandalism, credit card fraud, identity theft, intellectual property theft, or one of many other forms of crime. In the computing community, the term hacker generally describes a person who enjoys exploring and learning how to modify something, particularly related to computer systems. Hackers, for good or bad, are considered to be experts and tinkerers, but because of the way the media negatively portrays the term, hackers are often the subject of some controversy.

This book attempts to address the confusion surrounding this term by categorizing hackers as follows:

- Black-hat hackers—A black-hat hacker tries to break IT security and gain access to systems with no authorization in order to prove technical prowess. Black-hat hackers generally develop and use special software tools to exploit vulnerabilities. Black-hat hackers generally exploit holes in systems, but they generally do not attempt to disclose vulnerabilities they find to the administrators of those systems. They tend to promote the free and open use of computing resources as opposed to the notion of security.

- White-hat hackers—A white-hat hacker, or ethical hacker, is an information systems security professional who has authorization to identify vulnerabilities and perform penetration testing. The difference between white-hat hackers and black-hat hackers is that white-hat hackers will identify weaknesses for the purpose of fixing them, and black-hat hackers find weaknesses just for the fun of it or to exploit them.

- Gray-hat hackers—A gray-hat hacker is a hacker with average abilities who may one day become a black-hat hacker but could also opt to become a white-hat hacker. Another common definition is a hacker who will identify but not exploit discovered vulnerabilities, yet may still expect a reward for not disclosing the vulnerability openly. There is no common definition for this type of hacker.

Hackers are different from crackers. A cracker has a hostile intent, possesses sophisticated skills, and may be interested in financial gain. Crackers represent the greatest threat to networks and information resources. These threats usually involve fraud, theft of data, destruction of data, blockage of access, and other malicious activity. However, the activities of hackers can also cause damage and loss.

### NOTE

Another type of attacker is a script kiddie—a wannabe hacker, a person of any age with little or no skill. This person simply follows directions or uses a “cookbook” approach to carrying out a cyberattack, without fully understanding the meaning of the steps he or she is performing.

## Attack Tools

Protecting an organization’s assets and IT infrastructure requires that you have some idea of how attackers think. Knowing how an attack is conducted and what tools are used will help you build a defense plan. In fact, many organizations use the same tools that attackers use to help identify weaknesses they need to address. It is always better to find weaknesses in your own environment before an attacker does, but it is even more important to quickly remediate that weakness.

Computer criminals and cyberattackers use a number of hardware and software tools to discover exploitable weaknesses and other tools to perform the actual attack. These tools and techniques can include the following:

- Protocol analyzers
- Port scanners
- OS fingerprint scanners
- Vulnerability scanners
- Exploit software
- Wardialers
- Password crackers
- Keystroke loggers

## Protocol Analyzers

A protocol analyzer or packet sniffer (or just sniffer) is a software program that enables a computer to monitor and capture network traffic, whether on a LAN or a wireless network. Attackers can capture and compromise passwords and cleartext data. Protocol analyzers come in both hardware versions and software versions, or a combination of both. Sniffers operate in promiscuous mode, which means that every data packet can be seen and captured by the sniffer. Sniffers decode the frame and IP data packet, allowing you to see data in cleartext if it has not been encrypted.

## Port Scanners

A port scanner is a tool used to scan IP host devices for open ports that have been enabled. Think of a port number as a channel commonly associated with a service. For example, Port 80 is for HTTP web traffic, Port 21 is File Transfer Protocol (FTP), and Port 23 is Telnet, and so on. Request for Comments (RFC) 1700, now superseded by RFC 3232, lists the most common TCP/UDP port numbers and services. (For a complete list of port numbers, refer to the Internet Assigned Numbers Authority [IANA].) Port scanners are used to identify open ports or applications and services that are enabled on the IP host device. This provides attackers with valuable information that can be used in the attack.

## OS Fingerprint Scanners

An operating system (OS) fingerprint scanner is a software program that allows an attacker to send a variety of packets to an IP host device, hoping to determine the target device's operating system (OS) from the responses. Whereas network protocols are generally standard, different operating system vendors are free to implement them as they see fit. The packets sent from the OS fingerprint scanner will recognize differences from the various operating systems used in workstations, servers, and network devices. When an IP host device responds, then the OS fingerprint scanner can guess what operating system is installed on the device. Once an attacker knows what OS and version is installed, the better chance he has to use applicable software vulnerabilities and exploits. A software vulnerability is a bug or weakness in the program. An exploit is something that an attacker can do once a vulnerability is found.

## Vulnerability Scanners

A vulnerability scanner is a software program that is used to identify and, when possible, verify vulnerabilities on an IP host device. From this information, a vulnerability scanner compares known software vulnerabilities in its database with what it has just found. The vulnerability scanner lists all known software vulnerabilities and prioritizes them as critical, major, or minor.
