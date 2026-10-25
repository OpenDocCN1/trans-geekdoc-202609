
- 2. Grembi, J. (2008). Secure Software Development: A Security Programmer’s Guide. Boston, MA: Course Technology.
- 3. Krutz, R., and Fry, A. (2009). The CSSLP Prep Guide: Mastering the Certified Secure Software Lifecycle Professional. Indianapolis, IN: John Wiley & Sons.
- 4. Goertzel, K., et al. (2007). “Information Assurance Technology Analysis Center (ITAC)/Data and Analysis Center for Software (DACS): Software Security Assurance State-of-the-Art Report (SOAR).” Retrieved from https://apps.dtic.mil/sti/pdfs/ADA472363.pdf
- 5. Krutz, R., and Fry, A. (2009). The CSSLP Prep Guide: Mastering the Certified Secure Software Lifecycle Professional. Indianapolis, IN: John Wiley & Sons.
- 6. Goertzel, K., et al. (2007). “Information Assurance Technology Analysis Center (ITAC)/Data and Analysis Center for Software (DACS): Software Security Assurance State-of-the-Art Report (SOAR).” Retrieved from https://apps.dtic.mil/sti/pdfs/ADA472363.pdf
- 7. Krutz, R., and Fry, A. (2009). The CSSLP Prep Guide: Mastering the Certified Secure Software Lifecycle Professional. Indianapolis, IN: John Wiley & Sons.
- 8. Goertzel, K., et al. (2007). “Information Assurance Technology Analysis Center (ITAC)/Data and Analysis Center for Software (DACS): Software Security Assurance State-of-the-Art Report (SOAR).” Retrieved from https://apps.dtic.mil/sti/pdfs/ADA472363.pdf
- 9. Krutz, R., and Fry, A. (2009). The CSSLP Prep Guide: Mastering the Certified Secure Software Lifecycle Professional. Indianapolis, IN: John Wiley & Sons.
- 10. Goertzel, K., et al. (2007). “Information Assurance Technology Analysis Center (ITAC)/Data and Analysis Center for Software (DACS): Software Security Assurance State-of-the-Art Report (SOAR).” Retrieved from https://apps.dtic.mil/sti/pdfs/ADA472363.pdf
- 11. Fink, G., and Bishop, M. (1997). “Property-Based Testing: A New Approach to Testing for Assurance.” SIGSOFT Software Engineering Notes, vol. 22, no. 4, pp. 74–80.
- 12. Goertzel, K., et al. (2008). “Enhancing the Development Life Cycle to Produce Secure Software. Version 2.0.” U.S. Department of Defense Data and Analysis Center for Software, Rome, NY. Retrieved from https://www.researchgate.net/publication/233575692_Enhancing_the_Development_Life_Cycle_to_Produce_Secure_Software
- 13. Michael, C., and Radosevich, W. (2005). “Risk-Based and Functional Security Testing.” Cigital white paper, U.S. Department of Homeland Security. Retrieved from https://us-cert.cisa.gov/bsi/articles/best-practices/security-testing/risk-based-and-functional-security-testing
- 14. Saltzer, J., and Schroeder, M. (1974). “The Protection of Information in Computer Systems.” Fourth ACM Symposium on Operating Systems Principles, October 1974.
- 15. Ibid.
- 16. Grembi, J. (2008). Secure Software Development: A Security Programmer’s Guide. Boston, MA: Course Technology.
- 17. Microsoft Corporation. (2006). “New Guidelines to Help Developers Protect Customers’ Privacy.” Retrieved from https://news.microsoft.com/2006/10/19/new-guidelines-to-help-developers-protect-customers-privacy/
- 18. Microsoft Corporation. (2012). MSDN, “SDL—Process Guidance—Appendix C: SDL Privacy Questionnaire.” Retrieved from http://msdn.microsoft.com/en-us/library/cc307393.aspx
- 19. Microsoft Corporation. (2011). “Simplified Implementation of the Microsoft SDL.” Retrieved from http://www.microsoft.com/en-us/download/details.aspx?id=12379
- 20. Microsoft Corporation. (2006). “New Guidelines to Help Developers Protect Customers’ Privacy.” Retrieved from https://news.microsoft.com/2006/10/19/new-guidelines-to-help-developers-protect-customers-privacy/
- 21. Microsoft Corporation. (2012). MSDN, “SDL—Process Guidance—Appendix C: SDL Privacy Questionnaire.” Retrieved from http://msdn.microsoft.com/en-us/library/cc307393.aspx
- 22. Microsoft Corporation. (2011). “Simplified Implementation of the Microsoft SDL.” Retrieved from http://www.microsoft.com/en-us/download/details.aspx?id=12379
- 23. Microsoft Corporation. (2012). MSDN, “SDL—Process Guidance—Appendix C: SDL Privacy Questionnaire.” Retrieved from http://msdn.microsoft.com/en-us/library/cc307393.aspx
- 24. Microsoft Corporation. (2006). “New Guidelines to Help Developers Protect Customers’ Privacy.” Retrieved from https://news.microsoft.com/2006/10/19/new-guidelines-to-help-developers-protect-customers-privacy/
- 25. Ibid.
- 26. Microsoft Corporation. (2011). “Simplified Implementation of the Microsoft SDL.” Retrieved from http://www.microsoft.com/en-us/download/details.aspx?id=12379

## Chapter 6

### Design and Development (A4): SDL Activities and Best Practices

### CHAPTER OVERVIEW

In this chapter, we will describe the activities for the design and development (A4) phase of our security development lifecycle (SDL). This phase can be mapped to the “readiness” phase in a typical software development life cycle (SDLC).

### CHAPTER TAKE-AWAYS

- Explore the practices that compose the design and development (Phase A4) of the security development lifecycle (SDL).
- Document the key success factors for completion of Phase A4.
- Create initial, draft deliverables for Phase A4 for the case study in Appendix A.
- Prepare security testing reports for the case study in Appendix A.

Figure 6.1 illustrates the steps and activities found in Phase A4 of the SDL.

In Phase A4, we start with the continuation of policy compliance analysis for this phase and then move on to describe the elements of security test case execution. Building on the proper process for security testing that should have already been created, documented, and tested, the analysis will continue until necessary tuning is identified in order to accomplish the required security level. We then describe the use of automated tools, such as static, dynamic, and fuzz test tools, to help automate and enforce security practices efficiently and effectively at a low cost. Static analysis analyzes the source code prior to compiling, provides a scalable method of security code review, and helps ensure that secure coding policies are being followed. Dynamic analysis monitors application behavior and ensures that the software functionality works as

Figure 6.1 Design and Development (A4): SDL activities and best practices.

SDLC Activities and Best Practices

Design & Development

- A4 Policy compliance analysis
- Security test case execution
- Static analysis
- Dynamic analysis
- Fuzz testing
- Manual code review
- Privacy validation and remediation

4

Readiness

Typical SDLC Phases

designed. Fuzz testing induces program failure by deliberately introducing malformed or random data to an application and can be used as an effective and low-cost way of finding potential security issues prior to release and potentially throughout the SDL process. Fuzz testing is a specialized form of dynamic analysis. By using the latest version of these automated tools, the latest known automated security analysis, vulnerabilities, and recommended protections will be identified. After these multiple automated tools have been used to quickly analyze the flaws and vulnerabilities in the software, the code is then reviewed manually, every issue validated, and the code inspected to overcome the limitations of automated tools and techniques. As part of this process, attack surface and threat model reviews will ensure that any new attack vectors that have been created by any design or implementation changes have been identified and mitigated. Finally, we discuss the need, value, and process for privacy validation and remediation to be conducted during this phase of the SDL.

### 6.1 A4 Policy Compliance Analysis

This is a continuation of the A3 policy compliance review described in the previous chapter. As you will see, we continue to perform policy compliance analysis during different phases and review it again and again. It is of paramount importance that you persist through this and not make an assumption that you have covered everything in previous iterations. You will be surprised how often things are missed during initial phases/iterations of this step.

During this phase, any policy that exists outside the domain of the SDL policy is reviewed (or reviewed again). This may include policies from outside the development organization that carry security and privacy requirements and guidelines to be adhered to when developing software or applications anywhere within the organization. Often, too, policies are updated during the development process, and new requirements are added. Thus, it is best to obtain a list of updated policies and make sure you have incorporated any additional requirements.

Corporate security and privacy policies will likely instruct designers and developers on what the security and privacy features need to be and how they must be implemented. Other policies may focus on the use of third-party and open-source software used as part of a software product or on the protections and control of source code and other intellectual property within and outside the organization. Assuming that the software security group is separate from the centralized information security group, it is important that the two groups collaborate on all policies and guidelines related to the development and post-release security support by the organization. It helps the information security group to fine-tune its policies not only for corporate security policies/practices but also for software development. It is also important to collaborate with the privacy function of your company, whether it be a centralized group or outside legal counsel. If the company identifies potential new markets, privacy policies and practices (for that particular market) may be updated.

### 6.2 Security Test Case Execution

Security testing is a time-consuming process that requires proper preparation, consistency, and coordination with all stakeholders, as well as a deep understanding of what you are actually
