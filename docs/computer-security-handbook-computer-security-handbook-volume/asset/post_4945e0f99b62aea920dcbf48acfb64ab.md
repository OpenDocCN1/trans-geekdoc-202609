
be documented appropriately and escalated to management; it then will assist the regulatory compliance efforts.

### 39.8.6 Hacking

When bugs and problems do occur, hacking—both internal and external—should be considered a possibility and searched for by reviewing the logs of who worked on the software and when that work was done. Managers should be able to spot the use of legitimate IDs when the individuals involved were on vacation, out sick, or not available to log on for other reasons.

Archiving logs and retrieving them is an increasingly critical capability, aside from the regulatory requirements of SOX, HIPAA, GLBA, and so on. Logs are often used for:

- Incident response activities, particularly in determining:
  - If an incident occurred
  - When an incident occurred
  - What happened prior to and subsequent to when an incident is suspected to have occurred
- Research; this can be to review performance capabilities or issues of hardware or software or networking

To ensure that the logs are available when needed, the organization needs a sound strategy that preserves and archives logs periodically, so that an attacker or a system anomaly does not wipe them from the system’s hard drive. Although there are many means to accomplish this, a frequently used inexpensive method involves establishing a log server. For example, an organization might identify a discarded desktop computer, outfit it with a new, high-speed, high-capacity optical read-only memory (ROM) drive, and increase memory capacity (if needed). By routing the logs to the optical drive frequently and recording them throughout the day (perhaps multiple times during an hour) and changing the optical disk at least daily, the organization will create a forensically sound archive that can be duplicated easily for research, law enforcement, or legal use. Often the daily logs volume will not fill a DVD or a CD. However, having the regular routine of changing the media daily helps ensure that the media does not reach its capacity at an inopportune time—indeed, if a worm such as Blaster or Nimda infects the organization, then the logs likely will swell rapidly. Too, if an attacker within the system stops the logging, the organization should encounter less difficulty determining the date, time (or time period), and extent of the intrusion because ROM cannot be overwritten, in contrast with read-write (RW) media.

Unauthorized changes to code and data sometimes can be identified even if the perpetrator stops the logging and deletes or modifies log files. One method is to create checksums for production or other official versions of software and to protect the checksums against unauthorized access and modification using encryption and digital signatures. Similarly, unauthorized data modifications sometimes can be made more difficult by creating checksums for records and linking the checksums to time and date stamps and to the checksums for authorized programs. Under those conditions, unauthorized personnel and intruders find it difficult to create valid checksums for modified records. Other products, such as intrusion detection systems (IDSs) or intrusion prevention systems (IPSs), may be useful in an organization’s protection and risk-management strategy.

### 39.9 CONCLUSION

This chapter has presented a comprehensive overview of the software development and quality assurance processes that must be utilized when developing, implementing, and modifying software. Software development involves more than simply selecting and utilizing an approach such as the traditional, waterfall, or RAD methodology. It means working as a team to develop, review, refine, and implement a viable working product. Many good techniques and products can be applied to both the SDLC and the quality assurance portions of producing software; some of the key elements are good documentation, allowing sufficient time for testing in the development and maintenance processes, building good tests, establishing test data, automating testing, and keeping track of change requests.

### 39.10 FURTHER READING

- Basandra, S. Software Architecture, Data Structures, Algorithms, Programming and Testing Questions and Answers. Basandra Books, 2013.
- Black, D. B. Software Quality Assurance (Building Better Software Better). Amazon Digital Publishing, 2012.
- Chemuturi, M. Mastering Software Quality Assurance: Best Practices, Tools and Techniques for Software Developers. J. Ross Publishing, 2010.
- Fox, C., and P. Zonneveld. IT Control Objectives for Sarbanes-Oxley: The Role of IT in the Design and Implementation of Internal Control Over Financial Reporting. 2nd ed. IT Governance Institute, 2006.
- Godbole, N. S. Software Quality Assurance: Principles and Practices, 2nd ed. Alpha Science International Ltd., 2013.
- Hambling, B., and P. van Goethem. User Acceptance Testing—A Step-by-Step Guide. BCS, The Chartered Institute for IT, 2013.
- Horch, J. W. Software Quality Assurance: A Standards-based Guide. IEEE Computer Society, 2013.
- ISO/IEC. "ISO/IEC 29119 Software Testing: The new international software testing standard." ISO/IEC, 2013. www.softwaretestingstandard.org/index.php
- McCaffrey, J. D. Software Testing: Fundamental Principles and Essential Knowledge. BookSurge Publishing, 2009.
- OWASP. "Fuzzing." Open Web Application Security Project, 2013. https://www.owasp.org/index.php/Fuzzing
- Rasmussen, J. The Agile Samurai: How Agile Masters Deliver Great Software. Pragmatic Bookshelf, 2013.
- Rubin, K. S. Essential Scrum: A Practical Guide to the Most Popular Agile Process. Addison-Wesley Professional, 2012.
- Shaffer, S. C. A Brief Introduction to Software Development and Quality Assurance Management. S. C. Shaffer Publications, 2013.
- Tassey, G. The Economic Impacts of Inadequate Infrastructure for Software Testing: Final Report. RTI Project Number 7007.011. NIST, 2002.
- Wells, D. Extreme Programming: A Gentle Introduction. XP, 2009, www.extremeprogramming.org
- Wood, D. C. Principles of Quality Costs: Financial Measures for Strategic Implementation of Quality Management, 4th ed. Quality Press, 2013.

## MANAGING SOFTWARE PATCHES AND VULNERABILITIES

Karen Scarfone, Peter Mell, and Murugiah Souppaya

| Section | Page |
| --- | --- |
| 40.1 INTRODUCTION | 40·1 |
| 40.2 THE IMPORTANCE OF PATCH MANAGEMENT | 40·2 |
| 40.3 THE CHALLENGES OF PATCH MANAGEMENT | 40·2 |
| 40.3.1 Timing, Prioritization, and Testing | 40·3 |
| 40.3.2 Patch Management Configuration | 40·4 |
| 40.3.3 Alternative Host Architectures | 40·5 |
| 40.3.4 Other Challenges | 40·6 |
| 40.4 ENTERPRISE PATCH MANAGEMENT TECHNOLOGIES | 40·7 |
| 40.4.1 Components and Architecture | 40·7 |
| 40.4.2 Security Capabilities | 40·8 |
| 40.4.3 Management Capabilities | 40·9 |
| 40.5 METRICS AND MEASURES | 40·10 |
| 40.6 FURTHER READING | 40·11 |
| 40.7 NOTES | 40·11 |

### 40.1 INTRODUCTION

Vulnerabilities are flaws that can be exploited by a malicious entity to gain greater access or privileges than it is authorized to have on a computer system. Patches are additional pieces of code developed to address problems (commonly called “bugs”) in software. Patches correct security and functionality problems in software and firmware. Patch management is the process for identifying, acquiring, installing, and verifying patches for products and systems. Patch management is a security practice designed to proactively prevent the exploitation of IT vulnerabilities that exist within an organization. The expected result is to reduce the time and money spent dealing with vulnerabilities and the exploitation of those vulnerabilities. Proactively managing vulnerabilities of systems will reduce or eliminate the potential for exploitation and involve considerably less time and effort than responding after an exploitation has occurred.

This chapter is designed to assist organizations in implementing patch and vulnerability remediation programs. It first explains the importance of patch management and then discusses the challenges inherent in performing patch management. Next, the chapter provides an overview of enterprise patch management technologies and gives recommendations for their use. It also seeks to inform the reader about possible measures and metrics for enterprise patch management.¹
