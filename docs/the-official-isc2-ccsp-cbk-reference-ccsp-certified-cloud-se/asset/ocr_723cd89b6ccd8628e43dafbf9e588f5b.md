important part of the overall solution. Following these steps leads to a consistent and repeatable process. These phases are supported in older development methodologies such as the waterfall and spiral models as well as more modern methodologies such as agile and DevSecOps.

# ## APPLY THE SECURE SOFTWARE DEVELOPMENT LIFECYCLE

SSDLC is a collection of best practices focused on adding security to the standard SDLC. Applying an SSDLC process requires dedicated effort at each phase of the SDLC, from requirements gathering to deployment and maintenance. An SSDLC requires a change of mindset by the development teams, focusing on security at each phase of the project instead of just focusing on functionality.

Identifying security issues early helps reduce the risk of identifying security vulnerabilities late in the development process and minimizes the impact when these are found.

Having an SSDLC is beneficial only if it is implemented and used consistently and does not eliminate traditional security tests, such as penetration tests. Instead, it empowers developers to build secure applications from the very beginning of a project. Additionally, some standards and regulations, such as the General Data Protection Regulation (GDPR), Payment Card Industry (PCI), ISO27001, and others require security (data safeguards) to be incorporated in the development process.

# ## Avoid Common Vulnerabilities During Development

Common vulnerabilities and risks are listed in many places. Perhaps the most common list of risks in web-based development are the OWASP Top 10. These are updated regularly to ensure the most common risks are known to developers. By learning this list, developers can actively design and develop systems that have reduced vulnerabilities. The latest OWASP Top 10 2017 list is discussed in the “Common Cloud Vulnerabilities” section. The first five vulnerabilities are the following:

+   - **Injection:** SQL, NoSQL, LDAP, and OS injection errors allow the attacker to run unintended commands and access data without authorization.
+   - **Broken authentication:** When authentication and session management are incorrectly implemented, it leads to compromise of passwords, keys, and tokens.
+   - **Sensitive data exposure:** Web applications and APIs may poorly protect sensitive data, both at rest and in transit when encryption is not used.