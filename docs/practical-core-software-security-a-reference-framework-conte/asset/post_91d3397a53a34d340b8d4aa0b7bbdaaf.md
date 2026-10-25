
![](img/a54ed04827050a271316d34985425127_179_0.png)

Figure 7.2 Typical vulnerability scan process.

You should use as many vulnerability scanners as possible across the stack. Web application scanning alone will not be sufficient, as the software stack (operating system, web servers, application servers, database servers) can also have vulnerabilities that need to be remediated. Vulnerability scanning should include external scans, internal scans and authenticated scans of the entire stack (especially in a cloud environment). External scans are primarily targeted at exploring security issues that can be found outside the firewall. Since a firewall often restricts ports, these scans may be of only limited utility at times; however, they can still be very valuable because findings from external scans are often also quite accessible to attackers. Internal scans are executed from inside firewalls, and, thus, findings are not restricted to ports everyone can see from outside firewalls. Internal scans allow us to identify security issues that an attacker or malicious insider can exploit if he or she gets inside the network (and is not outside restricted by firewalls). Authenticated scans are most comprehensive in that they not only identify issues covered by external and internal scans but also identify missing patches and reduce false positives. Authenticated scans require software to log on to a system to scan it, however, and thus are most intrusive.

Earlier in the process, security architecture should have laid out configuration requirements for the software stack to harden the stack and remove attack surfaces. Configuration guidelines exist in various forms, including hardening standards for operating systems and other software on which the product will be deployed. For example, off-the-shelf operating systems will have many unnecessary services and configurations that increase the attack surface on the stack. Hardening guidelines can be instrumental in reducing risk from the default configuration.

In addition to vulnerability scanning, the security configuration should also be validated to ensure that the stack itself is hardened. An ideal solution is to create a “hardened image” of the stack itself and stamp it with security approval. Any variances from this image should raise a red flag when the product is finally deployed in the operational environment.

## 7.3 Code-Assisted Penetration Testing

Code-assisted penetration testing is a white-box security analysis of a software system to simulate the actions of a hacker, with the objective of uncovering potential vulnerabilities resulting from coding errors, system configuration faults, or other operational deployment weaknesses. It is also used to validate whether code implementation follows the intended design, to validate implemented security functionality, and to uncover exploitable vulnerabilities. White-box testing requires knowledge of how the system is implemented in order to ensure the robustness of the software product and its associated systems against intended and unintended software behavior, including malicious attacks as well as regular software failures. The white-box test assessors must be skilled and seasoned security professionals who have the background and knowledge as to what makes software secure or insecure, how to think like an attacker, and how to use different testing tools and techniques to simulate the actions of a hacker. Penetration tests are typically performed in conjunction with automated and manual code reviews and require the analysis of data flow, control flow, information flow, coding practices, and exception and error handling within the software and its associated systems.

To successfully conduct a white-box security test of the code being developed and the systems with which it will be interacting, three basic requirements must be satisfied holistically, not independent of each other. The assessor(s)/tester(s) must:

- 1. Have access to and be able to comprehend and analyze available design documentation, source code, and other relevant development artifacts, and have the background and knowledge of what makes software secure
- 2. Be able to think like an attacker and have the ability to create tests that exploit software
- 3. Have knowledge and experience with the different tools and techniques available for white-box testing and the ability to think “outside the box” or unconventionally, as an adversary would use the same tools and techniques.

Independence is a key element and requirement for penetration testing, which is why engaging a third-party external security firm to conduct a security review and/or penetration testing should always be considered. This provides the benefit of both an “outside set of eyes” and independence and should be mandatory for all projects that are considered to be a high business risk. An outside view and perspective will help identify the types of vulnerabilities that other processes are not preventing and make the current state of security maturity clear to all. The third party should be afforded access to the threat models and architectural diagrams created during the SDL to determine priorities, test, and attack the software as a hacker might. The level of scrutiny will always be predicated on the available budget, since these types of firms typically charge a premium for their services. Any security issues or vulnerabilities identified during penetration testing must be addressed and resolved before the project is approved for release and shipping.

- **(1) Assess**
  - Identify which software modules to focus on for penetration testing efforts.
  - A budget is developed and approved for outside penetration testing.
  - Determine the necessary skills and criteria for potential vendors.

- **(2) Identify**
  - Targets are selected for the penetration test(s).
  - Vendors are selected to respond to the Request for Proposal (RFP).

- **(3) Evaluate & Plan**
  - The RFP describing the testing to be performed is issued.
  - Vendor responses reviewed, and vendor selection is made.
  - Dedicated testing environment resembling production operating conditions is selected or developed.

- **(4) Deploy**
  - Execute the penetration test.
  - Perform any recommended remediation.

Figure 7.3 The four-phase process of penetration testing.

To achieve the minimum requirements for penetration testing, the four-phase process shown in Figure 7.3 should be followed.

The penetration test report is the final deliverable of the penetration test. The main body of the report should focus on what data was compromised and how, and provide the customer with the actual method of attack and exploit, along with the value of the data exploited. If needed or desired by the SDL and development teams, possible solutions can be included in the report as well. The detailed listing of the vulnerabilities that had attempted exploits and the false positives or vulnerabilities that were exploited but resulted in no data loss should be included in an appendix rather than the main body of the report in order to keep the primary part of this report succinct and to the point.

The long list of possible exposures typically generated from a vulnerability scan should be in the vulnerability scan report or readout and not part of the final penetration report. As mentioned in the previous section, the purpose of each activity and its results are different.

Security has been in the limelight for all of the wrong reasons of late, given that some very well-known companies have been attacked, and some popular products have been in the news for having security holes. This has resulted in customers (whether for traditional software or SaaS/cloud service) asking that an enterprise demonstrate and prove its security posture for products/services they are purchasing. At this point in the release cycle, it is a good idea to get together with your sales and marketing team and create a framework for discussing security with customers. The group should consider creating a security whitepaper that can be given to customers (and potential customers) during the sales cycle. They should also consider setting up to customers an annual review cycle for whitepapers as new issues are identified and hopefully remediated. Customers often need to demonstrate security and compliance within their own company, and thus will reach out to the product company for information about the security posture of the product or service you are selling. In our experience, such requests often come in the form of requests for penetration test results or detailed security findings reports on a regular basis (quarterly or annually). Especially in a cloud or SaaS environment, it may not be feasible to either allow customers to perform their penetration tests or to share each and every security finding with them. It is not feasible, however, to align the remediation service-level agreements (SLAs) of all your customers. In a nutshell, a framework within which to discuss security with your customers is very important if you do not want them to be setting or disrupting your own security priorities.

## 7.4 Open-Source Licensing Review

Although open-source software is free and it increases innovation, efficiency, and competitiveness for software product development, it must also be managed as an asset, the license obligations observed, and it must be as secure as internally developed software standards and requirements require. These sometimes unique and complex license and business risks can delay, and potentially prevent, software deployment or shipment if not properly managed. It is essential to be in compliance with applicable open-source requirements to avoid costly and time-consuming litigation. The two primary areas that need to be of concern for those managing an SDL in which open-source software is used as part of the product or solution are license compliance and security.

- 1. Open-source software license compliance. Noncompliance with open-source software licensing requirements can result in costly and time-consuming litigation, court time, copyright infringement, public press exposure, bad publicity, and negative risk to the noncompliant organization’s reputation and business relationships. Mismanagement and noncompliance with open-source licenses may also result in the difficulty or inability to provide software product support, the delay of current release and ship dates, or the stoppage of orders currently scheduled to ship.

- 2. Open-source software security. SDL and development teams, as well as their executive sponsors, need to be aware of and understand vulnerabilities associated with open-source software code to be used in their own software product. As with the software being developed in-house, all vulnerabilities known to the open-source and software security community must be identified, assessed, and mitigated throughout the SDL process and include the same threat modeling, architectural security and privacy review, and risk assessment rigor as the code being developed in-house.

To put this into perspective, a few examples of the consequences of not properly managing open-source software license or security are given below.
