
robust and detailed than a walk-through, those performing certain steps are involved in simulating their response to a disaster.

The next level of testing is a parallel test. Care must be taken not to disrupt normal business operations if possible. In a parallel test, key personnel and workforce members perform the steps needed in case of a disaster. More than simulating the steps, they actually perform the steps to ensure that they can accomplish the critical business processes if the existing systems were disrupted by a disaster. It is parallel because the critical systems continue to run, and some or all of the data is also run at the alternate site. It is then possible to compare the results of the alternate methods to the critical systems to determine any gaps in capabilities.

The most robust level of testing is a full cutover test. In this test, the disaster is simulated in full. The primary system is disconnected, and the business attempts to run critical functions. This is a high-risk test, as the critical functions may fail. Only the most mature organizations and plans should attempt a full cutover test.

## SUMMARY

Moving to the cloud is a business decision. Moving to the cloud changes capital expense to operational expense and can add high availability and resiliency at a price that is attractive to businesses of all types. It also provides capabilities not available to all businesses. To achieve these benefits, a customer must have an understanding of the key infrastructure pieces of a cloud environment. The customer must also understand the shared security responsibility between the CSP and the customer. Finally, a customer must understand how to properly configure and use the cloud resources they purchase to ensure appropriate controls are in place to secure the process and data.

## Cloud Development Basics

According to the Cloud Security Alliance (CSA) and SAFECode, the development of collective responsibility is essential and challenging when building a safety conscious application development program. This effort can be broken down into these three parts:

- **Security by design:** This implies that security is part of every step in the process. Security is not a bolt-on after application release or in response to a security flaw, but part of the process from application feasibility to retirement.
- **Shared security responsibility:** The idea is that security is the responsibility of everyone from the most junior member of the team to senior management. No one says that security is not their responsibility. In fact, security is the result of individual responsibility and trust.
- **Security as a business objective:** Security is not something in addition to what we do. Instead, secure computing is what we do. Security is part of all business objectives.

Each of these basic concepts requires a clear understanding of organizational culture, security vulnerabilities, and organizational vision and goals.

### Common Pitfalls

The first pitfall is not getting senior management’s initial and ongoing support. Efforts to instill a security culture are unlikely to be successful unless senior leadership supports these efforts—through their approval and adherence to security policy as well as funding and staffing security initiatives that are part of organizational goals.

The next pitfall is failing to understand organizational culture. Even companies in the same industry have very different cultures. Building and sustaining a security culture requires careful planning that recognizes an organization’s culture and then designs program-level efforts that work within that culture. In addition, program-level efforts must be reviewed regularly to ensure that they remain aligned with business objectives and cultural realities.

Another pitfall is staffing. The size of an organization may limit the number of security experts. These experts may then serve as resources to multiple development processes rather than as a member on one team. If the organization is large, development teams may use security experts as resources or may include security experts as team members. In either situation, it can be challenging to ensure the development of security-aware applications will be consistent across the organization.

Not having a framework for secure software development will also cause difficulties. A mature organization will have a well-defined process that integrates security as part of each step. The lack of a framework or process leads to ad hoc security and does not support a security-aware organization.

## OWASP Top 10

The OWASP Top 10 (owasp.org) is a periodically updated list and features the top threats in web application security. The last version is from 2017, with the previous version in 2013. The top 10 security risks lead to a variety of issues that include data breach, data integrity, and DoS. Essentially, each item of the CIA triad can be affected by one or more of these risks. The following were the top four in 2017:

- Injection flaws, including SQL, NoSQL, OS, and LDAP injection
- Broken authentication
- Sensitive data exposure
- XML external entities

The most disturbing thing about this list is that the items on the list rarely change. Sometimes all that changes is the order. For example, numbers 1 and 2 in 2013 and numbers 1 and 2 in 2017 are the same. In four years, the top risks were unchanged. Number 3 in 2013 moved to number 7 in 2017, while number 6 became number 3.

We know what the risks are. Organizations like the CSA and OWASP publish what the risks are. As expected, the overlap between the lists is high. Now, it is the responsibility of security professionals to address these risks.

## DESCRIBE THE SECURE SOFTWARE DEVELOPMENT LIFECYCLE PROCESS

The software development lifecycle (SDLC) has been understood for several years. The SSDLC enhances the SDLC process. The SDLC has several phases. These steps are Requirements, Design, Development, Testing, Deployment, and Operations and Maintenance (O&M). In the SSDLC, these phases are enhanced to include specific security-focused steps to allow security by design. There are many resources for implementing an SSDLC. These include the Microsoft SDL and the NIST SP 800-160, Systems Security Engineering. Two resources that this section will discuss are the NIST Secure Software Development Framework and the OWASP Software Assurance Maturity Model (SAMM). This section will also explore business requirements, phases, and methodologies related to the SSDLC.

## NIST Secure Software Development Framework

Similar to the popular NIST Cybersecurity Framework (CSF), the NIST Secure Software Development Framework (SSDF) defines and describes secure software development practices (`nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.04232020.pdf`).

important part of the overall solution. Following these steps leads to a consistent and repeatable process. These phases are supported in older development methodologies such as the waterfall and spiral models as well as more modern methodologies such as agile and DevSecOps.

### APPLY THE SECURE SOFTWARE DEVELOPMENT LIFECYCLE

SSDLC is a collection of best practices focused on adding security to the standard SDLC. Applying an SSDLC process requires dedicated effort at each phase of the SDLC, from requirements gathering to deployment and maintenance. An SSDLC requires a change of mindset by the development teams, focusing on security at each phase of the project instead of just focusing on functionality.

Identifying security issues early helps reduce the risk of identifying security vulnerabilities late in the development process and minimizes the impact when these are found.

Having an SSDLC is beneficial only if it is implemented and used consistently and does not eliminate traditional security tests, such as penetration tests. Instead, it empowers developers to build secure applications from the very beginning of a project. Additionally, some standards and regulations, such as the General Data Protection Regulation (GDPR), Payment Card Industry (PCI), ISO27001, and others require security (data safeguards) to be incorporated in the development process.

### Avoid Common Vulnerabilities During Development

Common vulnerabilities and risks are listed in many places. Perhaps the most common list of risks in web-based development are the OWASP Top 10. These are updated regularly to ensure the most common risks are known to developers. By learning this list, developers can actively design and develop systems that have reduced vulnerabilities. The latest OWASP Top 10 2017 list is discussed in the “Common Cloud Vulnerabilities” section. The first five vulnerabilities are the following:

- **Injection:** SQL, NoSQL, LDAP, and OS injection errors allow the attacker to run unintended commands and access data without authorization.
- **Broken authentication:** When authentication and session management are incorrectly implemented, it leads to compromise of passwords, keys, and tokens.
- **Sensitive data exposure:** Web applications and APIs may poorly protect sensitive data, both at rest and in transit when encryption is not used.
