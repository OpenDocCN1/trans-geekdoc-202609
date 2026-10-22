
### Exhibit 37.14 Privilege Management

| Alternative | Pros | Cons |
|---|---|---|
| Application-based access control | Easy to implement.<br>Does not require additional infrastructure, so saves cost. | Need to manage privileges on an application-by-application basis. Synchronization of privileges may be hard as applications increase and as they are distributed.<br>Security may be compromised if privileges are not removed from all applications. |
| Public Key Certificate | Easy to add to PKI.<br>Privileges can be managed easily by revoking certificate. | Higher operational costs.<br>Changes in privileges require revocation of identity certificate.<br>Sometimes this is a small price to pay for savings that result from not having to deploy and operate a separate privilege management infrastructure (PMI).<br>Parties issuing identity certificate may not have authority to bestow privileges. |
| Attribute Certificate | Privileges can be managed easily by revoking attribute certificates.<br>Change in privilege does not require revocation of public key certificate. | Cost of privilege management infrastructure (PMI). |

In a court of law, digital signatures may be disputed long after they were applied, if, for example, the cryptanalysis threat period for the keys has expired. In those circumstances, producing a document with a verified digital signature may not prevent repudiation. A party could claim that the cryptanalysis threat period has passed and the private key might have been discovered or broken by an adversary.

To mitigate both of these threats—data corruption and expiry of the cryptanalysis threat period—trusted archival services are required for transactions with a potential for this kind of dispute. Such an archival service also would be able to safeguard associated certificates and CRLs. Trusted archival services should depend on controls such as physical security, stable media (e.g., write-once read-many (WORM) devices), and appropriate techniques to maintain readability despite changing technologies. Such services should be capable of error-free transcription of data on older media and of translating outdated encoding into more modern media, and into current encoding schemes. For example, Extended Binary Coded Decimal Interchange Code (EBCDIC)-encoded data on nine-track magnetic tapes could be copied onto optical disks using ASCII encoding.

A related technology is the trusted time stamp, where a trusted third party attaches the current valid time to a document and signs it to prove the existence of the document

## CHAPTER 38: WRITING SECURE CODE

Lester E. Nichols, M. E. Kabay, and Timothy Braithwaite

- 38.1 INTRODUCTION 38-1
- 38.2 POLICY AND MANAGEMENT ISSUES 38-1
  - 38.2.1 Software Total Quality Management 38-2
  - 38.2.2 Due Diligence 38-4
  - 38.2.3 Regulatory and Compliance Considerations 38-5
- 38.3 TECHNICAL AND PROCEDURAL ISSUES 38-5
  - 38.3.1 Requirements Analysis 38-5
  - 38.3.2 Design 38-6
  - 38.3.3 Operating System 38-6
  - 38.3.4 Best Practices and Guidelines 38-7
  - 38.3.5 Languages 38-9
- 38.4 TYPES OF SOFTWARE ERRORS 38-10
  - 38.4.1 Internal Design or Implementation Errors 38-10
- 38.5 ASSURANCE TOOLS AND TECHNIQUES 38-15
  - 38.5.1 Education Resources 38-15
  - 38.5.2 Code Examination and Application Testing Techniques 38-16
  - 38.5.3 Standards and Best Practices 38-20
- 38.6 CONCLUDING REMARKS 38-20
- 38.7 FURTHER READING 38-21
- 38.8 NOTES 38-22

### 38.1 INTRODUCTION

The topic of secure coding cannot be adequately addressed in a single chapter. Unfortunately, programs are inherently difficult to secure because of the large number of ways that execution can traverse the code as a result of different input sequences and data values. The additional pressures to get the applications to market can also take a toll on the secure coding process.

This chapter provides a starting point and additional resources for security professionals, system architects, and developers to build a successful and secure development methodology. Writing secure code takes coordination and cooperation of various functional areas within an organization, and may require fundamental changes in the way software development currently is designed, written, tested, and implemented, as well as a change in corporate culture as it pertains to software development.

### 38.2 POLICY AND MANAGEMENT ISSUES

There are countless security hurdles facing those writing code and developing software. Today dependence on the reliability and security of the automated system is nearly total. For an increasing number of organizations, distributed information processes, implemented via networked environments, have become the critical operating element of their business. Not only must the processing system work when needed, but also the information processed must retain its integrity so that it can be trusted in use. Because of a general lack of basic IT organizational discipline, and adherence to fundamental software and systems development and maintenance principles, most software development efforts have been significantly lacking at best. If the same inadequate practices are left unchanged in the face of increasing cyber threats, they will continue contributing to the insecure systems of tomorrow, just as they have contributed to the insecure systems of today.

The fundamental problem underlying this kind of assertion is the difficulty of justifying what are often perceived as non-revenue-generating activities and the need to get the product to market on or before delivery timelines. The difficulty also stems from the infeasibility of proving a negative. For example, one cannot prove to the uninvolved or unimpressed observer that the time, money, and human resources spent on prevention are well spent simply because a disaster or incident was averted. Such an observer will take the fact that it did not occur as evidence that the possibility never really existed or that the problem was exaggerated. In the same way, a skeptical observer may take the absence of security breaches as evidence that no such threat existed, or that it was never as bad as claimed. The problem is exacerbated after spending time and effort on establishing security policies, security controls, and enforcement mechanisms.

In both cases, the money, time, and effort expended to prevent adverse computing consequences from harming an organization are viewed with suspicion and not qualifying at a level to justify the change in delivery schedule or funding. However, such suspicions are not new in the world of information processing. Throughout the history of IT, this attitude has existed regarding problem-prevention activities such as quality assurance, quality control testing, documentation, configuration management, change management, and other system-management controls designed to improve quality, reliability, and system maintainability.

If you consider the analogy of application development as being similar to the way a house is built, it is much harder to implement and integrate something after the fact. Security is not and should not be considered a superficial exercise similar to hanging the drapes or changing a light bulb. It is like the plumbing of a house, and it needs to be implemented with that in mind.

Problems with security are management problems. Management dictates how much time and money can be spent on security activities such as risk management and software testing. How much time and energy are invested in designing, building, testing, and fixing software is in the end a management call. Thus, the primary concern of those striving to improve software security must be the correction of these same basic and fundamental IT management defects: otherwise effective security can never be attained or maintained.

### 38.2.1 Software Total Quality Management

The nature of the computer security challenge is that of dynamically changing vulnerabilities and threats, based on rapidly changing technologies, used in increasingly complex business applications. Organizations need to build software around the idea of a continuous improvement model, as popularized by the total quality management (TQM) articulated in the ISO 9000 family of standards. For purposes of quality improvement, this model was viewed as a continuing cycle of plan-do-check-and-act. For software security, it can be thought of as a cycle of plan-fix-monitor-and-assess. A security management process to
