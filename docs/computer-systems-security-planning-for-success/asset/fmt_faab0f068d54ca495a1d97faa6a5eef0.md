
# Malware Distribution by OS (Q1 2020)

The most popular target for malware is the Windows OS by quite a large margin. This is due largely to its popularity as a desktop operating system. The second largest target is web browsers, which afford malware a unique cross-platform reach. The third largest target is the Android mobile operating system, which while technically Linux runs mostly on mobile phones. Both Linux and Mac do not receive as much malware attention. While this may be partially due to the open-source nature of Linux and the BSD kernel used by Macs, it is also partially due to the lack of popularity of each of these operating systems. Malware is often widely distributed, meaning it can target only the most popular/possibly weakest links and still be successful.

## Zero Days

Modern operating systems employ layers of security to ensure that programs do not have access to sensitive information or applications. This typically means that for malware to be effective, it needs to elevate its privileges. The most effective malware can perform privilege escalation without requiring user interaction. To do this malware may rely on new/undocumented exploits or vulnerabilities. These new exploits that have been disclosed for "zero days" are hence are referred to as zero days. Zero days are incredibly powerful and may be hoarded by APTs/criminal groups or sold for millions of dollars on the Dark Web.

## 3.3. Types of Malware

The definition of malware is so broad and new malware is being created daily. This can make it difficult to classify malware. As we go through some basic types, please keep in mind that there is significant overlap. For example, you may encounter ransomware distributed as a virus or ransomware distributed as a trojan. The fact that it is ransomware does not preclude it from being some other type of malware as well.

### 3.3.1. Worms, Viruses, and Trojans

Worms are self-propagating programs that spread without user interaction. Their code is typically stored within an independent object, such as a hidden executable file. Worms often do not severely damage their host, as they are concerned with rapid, exponential spreading.

#### Stuxnet

Stuxnet was a 2010 worm that specifically targeted Iranian nuclear facilities. The worm used an unprecedented four zero-day attacks and was designed to spread via USB flash drives and Remote Procedure Calls (RPCs). In this way it didn’t just rely on networks to propagate. Ultimately Stuxnet’s payload targeted the code used to program PLC devices that control motors and make them spin too fast, destroying the centrifuges. Stuxnet also employed an impressive rootkit to cover its tracks. Given the level of sophistication Stuxnet is believed to have been developed by the US and Israel.

Viruses typically require user interaction, such as copying and infected file from one machine to another, and store their code inside another file on a machine. An executable file may be infected by having the virus code added a separate page that executes before the standard program code. Viruses can be quite damaging to the host as they may take significant resources to spread locally. The term virus is also an unfortunately overloaded one. Due to it’s popularity it is often used by some lower-skill threat actors to refer to many different types of malware.

##### Concept Virus

The Concept virus was the first example of a Microsoft Word macro virus. The virus hid itself inside Microsoft Word files and used Word’s embedded macro language to perform its replication tasks. Viruses were later created for Excel and other programs that had sufficiently sophisticated yet ultimately insecure internal scripting languages.

A trojan is a form of malware that disguises itself as legitimate software. It does not have to rely on a software exploit as much as it exploits users into installing, running, or giving extra privileges to the malicious code. Trojans are the most popular kind of malware as they can be used as an attack vector for many other payloads. The name comes from Greek mythology, where a Trojan horse was disguised as a gift and given to a besieged town. Within the large horse were secret troops who came out in the middle of the night and opened the town gates.

##### Emotet

Emotet is a banking trojan from 2014 that spread through emails. It made use of malicious links or macro-enabled documents to make the user download its code. Emotet has been one of the most costly and destructive pieces of malware currently averaging about one million in incident remediation. It continues to be adapted to avoid detection and make use of even more sophisticated malware.

### 3.3.2. Ransomware

Wana Decrypt0r screenshot is used under fair use

Ransomware is a type of malware that encrypts files and demands a ransom to decrypt them. Modern ransomware uses symmetric encryption to the files quickly and then encrypts the symmetric key asymmetrically using a hard-coded public key for which the threat actor has the corresponding private key. When the ransom is paid, typically via cryptocurrency, the threat actor can decrypt the symmetric key using their private key and the user can use the symmetric key to decrypt the files.

Ransomware is considered a data breach in the data is often exfiltrated as well. It is also worth noting that when the ransom is paid, there is no guarantee that the threat actor will actually begin the decryption process. Typical targets of ransomware include corporate infrastructure and health care systems although ransomware may also be spread indeterminately. The payout of ransoms can be a large money-making enterprise so many APTs or criminal groups may employ its use. Ransomware is considered the biggest threat to cyber stability today.

### 3.3.3. Spyware

Malware specifically designed for espionage/data theft is known as spyware. Like ransomware, spyware can also have a monetary payoff for the threat actor. Actors may use extortion to demand payment or the data will be leaked. This typically means either sold on the dark web or publicly posted. Once again, given the possibility of monetary gain, spyware is often associated with criminal groups. APTs may use spyware as well to obtain secrets of national importance.

Customer data, trade secrets, proprietary data, and government secrets are all targets of spyware. Even outside of governments systems, in the corporate setting, spyware is still a major threat.

#### Fileless Malware

Malware is often detected by scanning storage for files that match a particular hash or by looking in files to see if they contain patterns. Both of these detection techniques rely on the malware being stored in a file. Fileless malware attempts to avoid detection by leaving no footprint in the file system. This type of malware uses legitimate processes to load itself into memory, often with a registry key created to reload every time the machine is restarted. This creates a persistent, hard-to-detect type of malware that is often used by sophisticated threat actors such as APTs and criminal groups.

### 3.3.4. Cryptojacking

Crypto currencies utilizing proof-of-work algorithms have made it easier than ever for programs to convert processor cycles into money. Certain types of malware capitalize on this by mining cryptocurrency in the background on a users machine. This theft of power and resources can result income for the malware distributor when the funds from mining are deposited into their online wallet.

Cryptojacking is more popular than ever, especially considering that large botnets of infected machines have already been created. Cryptojacking creates a simpler path to monetization for malicious actors who may already have control of many compromised machines.

### 3.3.5. Rootkit

A rootkit is a secret program designed to give back door access to a system. They are designed to remain hidden and may even actively disable or circumvent security software. Due to their low-level nature, many rootkits can be difficult to detect and even more difficult to remove.

Rootkits are often classified in accordance with the layer in which they are hidden:

- Firmware Rootkit : Firmware is code that a hardware device uses to run. It is often a thin layer of commands used for setting up and interfacing with the device. A firmware rootkit may reside in the BIOS of a motherboard and can be very difficult to remove.
- Bootloader Rootkit : A bootloader prepares the system to boot an operating system kernel, typically by loading the kernel into memory. A bootloader rootkit may hijack this process to load itself into separate memory space or manipulate the kernel being loaded.
- Kernel-mode Rootkit : Many operating system kernel, including Linux, have the ability to load dynamic modules. These kernel modules have complete access to OS kernel operations. A kernel-mode rootkit can be difficult to detect live as the OS kernel being given the instructions to detect the rootkit can no longer be trusted.
- Application Rootkit : An application or user-mode rootkit is usually installed as an application that runs in the background with administrative privileges. These rootkits are typically the easiest to develop and deploy, a low-level knowledge of the hardware the system is using is not required, but they are also the easiest to detect and remove.

#### Sony Rootkit

In 2005 Sony released CDs for their music software with an application rootkit designed to run on Microsoft Windows systems. The rootkit ran persistently in the background, slowing systems, and did not have an uninstaller to remove the program. It was designed to prevent the OS from copying information from audio CDs, but it also opened up several security holes that could be exploited by other malware. Ultimately the rootkit led to several class-action lawsuits against Sony BMG and a led to a settlement with the Federal Trade Commission that required Sony to reimburse customers who reported damages from the rootkit.

### 3.3.6. Botnet

A botnet is a network of exploited hosts controlled by a single party. These hosts may be desktop computers, servers, or even internet of things (IoT) devices. Botnets are often used in large-scale distributed denial of service (DDoS) attacks where the nature of the attack is to have many machines flooding a single machine with traffic. Botnets may also be used to send spam emails as their access to SMTP email relay may vary depending on their internet service provider (ISP).

Bots are typically controlled through a command and control (C2, C&C) server. While this C2 server may use a custom protocol, it is far more typical for modern botnets to rely on other infrastructure. C2 traffic can use SSH, HTTP, Internet Relay Chat (IRC), or even Discord to send commands to bots and receive data from bots.

### 3.3.7. RAT

RAT stands for Remote Access Trojan an it is used to gain full access and control of a remote target. The malware distributor can browse the files on a computer, send keystrokes and mouse movements, view the screen, and/or monitor the input from the microphone and camera. RATs often actively bypass security controls and as such they may be difficult to detect.

### 3.3.8. Adware / Potentially Unwanted Programs (PUP)

Adware is malware that is designed to track user behavior and deliver unwanted, sometimes intrusive, tailored ads. Adware may slow down a system and/or add ad walls to sites. This type of malware often targets a users web browser.

Potentially Unwanted Programs (PUP) are typically downloaded as part of the install of another program. Commons PUPs are browser toolbars, PDF readers, compression utilities, or browser extensions. These programs may have adware/spyware components in them and can also slow down a system.

## 3.4. Indicators of Compromise

An indicator of compromise (IoC) is an artifact with high confidence the indicates an intrusion. It is a way to tell if a machine has been a victim of malware. IoCs are publicly communicated by security professionals in an effort to help mitigate the effects of malware.

### Common IoC Types

- Hash : A hash of files that are known to be malicious. This can help in identifying trojans and worms.
- IP addresses : Tracking the IP addresses which malware connects to can be used to determine if a machine is infected.
- URLs/Domains : Tracking the URLs or domains that malware uses can also be used to determine if a machine is infected.
- Virus definition/signature : Executables and other files can be scanned for specific sequences of bytes which are unique to a particular virus. In this way even if the malware is hiding within another file, it can still be detected.

## 3.5. Delivery of Malware

Malware is often delivered through social engineering, namely convincing an actor within an organization to download and run or click on something. It can also delivered through infiltrating the software packages something depends on, supply chain, or possibly through a software exploit on an publicly exposed service. Some of the most common ways of spreading malware are detailed below.

### 3.5.1. Phishing

Phishing involves communicating with someone via a fraudulent message in an effort to make them perform and action that will harm them. It is broken into five main categories:

- Spear phishing : Sending phishing emails or other communications that are targeted towards a particular business or environment. These messages may include information about the inner workings of the organization in an attempt to prove their validity. They may also take advantage of a known, insecure practice at a particular organization. Spear phishing is not your standard wide-net phishing attempt, but more of a focused, tailored, custom campaign.
- Whaling : Targeting high-ranking individuals at an organization. Whaling is often used in conjunction with spear phishing.
- Smishing : Using SMS messages when phishing.
- Vishing : Using voice messages when phishing.
- Phishing sites : Threat actors can attempt to gain unauthorized access through information obtained from non-business related communication channel. For example, malicious actors may know that the CEO frequents a popular sailing forum. These actors could set up an account on the sailing forum to direct message the CEO for information.

### 3.5.2. SPAM

SPAM consists of large quantities of unsolicited emails. These emails may be malicious or they may simply be advertising. In either case SPAM accounts for nearly 85% of all email. It is interesting to note that sometimes the malware distributed through SPAM is actually used to send more SPAM through a victim’s machine. The war on SPAM is constantly evolving and while many updates have been made to the way we send email, many improvements have yet to be realized.

### 3.5.3. Dumpster Diving

Information that can ultimately lead to the spread of malware can also be found in improperly disposed trash. Old records or hard drives may contain corporate secrets or credentials that give someone unauthorized access. It is important to properly dispose of sensitive information, making sure that all things that need to be destroyed are destroyed in a complete manner.

### 3.5.4. Shoulder Surfing

PINs, passwords, and other data can also recovered simply by looking over someone’s shoulder. These credentials could be the "in" that an attacker needs to spread malware. Through the aid of optics, such a binoculars, shoulder surfing can even occur at a long distance. Privacy screens, which limit the angle at which you can see a monitor, can be helpful in mitigating this type of attack.

### 3.5.5. Tailgating

Following behind someone who is entering a secure location with a credential is known as tailgating. Often people will even hold secure doors open for someone if they have their hands full. It is human nature to want to help people, but you also must remember that the person behind you may have a USB key with malware ready to deploy as soon as they gain physical access to a machine in the building.

### 3.5.6. Impersonation/Identity Theft

Often as part of a phishing campaign, a threat actor will pretend to be someone else. This may be someone within the organization or someone with sufficient power outside the organization, such as a representative of a government oversight agency. Attackers may also use stolen credentials to make their messages appear official, once again giving them and easy route through which to deploy malware.

## 3.6. Cyber Killchain

One way of analyzing an attack involving malware is through the steps of the Cyber Killchain. The Cyber Killchain was developed by Lockheed Martin and is a military method of analysis that has been adopted by cybersecurity. Cyber Killchain is broken into seven steps: Recon, Weaponization, Delivery, Exploitation, Installation, Command and Control, and Exfiltration.

### 3.6.1. Recon

Recon is short for reconnaissance, military parlance for a preliminary survey used to gain information. During the recon phase, a malicious actor will gather as much information as possible. Methods used in this phase may be passive or active.

Passive recon involves gathering information without sending anything to the target. This typically involves accessing publicly available information, such as social media, published websites, and DNS records. If the actor has access they may also passively sniff network packets.

Active recon involves interaction with the target. This can include port scanning, vulnerability scanning, brute forcing directories and filenames on an HTTP server, or even contacting workers. Active recon can yield more information, but it is also significantly easier to detect.

### 3.6.2. Weaponization

In the weaponization phase the actor begins readying exploits for the vulnerabilities that were assessed during recon. This may include tailoring malware, creating phishing emails, customizing tools, and preparing an environment for the attack. For malware to be effective it must utilize the correct exploits and work under the correct OS and environment. Metasploit is a penetration testing framework that is often used in this step to create custom malware.

### 3.6.3. Delivery

During the delivery phase the malware is handed over to the target. Typically steps are taken to bypass detection systems. Delivery may involve the sending of emails linked to malware or the exploitation of vulnerable servers to then run malware. At the end of this phase, an attacker typically waits for a callback from the malware via the command and control channel.

### 3.6.4. Exploitation

Technically the exploitation step occurs once the malware is successfully executed. In many cases, this involves almost no interaction from the attacker. Once malware is activated or the payload of an exploit executed, the victim has completed the exploitation step.

### 3.6.5. Installation

The installation step is typically performed by the malware once it is running. The malware installs itself, hides itself, and sets up persistence (the ability to restart after being stopped). The malware may escalate privilege or move laterally. It may also install second stage additional payloads from a remote server. A common tactic is injecting downloaded code into an existing process to mask which process is performing questionable actions.

### 3.6.6. Command and Control (C2, C&C)

Malware will reach out via its Command and Control channel for more instructions. At this point an attacker may interact with the malware, giving it additional commands. C2 traffic is usually designed to blend in with existing traffic and not draw attention.

### 3.6.7. Exfiltration / Actions & Objectives

The final step involves getting data from the exploited systems or disabling/misusing the systems in another way. At this point an attacker can use the C2 channel to pull sensitive information from the system, credit card information, password hashes, etc. Its important to not that exfiltration of data may not be the only goal of the attack. An attacker can also disable the system, commit fraud with the system, mine crypto currencies, etc. At this point the malicious actor is in complete control of the exploited system.

## 3.7. Lab: Malware Analysis

The website Any Run offers free interactive malware analysis. We will be using this site to avoid the complications of running malware in a VM.

Start by visiting Any Run and registering for an account with your NJIT email address. Once you have activated your account via email, follow the tutorial to learn how to analyze threats. Use the demo-sample task provided by Any Run. Follow the prompts and watch how the process tree changes. Feel free to take your time, even after the time expires you will still be able to look at the running processes and analyze HTTP Requests, Connections, DNS Requests, and Threats.

For this lab we are going to look at an example of Emotet, a banking Trojan discovered in 2014. On the left-hand side of the Any Run site, click on Public tasks and search for the md5 sum 0e106000b2ef3603477cb460f2fc1751. Choose one of the examples (there are three) and look through the screenshots to get an idea of how the malware is run. It may also help to glance at the network traffic processes.

Run the VM live by clicking Restart in the upper right-hand corner. Perform the actions necessary to trigger the malware, adding time as needed. Finally open notepad on the VM, type in your name, and take a unique screenshot.

Submit a unique screenshot of your VM

Use the Any Run tools to analyze the malware you chose.

Answer the following questions in the text box provided:

- What does this malware do to ensure that it is always running in the background?
- Why is malware often put inside an archive file instead of being distributed as a simple executable?
- What IP addresses does this malware attempt to connect to?
- Does this malware resolve any DNS addresses? How do you know?
- How could you uniquely identify this file as malware (be specific, like specific enough for a malware scanner to find it)?
- What are IoCs and what are the IoCs for this malware?

## 3.8. Review Questions

- Why might an APT choose to use fileless malware as opposed to malware that runs from a file on a machine?
- What is an IoC? Give an example.
- What is phishing? What are the five types of phishing? Give an example of each type.

## 4. Protocols

Protocols can be though of as rules that dictate communication. A protocol may include information about the syntax used, error correction, synchronization, or any other aspect of how communication occurs in the context of that situation. In computer security it is important to have a thorough understanding of common protocols as their weaknesses often determine how and if an attack will occur. Protocols exist for both hardware and software and have been developed via individuals and organizations. Early networking protocols were often developed on mailing lists using Requests for Comments (RFCs). You may still see RFCs being crafted, referred to, or actively worked on. Some of the earliest web protocols are detailed in RFCs. More often than not, large protocols have working groups and associations developing, such as the 802.11 group at the Institute of Electrical and Electronics Engineers (IEEE) which handles WiFi protocols. These groups publish papers detailing how the protocols work.

This chapter will give a brief description of important protocols following the TCP/IP layering model. It is important to note that some of these protocols may reach across layers to accomplish tasks. In this case they will be grouped according to which layer they largely function within.

### 4.1. Network Access Layer

#### 4.1.1. ARP

Address Resolution Protocol (ARP) is used on the local ethernet segment to resolve IP addresses to MAC addresses. Since this protocol functions at the ethernet segment level, security was not a primary concern. Unfortunately this means that ARP communications can be easily spoofed to cause a MitM scenario. A malicious actor simply sends out several ARP packets, gratuitous arp, saying that traffic for a certain IP address should be sent to them. Since the MAC to IP address table is cached in several places, it can take a long time for all the caches to invalidate and resolve an issue caused by malicious ARP frames.

There is a protocol designed to mitigate the issues with ARP. Dynamic ARP Inspection (DAI) reaches across layers to work with the DHCP lease database and drop packets that are not using the MAC address used when a DHCP lease was granted. While this can solve many of the issues associated with ARP it is also a good practice to use secure higher-level protocols such as HTTPS just in case.

#### 4.1.2. Wifi

The Wifi protocols we are most concerned with are the security standards used to encrypt data. By the nature of a wireless protocol, information sent on the network is available to anyone with an antenna. These Wifi security standards are the only thing protecting your network traffic from being viewing by anyone within your transmitting range. There are currently four standards:

- WEP : Wireless Equivalent Privacy (WEP) is depreceated and should not be used. It was developed in 1999 and uses an RC4 stream and 24-bit encryption. Several attacks have been developed that can crack WEP within a matter of seconds.
- WPA : Wifi Protected Access (WPA) utilized Temporal Key Integrity Protocol (TKIP) to change the keys being used. This 128-bit encryption method has also been cracked and the protocol should not be used.
- WPA2 : Wifi Protected Access 2 (WPA2) makes use of AES encryption and is currently the most popular standard. WPA2 is still considered secure.
- WPA3 : Wifi Protected Access 3 (WPA3) was developed in 2018 and is currently considered state-of-the-art. Many networks are beginning the transition from WPA2 to WPA3.

### 4.2. Internet Layer Protocols

#### 4.2.1. IP

IP stands for internet protocol and it was devised to allow creating a network of networks. The network of networks that uses it primarily is the Internet, although you could use IP in other scenarios as well. IP is largely concerned with routing traffic across and to networks. The protocol was first detailed by the IEEE in 1974 and comes from the Advanced Research Projects Agency Network (ARPANET) project, which created the first large, packet-switched network.

Most people are familiar with IP addresses, the unique number given to a host participating in an IP network. Currently there are two main versions of the IP protocol, IPv4 and IPv6, and one of the major differences is in how many IP addresses are available. IPv4 supports 32 bit addresses and IPv6 supports 128 bit addresses. To give an idea of how big of a change that is, we have currently allocated all possible IPv4 addresses, but with IPv6 we could give an address to every grain of sand on the beaches of earth and still not run out.

##### IPv6 Security Implications

From a security standpoint, the way addresses are used in IPv4 vs IPv6 has big consequences. Since there aren’t enough IPv4 addresses a typical internet user is assigned a local address that gets translated to an external IPv4 address when they route their packets through their router. This is referred to as Network Address Translation (NAT) and is usually handled by an all-in-one device that also makes sure external entities cannot connect to the internal network.

With IPv6 addresses each host on that same internal network can be given an external IPv6 address. A basic IPv6 router may simply pass the packets to the network without blocking connections to the internal network. If the machines are not hardened or a firewall is not put in place/enabled the machines could be subject to attack.

As a computer security specialist it is important to test not only IPv4 connectivity, but also IPv6 to ensure that your network is configured appropriately.

#### 4.2.2. ICMP

Internet Control Message Protocol (ICMP) is largely used to send messages between systems when IP doesn’t work. For example, lets say we tried to connect to a host but our router doesn’t know how to get there. Our router can send us an ICMP Destination Unreachable message to let us know that something is going wrong. Because ICMP messages work at the network layer, we will receive this message even if there is an issue with the internet layer.

The most common use for ICMP is the ping command. ping sends an ICMP echo request to check to see if a host is up. By responding to the request with the data included in the request we can assume that the host is up and functioning.

ICMP is also used in the traceroute command. traceroute incrementally increase the Time To Live (TTL) field of ICMP packets and watches for TTL Exceeded messages to determine what route packets are taking to get to a host. Example traceroute output is shown below:

```
traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
```
