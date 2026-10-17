
The `Ping of Death`: This attack is like a `Smurf` attack. It occurs when a hacker manipulates an IP protocol by sending large packets with the maximum value allowed in the IP header to a target. When the targeted computing device tries to reassemble these large packets, the packets overload the network resources, causing the buffer to overflow, slowing the network, or crashing the operating system. This causes a denial of service for legitimate packets.^([^(311)](#fn311))

![FIGURE 6.12 The three-way handshake.](images/fig6.12.jpg)

**FIGURE 6.12** The three-way handshake.

![FIGURE 6.13 The SYN flood attack. The three-way handshake is not completed.](images/fig6.13.jpg)

**FIGURE 6.13** The SYN flood attack. The three-way handshake is not completed.

`Distributed denial-of-service (DDoS)` attacks are more advanced. They occur when multiple computing systems coordinate a synchronized attack. A hacker exploits security vulnerability to take control of multiple computers and turns them into botnets or bots (zombie computers). The hacker then uses the bots to attack other computers or networks. The botnets can be made up of a single handful of bots or thousands of them, located around the world. These infected computers are managed through a command-and-control server. DDoS attacks provide an opportunity for hackers to gain access to numerous compromised computing devices. [Figure 6.14](#c6.xhtml#f6.14) demonstrates a typical DDoS attack.

![FIGURE 6.14 A DDoS attack.](images/fig6.14.jpg)

**FIGURE 6.14** A DDoS attack.

In addition to the above DoS attacks that can be utilized by a DDoS as well, the most common DDoS attacks are:

*   The `User Datagram Protocol (UDP) Flood` is like the `ping flood`. The attacker floods the targeted network with UDP packets. Since the UDP protocol is connectionless it does not require any link to be established between the source and destination before data transfer occurs. The goal of this kind of attack is to flood random ports on a remote host with data. Because there is no established connection, the target computer is unable to find an application-sending data and tells the sender that the destination is unreachable. This process consumes host resources, which can ultimately result in denial of services. To defend against UDP floods, firewalls that block malicious UDP packets along with the use of IP routing technology have been used to prevent an attacker from overwhelming a computing system.^([^(312)](#fn312))

*   A `Slowloris attack` occurs when an attacker overwhelms a targeted server by sending numerous HTTP requests until the server cannot make any more connections. The attacker is using a legitimate HTTP request. As a result, the server is forced to keep existing connections open indefinitely. To keep the connections open and alive, the attacker periodically sends partial requests (HTTP headers) to the server saying, “Hey server I’m still here.” Therefore, these unfinished requests exhaust bandwidth and affect the server’s ability to respond to additional traffic requests.^([^(313)](#fn313))

*   `Zero-Day DDoS attacks` or `0-day` is used as a blanket term to refer to all unknown new DDoS attacks that exploit vulnerabilities that have not yet been discovered. Since these types of attacks are not understood, they are exceptionally destructive since the targets have no defense. In other words, a new attack can be called a vector’s zero-days.^([^(314)](#fn314))

![FIGURE 6.15 A normal HTTP request.](images/fig6.15.jpg)

**FIGURE 6.15** A normal HTTP request.

![FIGURE 6.16 A Slowloris attack with unfinished simultaneous HTTP request.](images/fig6.16.jpg)

**FIGURE 6.16** A Slowloris attack with unfinished simultaneous HTTP request.

#### [6.3.2.1 Notable DDoS Attacks](#contents.xhtml#re_h-6-8)

*   The 2020 Amazon Web Services massive DDoS attack. The attack lasted 3 days and peaked at 2.3 terabytes per second.^([^(315)](#fn315))

*   The 2018 DDoS attack on GitHub, a platform for hosting software development. GitHub got hit by1.35 Tb per second traffic at once.^([^(316)](#fn316))

*   In 2016, the Mirai strain of malware infected the Internet of Things (IoT) running on Linux, turning the devices into remotely controlled bots that created DDoS attacks.^([^(317)](#fn317))

*   In 2013, `spamhaus.org`, an anti-spam organization, suffered a DDoS attack with an estimated size of more than 300 Gb per second of attack traffic.^([^(318)](#fn318))

#### [6.3.2.2 DoS Attacking Tools](#contents.xhtml#re_h-6-9)

Some of the most common and free DoS attack tools are the following:

*   `DoSHTTP`, an easy-to-use and powerful DoS tool that generates HTTP flooding

*   `High Orbit Ion Cannon (HOIC)`, intended to attack more than one URL at the same time using HTTP (Hypertext Transfer Protocol)

*   `HTTP Unbearable Load King (HULK)`, a DoS attack tool that generates a unique demand for every request to the Web server

*   `Layer 7 DDoS Simulator (DDOSIM)`, a DoS attacking tool that mimics several zombie hosts with full TCP connections

*   `Low Orbit Ion Cannon (LOIC)`, an open-source network stress testing and DoS attack application

*   `R-U-Dead-Yet`, an HTTP POST DoS attack tool

*   `Tor’s Hammer`, an attacking tool for slow-rate attacks using HTTP POST requests

*   `XOIC`, a DoS attack application for any server with an IP address

### [6.3.3 Malware](#contents.xhtml#re_h-6-10)

Malware is short for “malicious software” and consists of computer viruses, worms, Trojan horses, ransomware, spyware, and other types of destructive software or code. Malware impairs or infiltrates a computing device or system to execute specific damage, without the user’s knowledge. Java Scripts are commonly used for placing malware on a victim’s computing device.^([^(319)](#fn319))

*   `Virus` is a type of malicious code or a program that replicates and spreads from one computer to another after initial execution. A computer virus requires a `host program` and `user action`. Typically, a virus is attached to a computer program, file, or document. For example, a malicious macro infection can be attached to a Word or PDF file. For this code to infect a computing device, the user must run the infected program, and then the executing code can pass the virus to the device.

*   A `Trojan horse` is named after the famous wooden horse that tricked the Trojans and allowed the ancient Greeks to conquer the city of Troy. Trojan horses are scripts or computer programs camouflaged as legitimate software. Instead, they are delivery vehicles for a variety of threats. For example, when a user innocently downloads a utility, game, or movie from a website considered safe and runs it or opens an attachment containing the infected file, the following may occur:

*   A backdoor may open, providing hackers with unauthorized remote access.

*   An exploit occurs that takes advantage of a weakness of the software or hardware.

*   Harmful software is installed, or files are deleted.  

      Some examples of Trojans are the `Zeus` or `Zbot Trojan` malware that hacked the U.S. Department of Transportation;^([^(320)](#fn320))

*   A `ransomware` attack occurs when a hacker uses malicious software, usually malware or phishing spam, to extort victims by locking and encrypting their data until the victim pays a ransom in cryptocurrency. Even after payment the data may not be made available.  

      A ransomware report alert was issued by the CISA, the FBI, and the HHS (U.S. Department of Health and Human Services).^([^(321)](#fn321))

*   Ransomware frequently indicates the end of a lengthy cyberattack chain or cyber kill chain. The attacker has usually spent many days or weeks laying the groundwork for ransomware in the victim’s network.  
