
Many email administrators use graylists to deal with spam. A graylist rejects any email sender that is unknown. Mail that is from a legitimate email server is retransmitted after a period of time, and the graylisted email is moved off the graylist and onto the whitelist, at which point it is delivered to the inbox of the receiving account. Email is not necessarily blacklisted or deleted until the user evaluates the decision and makes a human decision to reject or accept the sender.

A related technique is sandboxing. A sandbox is often used when untested code or untrusted programs from third-party sources are being used.

> **ExamAlert**
> 
> For the CISSP exam, you should understand blacklists, graylists, and whitelists.

## Firewalls

The CISSP exam might test you on the advantages and disadvantages of different types of firewalls and their design. A packet filter, which is the most basic form of firewall, operates at the network layer of the OSI model. This type of firewall filters traffic by using an access control list (ACL). The ACL determines what packets can be accepted and what packets should be denied access.

Another type of firewall, a proxy firewall, can be an application-level proxy, a circuit-level proxy, or a kernel-level proxy. A kernel-level proxy is the most advanced and operates at the application layer of the OSI model. A kernel-level proxy firewall works faster than all the application-level firewalls because activity is centered in the kernel. When a packet ingresses a kernel proxy firewall, a new virtual stack is created that has only the protocol proxies needed to examine that specific packet.

Firewalls can be designed in three main ways:

- Single-homed: With a single-homed firewall, one packet-filtering router is installed between the trusted and untrusted networks (which are usually the Internet and the organization's network).

- **Dual-homed**: A dual-homed gateway offers an improvement over a basic packet-filtering router because it comprises a bastion host that has two network interfaces. One important factor with a dual-homed gateway is that IP forwarding is disabled on the host. Additional protection can be provided by adding a packet-filtering router in front of a dual-homed host.

- **Demilitarized (DMZ)**: A DMZ (or screened subnet) is a subnet that is in between firewalls or off one leg of a firewall (see Figure 8.2). Because the DMZ sits in between the public Internet and private networks, it keeps the internal, private network isolated from the external network and provides an area of middle ground where you can host web, mail, and authentication servers.

![](img/cd307d33c10f35ada49ea76811ef60ad_603_0.png)

FIGURE 8.2 Screened Host

### Phone, Fax, and PBX

Three techniques attackers can use to target phone users are phone hijacking, slamming, and cramming. Phone hijacking occurs when hackers use personal information to deceive a phone company's customer service representatives into transferring your phone number to them. Slamming refers to switching users' long-distance phone carriers without their knowledge. Cramming relates to unauthorized phone charges. One cramming technique is to send a fake SMS message that, when clicked on, authorizes the attacker to bill the victim a small amount each month.

Fax machines can present some security problems if they are being used to transmit sensitive information. Fax systems can be secured by using fax servers, encryption, and activity logs.

> **Caution**
> 
> Although fax servers have solved many security problems, they have their own challenges. Many of them use hard drives where organizations store large numbers of commonly used administrative documents and forms. Others allow HTTP and/or FTP access to the print queue, where someone can capture the files. These issues must be addressed before effective security can be achieved.

Private organizations use PBX systems, which permit users to connect to a public switched telephone network (PSTN). A PBX can be used to assign extensions, provide voicemail, and enable special services for internal users and customers. Like other organizational resources, a PBX can be a potential target. If hacked, the PBX can be used to allow callers to call out and make free long-distance phone calls that are charged to the organization. PBX hacking is not as prevalent today as it was in the past, but a PBX can still pose a threat to operational security. Individuals who target PBX and phone systems are known as *phreakers*. *Phreaking* is the art of hacking phone systems. Although this might sound like a rather complicated affair, back in the early 1970s, it was discovered that free phone calls could be made by playing a 2600 Hz tone into a phone. This tone allowed the phreaker to bypass the normal billing process. The first device tailored to this purpose was known as a *blue box*. These boxes were invented in the 1970s and used until the early 1990s.

Although these tools are primarily historical, phreakers can still carry out activities like caller ID spoofing, SIM swapping attacks and they might even target VoIP phone systems for DoS attacks or sniffing attacks.

## Anti-malware

Malware is a problem that computer users are faced with daily. Training users in safe computing practices is a good start, but anti-malware tools are still needed to protect an organization’s computers. When you find suspected malware, there are generally two ways to examine it: using static analysis or active analysis. Whereas static analysis requires you to decompile or disassemble the code, active analysis requires the suspected malware to be executed. Because executing malware on a live production environment can be dangerous, it is typically done on a standalone system or virtual machine referred to as a sandbox. The sandbox allows you to safely view or execute the suspected malware or any untrusted code while keeping it contained.

> **Caution**
> 
> Keep in mind that even when malware is run in a sandbox, there is always some possibility that it may escape and infect other systems.

*Anti-malware* is software that helps you prevent malware from executing on your systems. Anti-malware software should be installed on servers, workstations, and even portable devices. It can use one or more techniques to check files and applications for viruses and other types of common malware. These techniques include the following:

- **Signature scanning**: In a similar fashion to intrusion detection system (IDS) pattern-matching systems, signature scanning looks at the beginning and end of an executable file for known virus signatures. Virus creators attempt to circumvent the signature scanning process by making viruses polymorphic.
- **Heuristic scanning**: Heuristic scanning examines computer files for irregular or unusual instructions. For example, think of your word processing program. It probably creates, opens, and updates text files.
- **Integrity checking**: An integrity checker works by building a database of checksums or hashed values. Periodically, new scans are performed, and the results are compared to the stored results. Although integrity checking is not always effective for data files, this technique is useful for executables because their contents rarely change. For example, the md5sum hashed value of the Linux bootable OS Kali Linux is a66bf35409f4458ee7f35a77891951eb. Any change to the Kali.iso would result in a change in the hashed value, and an integrity checker would easily detect the change.
- Activity blockers: An activity blocker intercepts a virus when it starts to execute and blocks it from infecting other programs or data. Activity blockers are usually designed to start at bootup and continue until the computer shuts down.

### Honeypots and Honeynets

Honeypots and honeynets are much like IDSs in that they are tools for detecting intrusion attempts.

A honeypot is really a tool of deception. Its purpose is to fool an intruder into believing that the honeypot is a vulnerable computer. Honeypots are used for diversion and analysis of an attacker’s tactics, tools, and methods. Honeypots are simply fake systems or networks. Honeypots contain files, services, and databases that have no real value to an organization if compromised but are generally attractive to a hacker. Honeypots are effective because they can appear attractive without putting sensitive information at risk. To be effective, a honeypot must adequately persuade hackers that they have discovered a real system.

Some honeypot vendors sell products that can simulate an entire network, including routers and hosts, that are actually located on a single workstation; these are called honeynets. A honeynet can be deployed so that it is a separate server that is not being used in production.

Real servers can generate tons of traffic, which can make it hard to detect malicious activity. Because nothing is running on a honeypot or honeynet, any activity can easily be detected as a potential intrusion.

Honeypots can be configured for low interaction or high interaction. Low-interaction honeypots simulate only some parts of a service. For example, using a tool like netcat as a low-interaction honeypot, you can set a listener on a common port as shown here:

```
nc -v -n -l -p 80
```
