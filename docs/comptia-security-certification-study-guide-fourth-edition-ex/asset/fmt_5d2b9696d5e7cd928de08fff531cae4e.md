
![Image](boxx.jpg) **A, C,** and **D** are incorrect. Ping is a TCP/IP utility that tests connectivity to a remote system. Dig is an example of a DNS profiling tool that queries DNS looking for DNS data. Although answer D uses `nmap`, it is looking for the wrong port—port 3389 is the Remote Desktop port and not SQL Server.

[**10.**](#ch20.xhtml#rch20que10) ![Image](boxt.jpg) **B.** An unknown environment test, formerly known as a black box test, involves not giving the tester any details about the network setup, such as computer names, IP addresses, and services running.

![Image](boxx.jpg) **A, C,** and **D** are incorrect. A known environment test, formerly known as a white box test, involves giving the security tester all of the details as to the setup of the environment. A partially known environment test, formerly known as a gray box test, involves giving the tester a small amount of detail, such as the IP address used by the company. There is no such thing as an Internet environment test.

[**11.**](#ch20.xhtml#rch20que11) ![Image](boxt.jpg) **C.** Kali Linux is a penetration testing toolset that has a number of hacking tools preinstalled, ready for use.

![Image](boxx.jpg) **A, B,** and **D** are incorrect. LANguard, Nessus, and `nmap` are not penetration testing tools—they are considered scanners. LANguard and Nessus are vulnerability scanners, while `nmap` is a pinger/port scanner.

##### Tools Used to Assess Security

[**12.**](#ch20.xhtml#rch20que12) ![Image](boxt.jpg) **D.** It is critical that the honeypot has auditing and logging enabled so that you can record all the hacker's activity. It is a best practice to ensure that the logs are stored in a secure location so that the hacker cannot delete or erase entries from the logs.

![Image](boxx.jpg) **A, B,** and **C** are incorrect. You should not take steps to make the honeypot less secure than a normal system would be because the hacker will suspect it is a honeypot. This means you would not have a blank password or open additional ports. You would also not configure a Trojan virus, as a regular system would not have a Trojan virus installed (unless the hacker planted it there).

[**13.**](#ch20.xhtml#rch20que13) ![Image](boxt.jpg) **A.** You will use a password cracker such as John the Ripper to crack passwords.

![Image](boxx.jpg) **B, C,** and **D** are incorrect. `Nmap` (network mapper) is a port scanner that identifies ports open on a system. LANguard and Nessus are examples of vulnerability scanners.

[**14.**](#ch20.xhtml#rch20que14) ![Image](boxt.jpg) **D.** A passive tool does not create activity on a system. The only example of a tool that does not create activity on a system in the list of choices is a network sniffer.

![Image](boxx.jpg) **A, B,** and **C** are incorrect. John the Ripper is a password attack tool, whereas `nmap` is a port scanner and Metasploit is a tool used to actively exploit a system. All of these create activity on a system so they are considered active tools.

[**15.**](#ch20.xhtml#rch20que15) ![Image](boxt.jpg) **A.** John the Ripper is used to perform password attacks when you're doing a penetration test or assessing password complexity.

![Image](boxx.jpg) **B, C,** and **D** are incorrect. Dig and nslookup are DNS profiling tools, whereas `nmap` is a port scanner.

[**16.**](#ch20.xhtml#rch20que16) ![Image](boxt.jpg) **D.** A honeynet is a group of systems used to create a fake network to lure the attacker to that network. The goal is to keep the hacker busy on the honeynet while you log all activity and buy yourself some time to detect the hacker and prevent them from compromising production systems.

![Image](boxx.jpg) **A, B,** and **C** are incorrect. A honeypot is one system that is set up to attract a hacker and to have the hacker trigger alarms to notify the administrator of the hacker's presence. You typically will place a honeypot in the DMZ (not your LAN), but the DMZ is not the honeypot or honeynet itself.

##### Performance-Based Question

[**17.**](#ch20.xhtml#rch20que17) The following illustration displays the correct answer. Note that on the real exam you will find similar questions that expect you to drag the box from one side to the other.

![Image](f0824-01.jpg)

## Chapter 21

## Incident Response and Computer Forensics

### CERTIFICATION OBJECTIVES

- [21.01 Working with Evidence](#ch21.xhtml#ch21obj01)
- [21.02 Collecting Digital Evidence](#ch21.xhtml#ch21obj02)
- [21.03 Looking at Incident Response](#ch21.xhtml#ch21obj03)
- [✓ Two-Minute Drill](#ch21.xhtml#ch21lev1sec5)
- [**Q&A** Self Test](#ch21.xhtml#ch21lev1sec6)

A popular topic that relates to computer security is computer forensics and investigations. *Computer forensics* deals with the capture and analysis of evidence from computers, servers, or mobile devices. This chapter introduces you to computer forensics and helps you prepare for the related questions on the Security+ exam. This chapter is by no means intended to be a complete discussion of computer forensics, because it would take an entire book to expose you to the concepts and skills needed to be a computer forensics investigator.

The two major categories of forensics investigations are corporate investigations (internal) and public investigations. A *corporate investigation* arises because an employee is suspected of violating a corporate policy or misusing a corporate asset such as e-mail or the Internet. A *public investigation* arises due to suspicion that a law has been broken. In both cases, it is important to seek legal advice before starting your investigation to ensure that you follow proper procedures for obtaining evidence so that it will be admissible in court should the case go to trial.

Your job as a computer forensics investigator is to ensure that you collect the digital evidence needed to prove or disprove that someone has broken a law or that an employee has violated corporate policy.

### CERTIFICATION OBJECTIVE 21.01

### Working with Evidence

It is critical that you understand not only how to acquire and analyze digital evidence when performing a computer investigation but also the different types of evidence and how evidence is managed. This section introduces you to what evidence is.

#### Admissibility

For evidence to be admissible in court, it must meet three conditions—it must be *sufficient* evidence, it must be *competent* evidence, and it must be *relevant* evidence. For evidence to be considered sufficient, it must prove a fact by itself, without the need for supporting evidence to prove the point. The evidence must also be competent evidence, which means that the evidence must have been legally obtained. If the evidence has been illegally obtained, it is inadmissible in court. Finally, the evidence must have relevance—meaning that the evidence must be related to and have meaning to the case.

#### Types of Evidence

When working on collecting evidence, you need to understand the different types of evidence presented in court. The major types of evidence are real evidence, direct evidence, documentary evidence, and demonstrative evidence.

*Real evidence,* also known as *physical evidence,* is a tangible object presented in court. An example of real evidence in a murder trial such as a stabbing would be the actual murder weapon (the knife).

*Direct evidence* is testimony from a witness who has seen or experienced the event firsthand. For example, if someone saw the murder and tells how it happened, that is direct evidence.

The next type of evidence is *documentary evidence,* which is typically a printed document. Examples of documentary evidence are contracts, an invoice for some form of service or product, and a printed e-mail supporting something communicated through electronic mail. Documentary evidence could also be evidence such as voice recordings, video recordings, or photographs.
