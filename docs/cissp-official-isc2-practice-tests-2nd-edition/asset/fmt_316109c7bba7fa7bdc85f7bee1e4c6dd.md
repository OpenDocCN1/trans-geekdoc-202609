
# 96. Susan is troubleshooting Kerberos authentication problems...

Susan is troubleshooting Kerberos authentication problems with symptoms including TGTs that are not accepted as valid and an inability to receive new tickets. If the system she is troubleshooting is properly configured for Kerberos authentication, her username and password are correct, and her network connection is functioning, what is the most likely issue?

1.  The Kerberos server is offline.
2.  There is a protocol mismatch.
3.  The client’s TGTs have been marked as compromised and de-authorized.
4.  The Kerberos server and the local client’s time clocks are not synchronized.

# 97. Kerberos, KryptoKnight, and SESAME are all examples of what type of system?

1.  SSO
2.  PKI
3.  CMS
4.  Directory

# 98. Which of the following access control categories would not include a door lock?

1.  Physical
2.  Directive
3.  Preventative
4.  Deterrent

# 99. What authentication protocol does Windows use by default for Active Directory systems?

1.  RADIUS
2.  Kerberos
3.  OAuth
4.  TACACS+

# 100. Alex configures his LDAP server to provide services on 636 and 3269...

Alex configures his LDAP server to provide services on 636 and 3269. What type of LDAP services has he configured based on LDAP’s default ports?

1.  Unsecure LDAP and unsecure global directory
2.  Unsecure LDAP and secure global directory
3.  Secure LDAP and secure global directory
4.  Secure LDAP and unsecure global directory

# Chapter 6: Security Assessment and Testing (Domain 6)

## 1. During a port scan, Susan discovers a system running services...

During a port scan, Susan discovers a system running services on TCP and UDP 137-139 and TCP 445, as well as TCP 1433. What type of system is she likely to find if she connects to the machine?

1.  A Linux email server
2.  A Windows SQL server
3.  A Linux file server
4.  A Windows workstation

## 2. Which of the following is a method used to design new software tests...

Which of the following is a method used to design new software tests and to ensure the quality of tests?

1.  Code auditing
2.  Static code analysis
3.  Regression testing
4.  Mutation testing

## 3. During a port scan, Lauren found TCP port 443 open...

During a port scan, Lauren found TCP port 443 open on a system. Which tool is best suited to scanning the service that is most likely running on that port?

1.  zzuf
2.  Nikto
3.  Metasploit
4.  sqlmap

## 4. What message logging standard is commonly used...

What message logging standard is commonly used by network devices, Linux and Unix systems, and many other enterprise devices?

1.  Syslog
2.  Netlog
3.  Eventlog
4.  Remote Log Protocol (RLP)

## 5. Alex wants to use an automated tool to fill web application forms...

Alex wants to use an automated tool to fill web application forms to test for format string vulnerabilities. What type of tool should he use?

1.  A black box
2.  A brute-force tool
3.  A fuzzer
4.  A static analysis tool

## 6. Susan needs to scan a system for vulnerabilities...

Susan needs to scan a system for vulnerabilities, and she wants to use an open-source tool to test the system remotely. Which of the following tools will meet her requirements and allow vulnerability scanning?

1.  Nmap
2.  OpenVAS
3.  MBSA
4.  Nessus

## 7. NIST Special Publication 800-53A describes four major types...

NIST Special Publication 800-53A describes four major types of assessment objects that can be used to identify items being assessed. If the assessment covers IPS devices, which type of assessment objects is being assessed?

1.  A specification
2.  A mechanism
3.  An activity
4.  An individual

## 8. Jim has been contracted to perform a penetration test...

Jim has been contracted to perform a penetration test of a bank’s primary branch. In order to make the test as real as possible, he has not been given any information about the bank other than its name and address. What type of penetration test has Jim agreed to perform?

1.  A crystal box penetration test
2.  A gray box penetration test
3.  A black box penetration test
4.  A white box penetration test

## 9. Alex is using nmap to perform port scanning...

Alex is using nmap to perform port scanning of a system, and he receives three different port status messages in the results. Match each of the numbered status messages with the appropriate lettered description. You should use each item exactly once.

**Status message**

1.  Open
2.  Closed
3.  Filtered

**Description**

1.  The port is accessible on the remote system, but no application is accepting connections on that port.
2.  The port is not accessible on the remote system.
3.  The port is accessible on the remote system, and an application is accepting connections on that port.

## 10. In a response to a Request for Proposal...

In a response to a Request for Proposal, Susan receives an SSAE 18 SOC 1 report. If she wants a report that includes operating effectiveness detail, what should Susan ask for as follow-up and why?

1.  A SOC 2 Type II report, because Type I does not cover operating effectiveness
2.  A SOC 1 Type I report, because SOC 2 does not cover operating effectiveness
3.  A SOC 2 Type I report, because SOC 2 Type II does not cover operating effectiveness
4.  A SOC 3 report, because SOC 1 and SOC 2 reports are outdated

## 11. During a wireless network penetration test...

During a wireless network penetration test, Susan runs aircrack-ng against the network using a password file. What might cause her to fail in her password-cracking efforts?

1.  Use of WPA2 encryption
2.  Running WPA2 in Enterprise mode
3.  Use of WEP encryption
4.  Running WPA2 in PSK mode

## 12. A zero-day vulnerability is announced...

A zero-day vulnerability is announced for the popular Apache web server in the middle of a workday. In Jacob’s role as an information security analyst, he needs to quickly scan his network to determine what servers are vulnerable to the issue. What is Jacob’s best route to quickly identify vulnerable systems?

1.  Immediately run Nessus against all of the servers to identify which systems are vulnerable.
2.  Review the CVE database to find the vulnerability information and patch information.
3.  Create a custom IDS or IPS signature.
4.  Identify affected versions and check systems for that version number using an automated scanner.

## 13. What type of testing is used to ensure...

What type of testing is used to ensure that separately developed software modules properly exchange data?

1.  Fuzzing
2.  Dynamic testing
3.  Interface testing
4.  API checksums

## 14. Which of the following is not a potential problem...

Which of the following is not a potential problem with active wireless scanning?

1.  Accidently scanning apparent rogue devices that actually belong to guests
2.  Causing alarms on the organization’s wireless IPS
3.  Scanning devices that belong to nearby organizations
4.  Misidentifying rogue devices

## 15. Ben uses a fuzzing tool that tests an application...

Ben uses a fuzzing tool that tests an application by developing data models and creating fuzzed data based on information about how the application uses data. What type of fuzzing is Ben doing?

1.  Mutation
2.  Parametric
3.  Generational
4.  Derivative

## 16. Saria wants to log and review traffic information...

Saria wants to log and review traffic information between parts of her network. What type of network logging should she enable on her routers to allow her to perform this analysis?

1.  Audit logging
2.  Flow logging
3.  Trace logging
4.  Route logging

## 17. Jim has been contracted to conduct a gray box penetration test...

Jim has been contracted to conduct a gray box penetration test, and his clients have provided him with the following information about their networks so that he can scan them:

*   Data center: 10.10.10.0/24
*   Sales: 10.10.11.0/24
*   Billing: 10.10.12.0/24
*   Wireless: 192.168.0.0/16

What problem will Jim encounter if he is contracted to conduct a scan from offsite?

1.  The IP ranges are too large to scan efficiently.
2.  The IP addresses provided cannot be scanned.
3.  The IP ranges overlap and will cause scanning issues.
4.  The IP addresses provided are RFC 1918 addresses.
