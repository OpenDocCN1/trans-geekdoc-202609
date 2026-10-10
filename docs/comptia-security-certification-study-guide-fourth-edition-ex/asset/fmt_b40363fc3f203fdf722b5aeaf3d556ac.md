
# Performing a Penetration Test

## 8. Which of the following tools will help you identify what services are running on the system?

A. Honeynet
B. Sniffer
C. Port scanner
D. Honeypot

## 9. Your manager has just heard of a new exploit against SQL servers and would like to locate these servers on the 192.168.2.0 network. Which of the following would accomplish this goal?

A. `ping -t 192.168.2.0`
B. `nmap -sS 192.168.2.0/24 -p 1433`
C. `dig www.gleneclarke.com`
D. `nmap -sS 192.168.2.0/24 -p 3389`

## 10. Your manager has hired a consultant to perform a penetration test. She asks that you not give the tester any details of the company or the configuration. What type of test is she looking to have performed?

A. Known environment
B. Unknown environment
C. Partially known environment
D. Internet environment

## 11. Which of the following is a penetration testing toolset that has hacking tools preinstalled for your use during a penetration test?

A. LANguard
B. Nessus
C. Kali
D. nmap

# Tools Used to Assess Security

## 12. You have configured a system to use as a honeypot and have ensured that you have configured the security on the system so that it is not too easy for a hacker to get in. What else should you configure on the honeypot?

A. Have a blank password on the administrative account.
B. Configure a Trojan virus.
C. Open extra ports on the system.
D. Enable logging.

## 13. You want to assess the passwords used on the network and see how easy it is to crack them. What tool will you use?

A. John the Ripper
B. nmap
C. LANguard
D. Nessus

## 14. Which of the following tools is considered a passive tool?

A. John the Ripper
B. nmap
C. Metasploit
D. Sniffer

## 15. Which of the following tools can be used to crack passwords on a system when performing a penetration test?

A. John the Ripper
B. dig
C. nmap
D. nslookup

## 16. What is the term used for a group of systems that have been configured to lure the hacker away from production systems?

A. Honeypot
B. LAN
C. DMZ
D. Honeynet

# Performance-Based Question

## 17. Using the following exhibit, match the characteristic on the left with the type of scan listed on the right.

![Image](f0821-01.jpg)

# SELF TEST ANSWERS

## Understanding Types of Assessments

### 1.
**B.** Penetration testing is considered active testing because you are performing actual attacks on the systems and trying to compromise the security controls.

**A, C,** and **D** are incorrect. Vulnerability scanning, or assessment, is known as a passive method of performing an assessment because you are not actually trying to compromise the security controls of the system. `LANguard` is an example of a vulnerability scanner. Risk assessment is passive as well because you are only listing the threats against the system and figuring out how to mitigate those threats.

### 2.
**D.** Any time your business develops an application, you should perform a code review to make sure that no unsecure code is in the application. You are checking to ensure that developers validate input and do not create back doors to the application.

**A, B,** and **C** are incorrect. A risk assessment involves identifying the assets, the threats against those assets, and then planning how to mitigate those threats. A threat assessment is part of the risk assessment (analysis). A penetration test is actively trying to bypass the security controls of a system.

### 3.
**C.** If you are not allowed to try to compromise a system by bypassing the security controls of the system, then perform a vulnerability scan to identify missing patches or configuration errors within a system.

**A, B,** and **D** are incorrect. A penetration test involves trying to hack into the system to determine its security, and in this case, the scenario stated that this type of action is not allowed. A design review involves reviewing the requirements of a solution to ensure that the solution meets the demands. A code review involves reviewing application code to verify that the code was developed in a secure way.

### 4.
**A.** A risk assessment involves identifying the assets, the threats against those assets, and how to mitigate those threats.

**B, C,** and **D** are incorrect. A code review involves reviewing application code to verify that it was developed in a secure way. A design review involves reviewing the requirements of a solution to ensure that the solution meets the demands. A penetration test involves trying to hack into the system to determine its security.

### 5.
**B.** Before doing anything that relates to the penetration test, you first have to find out the scope of what needs to be done and then have a legal document drafted by a lawyer stating you have permission to perform such actions. The document needs to be signed by upper-level management of the company for which you are performing the pentest.

**A, C,** and **D** are incorrect. Although you will create a test plan eventually and most likely will do some password-cracking and buffer overflow attacks, you first need signed approval from management.

## Performing a Security Assessment

### 6.
**C.** Passive security testing means that you are not actually trying to bypass the security controls, but are simply looking at the state of the system or environment to assess the security. Vulnerability scanners assess the level of security without trying to bypass the security of the system.

**A, B,** and **D** are incorrect. Active testing is intrusive in the sense that an active test tries to compromise security by attempting to bypass the security controls and hack into the system. Penetration testing uses active assessment techniques.

### 7.
**B.** Performing a credentialed scan allows you to authenticate with the system and collect more information about it than an anonymous (noncredentialed) scan would.

**A, C,** and **D** are incorrect. You would not perform a noncredentialed (anonymous) scan, as that is likely the scan type you are currently performing. You also would not use `Metasploit`, as that is a toolset used to actively compromise the system and is considered intrusive. You would not try to perform password cracking either, as that is considered hacking and is intrusive (your manager is looking for nonintrusive methods).

## Performing a Penetration Test

### 8.
**C.** Port scanners identify what ports are open, which helps determine what services are running on a system. For example, if port 80 is open on a system, you know that web server software is running.

**A, B,** and **D** are incorrect. A honeynet is a fake network created to lure a hacker away from the real network. A sniffer is a passive tool that will capture network traffic, and a honeypot is a fake system that will lure a hacker away from production systems and log all the steps the hacker takes to hack into the system.

### 9.
**B.** You can use a port scanner such as `nmap` to locate specific services on the network. In this example, you want to locate SQL servers, which listen on port 1433 by default.
