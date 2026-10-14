
*   Tricking the client into thinking the attacker’s system is the server, acting as the middleman as the client sets up a legitimate connection with the server, and then disconnecting the client
*   Accessing a web application using the cookie data of a user who did not properly close the connection

All of these techniques can have disastrous results for the end user and must be addressed with both administrative controls (such as anti-replay authentication techniques) and application controls (such as expiring cookies within a reasonable period of time).

## Summary

Applications developers have a lot to worry about! As hackers become more sophisticated in their tools and techniques, the Application layer is increasingly becoming the focus of their attacks due to its complexity and multiple points of vulnerability.

Malicious code, including viruses, worms, Trojan horses, and logic bombs, exploits vulnerabilities in applications and operating systems or uses social engineering to infect systems and gain access to their resources and confidential information.

Applications themselves also may contain a number of vulnerabilities. Buffer overflow attacks exploit code that lacks proper input validation to affect the contents of a system’s memory. Back doors provide former developers and malicious code authors with the ability to bypass normal security mechanisms. Rootkits provide attackers with an easy way to conduct escalation-of-privilege attacks.

Many applications are moving to the web, creating a new level of exposure and vulnerability. Cross-site scripting attacks allow hackers to trick users into providing sensitive information to unsecure sites. SQL injection attacks allow the bypassing of application controls to directly access and manipulate the underlying database.

Reconnaissance tools provide attackers with automated tools they can use to identify vulnerable systems that may be attacked at a later date. IP probes, port scans, and vulnerability scans are all automated ways to detect weak points in an organization’s security controls. Masquerading attacks use stealth techniques to allow the impersonation of users and systems.

## Exam Essentials

**Understand the propagation techniques used by viruses.** Viruses use four main propagation techniques—file infection, service injection, boot sector infection, and macro infection—to penetrate systems and spread their malicious payloads. You need to understand these techniques to effectively protect systems on your network from malicious code.

**Know how antivirus software packages detect known viruses.** Most antivirus programs use signature-based detection algorithms to look for telltale patterns of known viruses. This makes it essential to periodically update virus definition files in order to maintain protection against newly authored viruses as they emerge. Behavior-based detection is also becoming increasingly common, with antivirus software monitoring target systems for unusual activity and either blocking it or flagging it for investigation, even if the software does not match a known malware signature.

**Explain the techniques that attackers use to compromise password security.** Passwords are the most common access control mechanism in use today, and it is essential that you understand how to protect against attackers who seek to undermine their security. Know how password crackers, dictionary attacks, and social engineering attacks, such as phishing, can be used to defeat password security.

**Be familiar with the various types of application attacks attackers use to exploit poorly written software.** Application attacks are one of the greatest threats to modern computing. Attackers exploit buffer overflows, back doors, time-of-check-to-time-of-use vulnerabilities, and rootkits to gain illegitimate access to a system. Security professionals must have a clear understanding of each of these attacks and associated countermeasures.

**Understand common web application vulnerabilities and countermeasures.** As many applications move to the web, developers and security professionals must understand the new types of attacks that exist in this environment and how to protect against them. The two most common examples are cross-site scripting (XSS) and SQL injection attacks.

**Know the network reconnaissance techniques used by attackers preparing to attack a network.** Before launching an attack, attackers use IP sweeps to search out active hosts on a network. These hosts are then subjected to port scans and other vulnerability probes to locate weak spots that might be attacked in an attempt to compromise the network. You should understand these attacks to help protect your network against them, limiting the amount of information attackers may glean.

## Written Lab

1.  What is the major difference between a virus and a worm?
2.  Explain how an attacker might construct a rainbow table.
3.  What are the actions an antivirus software package might take when it discovers an infected file?
4.  Explain how a data integrity assurance package like Tripwire provides some secondary virus detection capabilities.

## Review Questions

1.  What is the most commonly used technique to protect against virus attacks?
    1.  Signature detection
    2.  Heuristic detection
    3.  Data integrity assurance
    4.  Automated reconstruction

2.  You are the security administrator for an e-commerce company and are placing a new web server into production. What network zone should you use?
    1.  Internet
    2.  DMZ
    3.  Intranet
    4.  Sandbox

3.  Which one of the following types of attacks relies on the difference between the timing of two events?
    1.  Smurf
    2.  TOCTOU
    3.  Land
    4.  Fraggle

4.  Which one of the following techniques is most closely associated with APT attacks?
    1.  Zero-day exploit
    2.  Social engineering
    3.  Trojan horse
    4.  SQL injection

5.  What advanced virus technique modifies the malicious code of a virus on each system it infects?
    1.  Polymorphism
    2.  Stealth
    3.  Encryption
    4.  Multipartitism

6.  Which one of the following tools provides a solution to the problem of users forgetting complex passwords?
    1.  LastPass
    2.  Crack
    3.  Shadow password files
    4.  Tripwire

7.  What type of application vulnerability most directly allows an attacker to modify the contents of a system’s memory?
    1.  Rootkit
    2.  Back door
    3.  TOC/TOU
    4.  Buffer overflow

8.  Which one of the following passwords is least likely to be compromised during a dictionary attack?
    1.  mike
    2.  elppa
    3.  dayorange
    4.  fsas3alG

9.  What technique may be used to limit the effectiveness of rainbow table attacks?
    1.  Hashing
    2.  Salting
    3.  Digital signatures
    4.  Transport encryption

10.  What character should always be treated carefully when encountered as user input on a web form?
     1.  !
     2.  &
     3.  \*
     4.  '

11.  What database technology, if implemented for web forms, can limit the potential for SQL injection attacks?
     1.  Triggers
     2.  Stored procedures
     3.  Column encryption
     4.  Concurrency control

12.  What type of reconnaissance attack provides attackers with useful information about the services running on a system?
     1.  Session hijacking
     2.  Port scan
     3.  Dumpster diving
     4.  IP sweep

13.  What condition is necessary on a web page for it to be used in a cross-site scripting attack?
     1.  Reflected input
     2.  Database-driven content
     3.  .NET technology
     4.  CGI scripts

14.  What type of virus utilizes more than one propagation technique to maximize the number of penetrated systems?
     1.  Stealth virus
     2.  Companion virus
     3.  Polymorphic virus
     4.  Multipartite virus

15.  What is the most effective defense against cross-site scripting attacks?
