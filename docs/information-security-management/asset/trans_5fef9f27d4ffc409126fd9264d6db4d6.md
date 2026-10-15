
### 2. 
Carges, M., Belisle, D., & Workman, M. (1990). The portable operating system interface: Distributed database transaction processing systems and the XA protocol. IEEE Standard 1003.11 & X/Open-POSIX, Parsippany, NJ: ISO/IEC.

### 3. 
Workman, M. (2019, July 5). Missteps involved in cybersecurity mishaps: A study of social media influences in human security behaviors. Proceeding from the Annual CINSec Conference (pp. 291–303). Lyon FR.

### 4. 
Behr, K., Kim, G., & Spafford, G. (2004). The visible OPs handbook: Starting ITIL in 4 practical steps. Eugene, OR: IT Process Institute.

### 5. 
Uyheng, J., Ng, L.H.X., & Carley, K.M. (2021). Active, aggressive, but to little avail: Characterizing bot activity during the 2020 Singaporean elections. Comput Math Organization Theory. https://doi.org/10.1007/s10588-021-09332-1

### 6. 
Johnson, A., Dempsey, K., Ross, R., Gupta, S., & Bailey, D. (2010). Guide for security configuration management of information systems. Gaithersburg, MD: Computer Security Division Information Technology Laboratory National Institute of Standards and Technology (NIST), SP 800-128.

### 7. 
Tennent, G. (2001). Six sigma: SPC and TQM in manufacturing and services. Burlington, MA: Gower Publishing.

![](images/part-openor.jpg)

## PART THREE  

Technologies and Techniques

© Antishock/Shutterstock

*   [Chapter 9  Security Policies and Managing Behaviors](#9781284211658_CH09.xhtml)

*   [Chapter 10 Cryptography](#9781284211658_CH10.xhtml)

*   [Chapter 11 Network Security, Firewalls, IDS, and SeCM](#9781284211658_CH11.xhtml)

*   [Chapter 12 Information Security Management](#9781284211658_CH12.xhtml)

![](images/chapter-openor.jpg)

## CHAPTER 9  

Security Policies and Managing Behaviors

© Antishock/Shutterstock

Even though cryptography is readily available and prescribed by companies in security policies, people do not always follow these directives. For example, Administaff Corporation circulated a letter to victims that read in part: “… an Administaff laptop computer containing personal information including Social Security numbers, names and addresses of current and former Administaff worksite employees was reported missing ... The laptop computer is password protected; however, the personal information was not saved in an encrypted location, which is a clear violation of company policies.” Later, credit monitoring companies found information from that laptop being sold on the Darknet. Such a violation of policy should never occur on a technology manager’s watch, but how do we prevent it?

Have you ever been a victim of identity theft? A recent FBI report stated that one in three people will become a victim at some point in his or her lifetime.

## 9.1 Security and Policies

We will take a break from the more technical aspects of information and cybersecurity for a bit and shift gears to look at organizational security behaviors and policies. A primary role for technology managers as far as security is concerned is to provide well-defined expectations for security behaviors. Part of this includes enforcing security policies. A security policy consists of rules and practices that govern acceptable security behaviors and serves as a foundation for the specifications of rules for systems and applications usage. As we discussed in the chapter on computer security, a system remains trusted by fulfilling and enforcing security policies and often the relationships between subjects and objects. The policy indicates what subjects can access which objects and what actions are permitted and denied, along with potential penalties for violations of the policy. Policies are important because for a system to provide an acceptable level of trust, it must be based on an architecture that provides the capabilities to protect itself from untrusted processes, intentional or accidental compromises, and attacks at different layers of the system.

| Automated Security Policies || Security policies may be codified into rules, such as in firewalls. For example, recall the concept of a reference monitor. A reference monitor establishes that the security kernel must control access such that all subjects must have proper authority to access objects. The security kernel comprises all the resources that supervise system activity in accordance with the system’s security policy and is part of the operating system that controls access to system resources. For this to work properly, individual resources must be isolated from each other, and domains need to be defined to dictate the objects that are available for access by authorized subjects. |

| --- | --- |

| Written Security Policies || Written security policies are directed at employees to govern acceptable behaviors. They are legal documents and thus should be drafted by attorneys and the human resources department. They outline, among other things, acceptable use, define access for least privileges, and outline sanctions for violations. |

| Least Privilege || Once resources and processes are isolated properly, least privilege needs to be enforced. This means that a user or process has no more privileges than necessary to be able to fulfill its job functions. Only processes that need to carry out critical system functions should be allowed, and less-privileged processes need to invoke privileged adjuvant processes such as system calls to carry out these types of activities when necessary. This type of indirect activity protects the system from poorly written or misbehaving code, creates semaphores where needed, and allows for logging and audits. |

### 9.1.1 Security Policies and Employment Law

If we are talking about security policies related to employee misconduct, we are necessarily also talking about employment law. Recall that under common law, a contract of employment for other than a definite term is terminable at will by either party. Accordingly, employers may dismiss their employees at will for good cause, for no cause, or even for a cause that might be considered morally reprehensible, without being guilty of a legal wrong. However, recently, the courts have delineated a growing number of implied contract and public policy grounds for allowing suits to be brought against former employers under federal and state-enacted rules (see Novosel v. Nationwide Insurance Company).[¹](#9781284211658_CH09_09.xhtml#c9-bib0001) There are also a growing number of tort suits.[²](#9781284211658_CH09_09.xhtml#c9-bib0002) A tort is defined as a breach of legal duty to exercise reasonable care that proximately causes injury or damage to another. This is a civil wrongdoing that does not arise from a breach of contract.

Because there are many international, federal, and state (or province, geographical, or local) laws that can be involved when it comes to security law, employment, and policies, when organizational policies are crafted it bears repeating that it is important to have legal guidance (such as from corporate attorneys in the legal department) along with the involvement of the human resources department. Still, the implementation and enforcement of written policies are often the burden of management, and so managers cannot afford to be ignorant of the law—and ignorance of the law is not a defense in a court of law.[³](#9781284211658_CH09_09.xhtml#c9-bib0003)
