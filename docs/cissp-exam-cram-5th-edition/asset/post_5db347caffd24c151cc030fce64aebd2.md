

- B. It is used for reviewing audit logs.
- C. It is used to exploit systems.
- D. It is used to find vulnerabilities.

### 13. Which of the following is a powerful way to test how an application reacts to various inputs?

- A. Synthetic transactions
- B. Fuzzing
- C. Dynamic code analysis
- D. Static code analysis

### 14. What type of penetration test examines what insiders can access?

- A. Whitebox
- B. Graybox
- C. Blackbox
- D. Bluebox

### 15. Which of the following individuals are known for their attacks on analog phone and telecommunication systems?

- A. Script kiddies
- B. Phreakers
- C. Crackers
- D. Hackers

## Answers to Exam Prep Questions

1. C. IP spoofing is a common practice when DoS tools are used to help an attacker mask his identity. Salami attacks, data diddling, and keystroke logging do not typically spoof IP addresses, so answers A, B, and D are incorrect.

2. C. This more advanced spoofing attack works by subverting the TCP connection between a client and a server. If it is successful, the attacker has a valid connection to the victim’s network and is authenticated with his credentials. This type of attack is very hard to do with modern operating systems but is trivial with older operating systems. Answer A is incorrect because session hijacking does not involve DNS; it functions by manipulating the TCP sequence number. Answer B is incorrect because session hijacking does not use UDP; UDP is used for stateless connections. Answer D is incorrect because, again, session hijacking is not based on DNS and UDP. These two technologies are unrelated to TCP sequence numbers.

3. B. The best defense against social engineering is to educate users and staff. Training can go a long way toward teaching employees how to spot scams. Although the other answers are not bad ideas, they will not prevent social engineering, so answers A, C, and D are incorrect.

4. D. Audits are a detective control. Answers A, B, and C are incorrect because they are not detective or compensating controls.

5. A. Insiders are the biggest threat to an organization because they possess two of the three things needed to attempt malicious activity: means and opportunity. Answers B, C, and D are incorrect because although outsiders might have a motive, they typically lack the means or opportunity to attack an organization.

6. B. NIST 800-137 defines ISCM. Answers A, C, and D are incorrect. NIST 800-92 addresses log management, NIST 800-115 deals with penetration testing, and ITIL is a framework of best practices for delivery of IT services.

7. D. SOC 3 for Service Organizations reports are general use reports that can be freely distributed. Answers A, B, and C are incorrect because SOC 1 reports are for evaluating the effect of controls at the service organization on users’ financial statements. SOC 2 reports provide detailed information about how a service organization handles users’ data and the confidentiality and privacy of the information processed by these systems. There is no SOC 4 designation.

8. D. While anyone can declare an emergency, only a business continuity planning coordinator can declare a disaster. Therefore, answers, A, B, and C are incorrect.

9. B. A UPS is best option for a graceful shutdown. Answer A is incorrect because a generator is for long-term recovery. Answers C and D are incorrect because redundant power supplies and dual power feeds are not short-term solutions.

10. B. Ethical hackers use the same methods as crackers and black hat hackers, but they report the problems they find instead of taking advantage of them. Ethical hacking has other names, such as penetration testing, intrusion testing, and red-teaming. Answer A is incorrect because ethical hackers do not have permission to destroy networks. Answer C is incorrect because ethical hackers can be held liable. Answer D is incorrect because ethical hackers can be jailed if they break the law or exceed the terms of their contract.

11. C. Synthetic transactions are run against a monitored system to see how it responds. Answer A is incorrect because Fagen inspections are carried out during code development. Answer B is incorrect because static code analysis is a type of manual review. Answer D is incorrect because fuzzing uses random variables as inputs to evaluate the output.

12. D. SATAN, the first vulnerability assessment program, was designed to find vulnerabilities in a network. Programs like Retina and Nessus are also used for vulnerability assessment. SATAN is not used for password cracking (answer A) or auditing logs (answer B), and it is not used to exploit systems (answer C).

13. B. There are two types of fuzzing: generation based and mutation based. Answer A is not correct because synthetic transactions are real-time transactions that are performed on monitored objects. Answer C is incorrect because dynamic code analysis is designed to test a running application for potentially exploitable vulnerabilities. Answer D is incorrect because static code analysis is a method of debugging that involves examining source code before a program is run.

14. B. Graybox testing aims to determine what type of activities can be performed. Answer A is incorrect because with whitebox testing, everything is known about the network. Answer C is incorrect because with blackbox testing, nothing is known about the network. Answer D is incorrect because blueboxing is a term used by phreakers to make free phone calls via a mechanical device.

15. B. Phreakers are individuals who are known for their attacks on analog phone and telecommunications equipment. Answers C and D are incorrect because hackers and crackers are both types of computer criminals. Answer A is incorrect because script kiddies are junior hackers who rely on using others’ processes and programs to attack computers.

## Need to Know More?

- RFC 1087: www.faqs.org/rfcs/rfc1087.html
- NIST 800-137: https://csrc.nist.gov/publications/detail/sp/800-137/final
- COBIT versus ISO 27001: https://advisera.com/27001academy/blog/2019/05/06/cobit-vs-iso-27001-how-much-do-they-differ/
- DOJ site on cybercrime: www.cybercrime.gov
- Fagan inspection: http://www.osel.co.uk/presentations/fitsbnwtf.pdf
- Log management (NIST 800-92): https://csrc.nist.gov/publications/detail/sp/800-92/final
- Synthetic transactions: www.logicmonitor.com/blog/an-introduction-to-executing-synthetic-transactions-with-logicmonitor/
- Misuse case testing: https://sqa.stackexchange.com/questions/1804/abuse-cases-and-misuse-cases
- Detecting vulnerabilities with SCAP and OVAL: https://www.integrigy.com/security-resources/stigs-scap-oval-oracle-databases-and-erp-security
- EU privacy laws: en.wikipedia.org/wiki/Data_Protection_Directive
- Generation and mutation fuzzing: www.f-secure.com/en/consulting/our-thinking/15-minute-guide-to-fuzzing

Federal rules of evidence: www.law.cornell.edu/rules/fre/

CVEs and CVSS defined: www.imperva.com/learn/application-security/cve-cvss-vulnerability/

Passive vulnerability monitoring: www.honeynet.org

Hearsay defined: https://en.wikipedia.org/wiki/Hearsay

Best practices for log review: www.computerweekly.com/tip/Best-practices-for-audit-log-review-for-IT-security-investigations

## Chapter 8

## Security Operations

### Terms you'll need to understand:

- Redundant array of inexpensive disks (RAID)
- Clustering
- Distributed computing
- Cloud computing
- Media management
- Least privilege
- Mandatory vacations
- Due care
- Due diligence
- Privileged entities
- Clipping level
- Resource protection

### Topics you'll need to master:

- Disaster recovery processes and plans
- How to understand and support investigations
- Foundational security concepts
- Different types of RAID
- How to implement disaster recovery strategies and recovery strategies
- How to participate in business continuity planning and exercises
- Perimeter and internal physical controls
- How to implement disaster recovery processes
- Auditing and monitoring

## Introduction

When preparing for the (ISC)² CISSP exam or reviewing the Security Operations domain, you need to understand what resources should be protected and be familiar with principles of best practices; methods to restrict access, protect resources, and monitor activity; and how to respond to incidents.

The Security Operations domain covers a wide range of topics involving operational security best practices. Security professionals apply operational controls to daily activities to keep systems running smoothly and facilities secure. This chapter reviews those controls and shows how their application to day-to-day activities can prevent or mitigate attacks.

The process starts before an employee is hired. Employers should perform background checks, reference checks, criminal history reports, and educational verification. Among many other onboarding tasks, a new employee must be trained on corporate policies.

Controls need to be put in place to limit the ability and access an employee has. Access is a major control that should be limited to just what is needed to complete required tasks; this limit is referred to as *least privilege*. Job rotation, dual control, and mandatory vacations are also several examples of these types of controls.

Controls are not just about people. Controls are also needed to deal with system failure. Disaster recovery and business continuity planning and exercises are key controls in this area.

Many of the controls discussed in this chapter are technical in nature. These

