
![](img/b2a7c1cdb4938c3b37d6925de0425ae9_407_0.png)

**FIGURE 11-17** Remote SNMP Agent Discovery enables you to discover responsive SNMP agents on the network.

![](img/b2a7c1cdb4938c3b37d6925de0425ae9_407_1.png)

**FIGURE 11-18** Zenmap, a Windows GUI front end for the Nmap port-mapping tool.

**Security Probes:** Nessus or its open source variant, OpenVAS, helps security administrators evaluate a large number of vulnerabilities. It recognizes several common networking, operating system, and application-related security problems. It can report the problems without actually exploiting them. Nessus and OpenVAS collect information available to anyone with access to the network. With a properly configured firewall in place, you can properly implement policies to protect information from unauthorized access. These tools are each a double-edged sword, however. As with many tools, attackers can use them as easily as security professionals can. It is a good idea to include scanning for evidence of Nessus® or OpenVAS reconnaissance of your network.

## Access and Privilege Escalation

Once an attacker profiles and probes a target network for potential vulnerabilities, he or she must access the target system(s). The primary goal of access is to establish the initial connection to a target host (typically a server platform). To conduct additional reconnaissance activities such as covertly installing hacking toolkits, the attacker must then gain administrative rights to the system.

The method of access depends on the connection technology necessary to reach the target network. As many organizations evolve to web-centric business models, they often maintain legacy dialup access infrastructures, either as secondary remote gateways or due to oversight. In some instances, organizations may not even be aware of modem facilities left connected to outside phone lines or private branch exchanges (PBXs). Alternatively, they may not consider the security risks of leaving unattended modem connections, which often compromise existing network perimeter defenses. These connections provide another entry point for malicious code attacks.

## Password Capturing and Cracking

One method of gaining access is to capture or crack passwords. An attacker can install a password logger as a backdoor Trojan on a target machine and monitor specific protocol and program activity associated with remote logon processes. Alternatively, if the attacker captures logon strings remotely, a program such as LophtCrack (www.l0phtcrack.com) can quickly decrypt and compromise administrator and user passwords. In fact, compromising passwords is so attractive that many attackers have become quite resourceful at this task. They have identified existing computer hardware that works well at password cracking. Many newer personal computers have powerful graphics processing units (GPUs) on their video cards. These GPUs are designed to handle the advanced math calculations required for rendering graphic images. Attackers have found that GPUs also work well in cracking passwords. Many new password-cracking tools offload much of the math to video card GPUs to speed up the whole process.

## Maintaining Access Using a Remote Administration Tool

Remote Access Tool (RAT) is a Trojan that, when executed, enables an attacker to remotely control and maintain access to a compromised computer. This is done via one of the following:

- **A server on the victim's machine**—This server listens for incoming connections to the victim. When it receives a connection, it provides remote access for the client that connects. It runs invisibly, with no user interface.

- **A client on the attacker's machine**—This is a GUI front end that the attacker uses to connect to and manage servers on victim machines.

What happens when a server is installed on the victim's machine depends on the capabilities of the Trojan, the interests of the attacker, and whether another attacker, who might have entirely different interests, manages to gain control of the server.

Across all types of devices, including servers, desktop computers, laptops, and mobile devices, infections by remote administration are becoming as frequent as viruses. One common source is through file and printer sharing. Attackers can use file and printer sharing to gain access to a hard drive. The attacker can then place the Trojan in the startup folder. The Trojan will then run the next time a legitimate user logs on. Another common attack method is to simply email the Trojan to the user. The attacker then uses social engineering to convince the user to run the Trojan.

Authors of these programs often claim that they are not intrusion tools. Rather, they are simply remote-control tools or tools to reveal weaknesses in an operating system. Based on past activity, however, it's clear that their real purpose is to gain access to computers for unauthorized use.

## Covering Traces of the Attack

One of the most important phases for an attacker avoiding detection is to remove any traces of an attack. Though the specific actions an attacker takes may differ from one attack to another, the basic steps are the same. Experienced attackers first attempt to remove any files they may have created and restore as many files to their preattack condition as possible. Second, the attacker will likely attempt to remove any log file entries that may provide evidence of the attack. The second step is generally much more difficult than the first step. Most systems use auditing methods that protect log files from modification. That means attackers may have to attack the log files or the auditing system to erase their tracks. Regardless of the effort, cleaning any tracks they left behind greatly increases the likelihood that an attack will go unnoticed. Make sure that you protect your detective security controls as well as other valuable assets. That way, even if you don't stop an attack, you can detect that it happened (or is currently happening).

## Attack Prevention Tools and Techniques

IT security practitioners must understand how to implement effective countermeasures to defend against malicious code attacks. They must also continuously monitor, test, and improve these countermeasures.

Defense in depth is the practice of layering defenses into zones to increase the overall protection level and provide more reaction time to respond to incidents. Defense in depth combines the capabilities of people, operations, and security technologies to establish multiple layers of protection, eliminating single lines of defense and effectively raising the cost of an attack. By treating individual countermeasures as part of an integrated suite of protective measures, you can ensure that you have addressed all vulnerabilities. Managers must strengthen these defenses at critical locations. They must then monitor attacks and react to them quickly.

With respect to malicious code threats, these layers of protection extend to specific critical defensive zones:

- Application defenses
- Operating system defenses
- Network infrastructure defenses

The goals of defense in depth are as follows:

- There should be layers of security and detection, even on single systems.
- Attackers must break through or bypass each layer undetected.
- Other layers can cover a flaw in one layer.
- Overall system security becomes a set of layers within the overall network security.
- Security improves by requiring the attacker to be perfect while ignorant.

## Application Defenses

Software applications provide end users with access to shared data. Some of these data are sensitive or confidential and are not available to all users. Attackers commonly launch attacks on application software to attempt to access or damage sensitive data. You should deploy appropriate controls to secure all application software running on all computers. Some common controls include the following:

- Implementing regular antivirus screening on all host systems
- Ensuring that virus definition files are up to date
- Requiring scanning of all removable media
- Installing firewall and IDS software on hosts as an additional security layer
- Deploying change detection software and integrity checking software and maintaining logs
- Implementing email usage controls and ensuring that email attachments are scanned
- Requiring all users to enable pop-up blockers in their web browsers to stop attackers from displaying pop-up windows and reducing exposure to accidental malware execution
- Establishing a clear policy regarding software installations and upgrades
- Ensuring that only trusted sources are used when obtaining, installing, and upgrading software through digital signatures and other validations

## Operating System Defenses

The operating system serves as an interface between application software and hardware resources. Any attack that compromises the operating system can yield nearly unlimited

## Staying Ahead of the Attackers

Most anti-malware software depends on an up-to-date malware signature database. These most common anti-malware solutions can only detect known exploits. But what happens to attacks based on new exploits that no one knows about? These are called zero-day attacks because the attacks are initially undetectable using malware signature databases. Once an attack is reported, anti-malware software vendors have to update their signature databases and release an update. Then users have to download and install the updated software or database. This time lag gives attackers a window of time to conduct attacks with little resistance.

One way to combat malware, including zero-day attacks, is to use blacklisting or whitelisting. Blacklisting is maintaining a list of all known dangerous sites. Any messages from a site in the blacklist is dropped. The main problem with blacklisting is keeping the blacklist up to date. Also, any site that gets into a blacklist by mistake will have its access dramatically decreased, with multiple would-be customers ignoring connections and network messages. To make matters worse, attackers are very good at changing host or site addresses frequently, requiring constant blacklist updating.

Whitelisting is maintaining a list of trusted sites. All messages and connection requests from sites not in the whitelist are ignored. Whitelisting is safer than blacklisting, but it is more restrictive. Any site that you wish to use must be added to your whitelist before connections are allowed. Both blacklisting and whitelisting can be used as an additional layer of protection to avoid malware attacks.
