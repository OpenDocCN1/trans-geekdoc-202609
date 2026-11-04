
### [25](#app02.xhtml#ch15qu-25).
In keeping with the best practices set forth by the PCI standard, how often should cybersecurity policies be reviewed, updated, and authorized?
**A.** Once
**B.** Semi-annually
**C.** Annually
**D.** Biannually

### [26](#app02.xhtml#ch15qu-26).
Which of the following is true of PCI requirements?
**A.** PCI standards augment but do not supersede legislative or regulatory requirements to protect personally identifiable information (PII) or other data elements.
**B.** PCI standards supersede legislative or regulatory requirements to protect personally identifiable information (PII) or other data elements.
**C.** PCI requirements invalidate regulatory requirements.
**D.** None of the above.

### [27](#app02.xhtml#ch15qu-27).
Which of the following is true about Level 1 merchants versus Levels 2–4 merchants?
**A.** Level 1 merchants process more than six million payment card transactions annually.
**B.** Level 1 merchants must pay a fee greater than $6 million.
**C.** Level 1 merchants must have biannual external penetration testing.
**D.** Level 1 merchants must complete a self-assessment questionnaire or pay a fine of more than $100,000.

### [28](#app02.xhtml#ch15qu-28).
PCI DSS version 3.2 incorporates DESV as an appendix primarily to merge requirements and to strengthen the importance of these requirements in establishing and maintaining ongoing cybersecurity processes. DESV is a list of resources and criteria that is designed to help service providers and merchants address key operational challenges while trying to protect payments and maintain compliance. Which of the following is not included in DESV?
**A.** Compliance program oversight
**B.** Proper scoping of an environment
**C.** Guaranteeing that proper mechanisms are used to detect and alert on failures in critical security control
**D.** The creation of public security vulnerability disclosure policies

### [29](#app02.xhtml#ch15qu-29).
Which of the following statements best describes the reason different versions of the SAQ are necessary?
**A.** The number of questions varies by payment card channel and scope of environment.
**B.** The number of questions varies by geographic location.
**C.** The number of questions varies by card brand.
**D.** The number of questions varies by dollar value of transactions.

### [30](#app02.xhtml#ch15qu-30).
Which of the following SAQs do not apply to e-commerce merchants?
**A.** SAQ-C
**B.** SAQ-B
**C.** SAQ C-VT
**D.** All of the above

## Exercises

### Exercise 15.1: Understanding PCI DSS Obligations
1. Compliance with PCI DSS is a contractual obligation. Explain how this differs from a regulatory obligation.
2. Which takes precedence—a regulatory requirement or a contractual obligation? Explain your answer.
3. Who enforces PCI compliance? How is it enforced?

### Exercise 15.2: Understanding Cardholder Liabilities
1. What should a consumer do if he or she misplaces a debit card? Why?
2. Go online to your bank’s website. Does it post instructions on how to report a lost or stolen debit or credit card? If yes, summarize their instructions. If no, call the bank and request the information be sent to you. (If you don’t have a bank account, choose a local financial institution.)
3. Explain the difference between the Fair Credit Billing Act (FCBA) and the Electronic Fund Transfer Act (EFTA).

### Exercise 15.3: Choosing an Authorized Scanning Vendor
1. PCI security scans are required for all merchants and service providers with Internet-facing IP addresses. Go online and locate three PCI Council Authorized Scanning Vendors (ASVs) that offer quarterly PCI security scans.
2. Read their service descriptions. What are the similarities and differences?
3. Recommend one of the ASVs. Explain your reasoning.

### Exercise 15.4: Understanding PIN and Chip Technologies
1. Payment cards issued in the United States store sensitive authentication information in the magnetic stripe. What are the issues associated with this configuration?
2. Payment cards issued in Europe store sensitive authentication information in an embedded microchip. What is the advantage of this configuration?
3. Certain U.S. financial institutions will provide a chip-embedded card upon request. Identify at least one card issuer who will do so. Does it charge extra for the card?

### Exercise 15.5: Identifying Merchant Compliance Validation Requirements
Complete the following table:
| **Merchant Level** || **Criteria** || **Validation Requirement** |
| --- | --- | --- |
|  || Processes fewer than 20,000 e-commerce transactions annually ||  |
| --- | --- | --- |
| Level 2 ||  ||  |
|  ||  || Required onsite annual audit |

## Projects

### Project 15.1: Applying Encryption Standards
Encryption is referenced a number of times in the PCI DSS standard. For each of the PCI requirements listed below:
1. Explain the rationale for the requirement.
2. Identify an encryption technology that can be used to satisfy the requirement.
3. Identify a commercial application that can be used to satisfy the requirement.
* **PCI DSS V3.2. 3.4.1:** If disk encryption is used (rather than file- or column-level database encryption), logical access must be managed separately and independently of native operating system authentication and access control mechanisms (for example, by not using local user account databases or general network login credentials). Decryption keys must not be associated with user accounts.
* **PCI DSS V3.2. 4.1.1:** Ensure wireless networks transmitting cardholder data or connected to the cardholder data environment are using strong encryption protocols for authentication and transmission and use industry best practices to implement strong encryption for authentication and transmission.
* **PCI DSS V3.2 6.1:** Establish a process to identify security vulnerabilities, using reputable outside sources for security vulnerability information, and assign a risk ranking (for example, “high,” “medium,” or “low”) to newly discovered security vulnerabilities.

### Project 15.2: Completing an SAQ
All major credit card companies have dedicated online portals to explain the way that they keep card member information safe and secure. The following are the links to the security portals for several major credit card companies:
* American Express: [https://merchant-channel.americanexpress.com//merchant/en_US/data-security](https://merchant-channel.americanexpress.com//merchant/en_US/data-security)
* Discover Card: [https://www.discovernetwork.com/en-us/business-resources/fraud-security/pci-rules-regulations/](https://www.discovernetwork.com/en-us/business-resources/fraud-security/pci-rules-regulations/)
* JCB Card: [www.global.jcb/en/products/security/pci-dss/](http://www.global.jcb/en/products/security/pci-dss/)
* MasterCard: [https://www.mastercard.us/en-us/merchants/safety-security/security-recommendations/site-data-protection-PCI.html](https://www.mastercard.us/en-us/merchants/safety-security/security-recommendations/site-data-protection-PCI.html)
* VISA: [https://usa.visa.com/support/small-business/security-compliance.html](https://usa.visa.com/support/small-business/security-compliance.html)
1. What are the differences and similarities among the information provided by these credit card companies? Describe how they document and address PCI DSS compliance.
2. Explain how they document requirements that apply to both merchants and service providers.
3. Does each company clearly list how anyone can report a security incident?

### Project 15.3: Reporting an Incident
Assume you are a Level 2 merchant and your organization suspects a breach of Visa cardholder information.
