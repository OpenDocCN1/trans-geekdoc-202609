

| Design and Development (A4): SDL Activities and Best Practices | Percent compliance with company policies (updated) - Percent of compliance in Phase 3 versus Phase 4 |
| --- | --- |
| | Number of lines of code tested effectively with static analysis tools |
| | Number of security defects found through static analysis tools |
| | Number of high-risk defects found through static analysis tools |
| | Defect density (security issues per 1000 lines of code) |
| | Number and types of security issues found through static analysis, dynamic analysis, manual code review, penetration testing, and fuzzing - Overlap of security issues found through different types of testing - Comparison of severity of findings from different types of testing - Mapping of findings to threats/risks identified earlier |
| | Number of security findings remediated - Severity of findings - Time spent (approximate) in hours to remediate findings |
| | Number, types, and severity of findings outstanding |
| | Percentage compliance with the security test plan |
| | Number of security test cases executed - Number of findings from security test case execution - Percent of retests executed |
| Ship (A5): SDL Activities and Best Practices | Percent compliance with company policies (updated) - Percent of compliance in Phase 5 versus Phase 4 |
| | Number, type, and severity of security issues found through vulnerability scanning and penetration testing - Overlap of security issues found through different types of testing - Comparison of severity of findings from different types of testing - Mapping of findings to threats/risks identified earlier |
| | Number of security findings remediated (updated) - Severity of findings - Time spent (approximate) in hours to remediate findings |
| | Number, types, and severity of findings outstanding (updated) |
| | Percentage compliance with security and privacy requirements |
| Post-Release Support (PRSA1–5) | Time in hours to respond to externally disclosed security vulnerabilities |
| | Monthly FTE (full-time employee) hours required for the external disclosure process |
| | Number of security findings (ranked by severity) after the product has been released |
| | Number of customer-reported security issues per month |
| | Number of customer-reported security issues not identified during any SDL activities |

a step-by-step process for software security that is relevant to today’s technical, operational, business, and development environments. We have focused on what humans can do to control and manage a secure software development process in the form of best practices and metrics. Although security is not a natural component of the way industry has been building software in recent years, the authors believe that security improvements to development processes are possible, practical, and essential. We believe that the software security best practices and model presented in this book will make this clear to all who read the book, including executives, managers, practitioners, and students.

When it comes to cyber security, we believe it is all about the software and whether it is secure or not. You can have the world’s best client, host, and network security, including encrypted transmission and storage of data, but if software application vulnerabilities exist and can be exploited, your defense-in-depth security approach has just become a speed bump to the inevitable. As the old adage goes, you are only as good as your weakest link, and in today’s world, that is still the software; and software permeates everything we do, from defense to medicine, industry, banking, agricultural, transportation, and how we manage and live our lives. This is a very serious and daunting vulnerability. You only have to look at how many years the same software vulnerabilities have remained on the CVE Top 25 or OWASP and SANS Top 25 to realize that organizations are still not taking software security seriously. Even worse, experienced and professional adversaries will target vulnerable software and don’t necessarily need it to be Internet-enabled to be at risk—that just makes the exploitation easier. But software is still the primary target because if you can own the software, you can own the data and the processes that it controls. In today’s world, this can result in life-threatening and serious local, regional, and global consequences. Throughout this book, we have described the SDL best practices and metrics to optimize the development, management, and growth of a secure software development life cycle (SDLC) and program to maximize the mitigation of this type of risk. Managing software security is an area that the authors live in on a daily basis, and this book is based on our real-world experiences. We have worked with Fortune 500 companies and have often seen examples of the breakdown of security development lifecycle (SDL) practices. In this book, we have taken an experience-based approach to applying components of the best available SDL models in dealing with the problems described above in the form of an SDL software security best practices model and framework. Most important, our SDL best practices model has been mapped to the standard model for an SDLC, explaining how you can use this to build and manage a mature SDL program. Although security issues will always exist, the purpose of this book has been to teach you how to maximize an organization’s ability to minimize vulnerabilities in your software products before they are released or deployed, by building security into the development process. We hope you enjoyed reading this book as much as we have writing it, as we are passionate about our efforts to help alleviate the risk of vulnerable software in the world at large and, specifically, in our readers’ organizations.

## References

- 1. Trapani, K. (2018, May 22). What Is AGILE?—What Is SCRUM?—Agile FAQ's. Retrieved from https://www.cprime.com/resources/what-is-agile-what-is-scrum/
- 2. Vashisht, S. (2012, August 3). “Agile vs DevOps: Demystifying DevOps.” Retrieved from http://www.agilebuddha.com/agile/demystifying-devops/
- 3. Maccherone, L. (2017, March 19). “DevSecOps Cycle” [Diagram]. Retrieved from https://twitter.com/lmaccherone/status/843647960797888512
- 4. REST API Tutorial. (2017, June 5). “What Is REST: Learn to Create Timeless RESTful APIs.” Retrieved from https://restfulapi.net/
- 5. Epstein, J. (2009, June 18). “Jeremy Epstein on the Value of a Maturity Model.” Retrieved January 7, 2022, from https://www.opensamm.org/2009/06/jeremy-epstein-on-the-value-of-a-maturity-model/
- 6. OWASP. (2017, April 14). “OWASP SAMM v1.5 Released.” Retrieved January 7, 2022, from https://www.opensamm.org/2017/04/owasp-samm-v1-5-released/
- 7. Migues, S., Steven, J., and Ware, M. (2021, September). “Building Security in Maturity Model.” Retrieved January 13, 2022, from https://www.bsimm.com/
- 8. SANS Institute. (2021, December 8). “Practical Risk Analysis and Threat Modeling Spreadsheet.” Retrieved January 10, 2022, from https://www.sans.org/blog/practical-risk-analysis-and-threat-modeling-spreadsheet/
- 9. “Security/OSSA-Metrics.” (n.d.). Retrieved from https://wiki.openstack.org/wiki/Security/OSSA-Metrics#DREAD
- 10. MITRE Corporation (Ed.). (n.d.). “MITRE ATT&CK.” Retrieved January 6, 2022, from https://attack.mitre.org/
- 11. Ibid.

![](img/a54ed04827050a271316d34985425127_256_0.png)

## Taylor & Francis

Taylor & Francis Group

http://taylorandfrancis.com

## Appendix A

### Case Study for Chapters 3 Through 8 Exercises

The following case study forms the basis for the exercises you'll find in Chapters 3 through 8.

Revvin' Engines Auto Parts is a statewide retail and commercial supplier of auto parts throughout Illinois. They have a robust business from walk-in traffic and from their auto repair shops close to their retail locations. Six months ago, the owners decided it was time to open their catalog of items they sell to customers across the United States.

They hired a local Schaumburg software development company to design an Internet E-commerce site, implement an online shopping cart, and permit credit card payments for online orders. They even slapped together a mobile app for both iOS® and Android® devices.

Once the system was implemented, Revvin' Engines decided it was time to bring in a new staff of development team members to take over the applications for enhancements and maintenance. They hired three local people and two remote employees for the new team:

- 2 C# programmers for .NET Core
- 1 tester
- 1 designer
- 1 lead engineer who handles the architecture and engineering of the application and the corresponding system.

The team is relatively new, comprising people who have not worked together before and who had no direct experience beyond programming courses they completed and some freelance application development.

Future plans for the applications include expansion of capabilities and rewriting the applications as cloud native, composed of a series of microservices and application programming interfaces (APIs) using web services based on representational state transfer (REST).

