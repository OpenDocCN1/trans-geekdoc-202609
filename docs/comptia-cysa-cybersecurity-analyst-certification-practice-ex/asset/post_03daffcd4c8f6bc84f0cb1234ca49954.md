
A. Information: private, Asset: critical
B. Information: private, Asset: noncritical
C. Information: public, Asset: critical
D. Information: proprietary, Asset: noncritical

# QUICK ANSWER KEY

+ 1. A
2. C
3. B
4. D
5. A, B
6. A, B, C, D, E
7. C
8. A
9. D
10. D
11. C, D
12. A, C, F
13. D
14. A, C
15. B
16. D
17. C
18. C
19. A
20. C
21. A, B
22. B
23. C
+ 24. A, B, C
25. A
26. B
27. E
28. A
29. C
30. B
31. A
32. E
33. B
34. D
35. A
36. D
37. C
38. D
39. B
40. A

# IN-DEPTH ANSWERS

1. A company needs a vulnerability scan performed on its internal network. After the company consults with an external cybersecurity analyst, the analyst immediately begins drafting a contract to outline conditions to be met for the scan. These conditions limit including who is allowed to view the results, specifying what servers and data must not be accessed under any circumstances, satisfying the company's need for two types of scans to be done quarterly. Which of the following is the most likely reason behind these conditions?

+ A. Regulatory requirements
B. Security policy
C. Analyst's recommendation
D. Past experience deems the contract prudent

A is correct. Regulatory requirements are by far the most likely driver of the contract. The conditions stated are examples of regulatory requirements.

B, C, and D are incorrect. B is incorrect because although security policy is also a likely reason behind the contract, the sample requirements are similar to HIPAA and PCI DSS requirements. C is incorrect because the analyst would offer the suggestion but not likely draft a contract with those specific conditions. D is incorrect because experience would not be the most likely cause.

+ 2. Regulatory requirements can specify the need for vulnerability scanning when a company is in the financial or health industry. However, what best specifies vulnerability scanning as a requirement without regulatory requirement?

+ A. CISO mandate
B. Local and/or national legislation
C. Corporate policy
D. NIST 800-53

+ C is correct. Corporate policy is the most likely internal source of such requirements.

+ A, B, and D are incorrect. A is incorrect because a CISO could require the scanning but would so via policy. B is incorrect because legislation suggests regulatory requirements. D is incorrect because NIST 800-53 suggests but does not manage vulnerability scanning.

+ 3. What is a technique that allows a company to vary resources spent protecting data according to a set value?

+ A. Data encryption
B. Data classification
C. Data criticality
D. Data storage location

+ B is correct. Data classification provides a method of allocating resources varying amounts based on the criticality or sensitivity of the data.

+ A, C, and D are incorrect. A is incorrect because encryption protects data but not according to its value. C is incorrect because criticality is an attribute that can classify the data, not a means to protect it. D is incorrect because storage location is not a practical primary means of protecting data to its value.

+ 4. With regard to asset inventory, how would a cybersecurity analyst classify assets such as financial systems, intellectual property, and a customer-facing ordering system?

+ A. Noncritical
+ B. Sensitive
+ C. Credentialed
+ D. D is correct. Those asset examples should be deemed critical, versus noncritical.

A, B, and C are incorrect. A is incorrect because those assets are certainly critical assets. B is incorrect because while the assets might have sensitive data, the assets themselves are critical. C is incorrect because credentialed is not a type of asset.

+ 5. When a company is developing a vulnerability management plan, its assets must be inventoried. Which of the following asset types would be included? (Choose all that apply.)

+ A. Noncritical
+ B. Critical
+ C. Critical only
+ D. On-site and assets of partners and suppliers

+ A and B are correct. Critical and noncritical assets both should be inventoried when developing a vulnerability management plan.

+ C and D are incorrect. C is incorrect because a company can inventory all its assets, whether on-site, mobile, or company assets currently at remote locations. D is incorrect because partner and supplier assets are not within a company's scope to be tracked.

+ 6. The frequency with which a company performs vulnerability scanning is dependent upon which of the following criteria? (Choose all that apply.)

+ A. Scanning policy
+ B. Vulnerability management planning
+ C. Risk appetite
+ D. Regulatory requirements
+ E. Limitations of time, tools, and personnel

+ A, B, C, D, and E are correct. All of those are important factors in determining vulnerability scanning frequency.

7. The cybersecurity analyst must consider several factors when determining vulnerability scanning frequency. Criteria such as network bandwidth, systems’ CPU capacity, and number of personnel are examples of which?

+ A. Soft restrictions
+ B. Regulatory requirements
+ C. Technical constraints
+ D. Budgetary limitations

C is correct. These are examples of technical constraints.

A, B, and D are incorrect. A is incorrect because "soft restrictions" is not a common term. B is incorrect because regulatory requirements would not include these. D is incorrect because although budgetary limitation might impact frequency, it is not the category for these specific metrics.

8. Apart from policies and regulatory requirements, what creates the largest impact on vulnerability scanning?

+ A. Regular routine of personnel
+ B. Management style of IT director
+ C. Mandates from information security
+ D. The CEO

A is correct. The regular routine of personnel has a huge impact.

B, C, and D are incorrect. The management style and mandates from executives are not the primary drivers here.

9. When a company is configuring tools to perform vulnerability scans, which of the following would be the earliest step?

+ A. Choosing the plug-ins
+ B. Generating reports
+ C. Establishing permissions
+ D. Establishing criteria

D is correct. Establishing criteria would come before the other options.

A, B, and C are incorrect. A is incorrect because choosing the correct plug-ins would come after determining criteria. B is incorrect because reports aren't generated before. C is incorrect because permissions would follow establishing criteria.

10. Cybersecurity analyst is performing a vulnerability scan of few systems, including a server processing protected health information (PHI). The scan of all servers completed successfully, with no interruption of service. To demonstrate proof of weaknesses found during the vulnerability scan, the analyst manages to exfiltrate documents from each server. Which of the following specifications of vulnerability scanning did the analyst likely breach?

+ A. Using credentials when a noncredentialed scan would suffice.
+ B. No vulnerability was evidenced.
+ C. Permissions set incorrectly.
+ D. Considering the sensitivity of the data on the scanned systems.
+ E. Using agents when a server-based scan would suffice.

D is correct. The sensitivity of the data, particularly the PHI, means no exfiltration can happen.

A, B, C, and E are incorrect. A is incorrect because there is no mention of credentials. B is incorrect, while the vulnerability scan specification might have detailed the requirement for a vulnerability feed, there is no evidence this was violated. C is incorrect because permissions didn't seem to impact the success of the scan. E is incorrect because the scan was completely successful, regardless of whether agents were used.

11. Which of the following are valid arguments for using server-based vulnerability scanning instead of agent-based scanning? (Choose all that apply.)

+ A. Erratic connectivity to remote and mobile devices
+ B. Limited bandwidth
+ C. Limited personnel availability for maintenance
+ D. Occasional rogue device connecting to the network

C and D are correct. Less availability of security staff to maintain the scanning agents would be a vote in favor of server-based scanning. Also, a server-based architecture would scan the entire network space and thus be able to detect rogue devices without an agent being installed.

A and B are incorrect. A is incorrect because erratic connectivity equates to
