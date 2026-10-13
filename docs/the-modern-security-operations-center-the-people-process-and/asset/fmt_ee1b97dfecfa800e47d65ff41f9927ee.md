
# Meeting Compliance

Meeting compliance is essential to any successful cybersecurity program. This chapter started by describing how to develop and maintain policies and procedures, which are the ingredients of an organization's process. Next, it covered how to evaluate existing policies and procedures through the use of a tabletop exercise. You then learned how standards, guidelines, and frameworks are resources that your organization can use to build or tune your policies and procedures; although following such resources is not required, they often represent industry best practices. Next, this chapter looked at how to meet compliance using audits as well as how to exceed compliance by focusing on all risk using assessments and penetration testing. Finally, this chapter surveyed several common legal and industry-based compliance requirements that might apply to your organization, depending on the nature of its operations.

Remember that compliance can only be met or not met in perspective of the entity enforcing the compliance; however, meeting compliance does not mean you are secure. Many organizations will continue to operate while they are not compliant as long as they have a plan in place to eventually become compliant, which not only increases the risk of compromise but also demonstrates a lack of focus for meeting what needs to be considered the bare minimal effort to be secure. Exceeding compliance means to not only meet compliance, but also to evaluate all risk, with a focus on actually securing the organization. Make sure to include both meeting compliance and security goals as part of how you establish your security baseline. This will result in your organization not only exceeding compliance, but also reducing the risk of a future compromise within your people, process, and technology.

[Chapter 7](#ch07.xhtml#ch07) dives into an extremely useful resource for securing your organization against attacks, known as threat intelligence.

## References

*   Archieve360 Team. (2019, February 14). Data Sovereignty and the GDPR; Do You Know Where Your Data Is? Archive360. [https://www.archive360.com/blog/data-sovereignty-and-the-gdpr-do-you-know-where-your-data-is](https://www.archive360.com/blog/data-sovereignty-and-the-gdpr-do-you-know-where-your-data-is)
*   California Association of Health facilities. (n.d.). Discussion Based Tabletop Exercise: Design Template & Documentation. CAHF. [http://www.ndltca.org/image/cache/Tabletop_Exercise_Template.pdf](http://www.ndltca.org/image/cache/Tabletop_Exercise_Template.pdf)
*   CIS. (2018, October 18). Tabletop Exercises: Six Scenarios to Help Prepare Your Cybersecurity Team. CIS. [https://www.cisecurity.org/wp-content/uploads/2018/10/Six-tabletop-exercises-FINAL.pdf](https://www.cisecurity.org/wp-content/uploads/2018/10/Six-tabletop-exercises-FINAL.pdf)
*   FIRST.org, Inc. (2019, November). Computer Security Incident Response Team (CSIRT) Services Framework Version 2.1.0. FIRST.org, Inc. [https://www.first.org/standards/frameworks/csirts/FIRST_CSIRT_Services_Framework_v2.1.0.pdf](https://www.first.org/standards/frameworks/csirts/FIRST_CSIRT_Services_Framework_v2.1.0.pdf)
*   Gitanjali, M. (2018, May 2). A Security Assessment Template for Small Businesses: Evaluate Your IT Security. GetApp. [https://lab.getapp.com/security-assessment-template-for-small-businesses/](https://lab.getapp.com/security-assessment-template-for-small-businesses/)
*   LaBoissonnière, L. (2018, February 2). Be Diligent: 5 Practical Steps to Enforceable Workplace Policies. McInnes Cooper. [https://www.mcinnescooper.com/publications/be-diligent-5-practical-steps-to-enforceable-workplace-policies/](https://www.mcinnescooper.com/publications/be-diligent-5-practical-steps-to-enforceable-workplace-policies/)
*   National Institute of Standards and Technology. (2018, April 16) Framework for Improving Critical Infrastructure Cybersecurity, Version 1.1. NIST. [https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.04162018.pdf](https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.04162018.pdf)
*   North American Electric Reliability Corporation. Critical Infrastructure Protection (CIP) Standards. NERC. [https://www.nerc.com/pa/Stand/Pages/CIPStandards.aspx](https://www.nerc.com/pa/Stand/Pages/CIPStandards.aspx)
*   Oltsik, J. (2018, January 11). Research Suggests Cybersecurity Skills Shortage Is Getting Worse. CSO. [https://www.csoonline.com/article/3247708/security/research-suggests-cybersecurity-skills-shortage-is-getting-worse.html](https://www.csoonline.com/article/3247708/security/research-suggests-cybersecurity-skills-shortage-is-getting-worse.html)
*   SANS. (2020). Security Policy Templates. SANS. [https://www.sans.org/information-security-policy/](https://www.sans.org/information-security-policy/)
*   Vlallno, B. (2014, October 27). 6 Tips for Effective Security Tabletop Testing. CSO. [https://www.csoonline.com/article/2838365/planning-for-a-security-emergency-from-the-tabletop-down.html](https://www.csoonline.com/article/2838365/planning-for-a-security-emergency-from-the-tabletop-down.html)

# Chapter 7

# Threat Intelligence

> *An intelligent hell would be better than a stupid paradise.*
>
> —Victor Hugo

Knowledge is one of the most powerful currencies. Some might even say it's the ultimate currency. How you react to a situation depends on how much knowledge you have of the situation. Imagine the difference between having knowledge that the stock market is going to crash before it happens versus having no knowledge until the event is well under way. If you're heavily invested in stocks, that piece of information could make the difference between securing your wealth and ending up in bankruptcy. A similar comparison can be applied to the world of cybersecurity. Having knowledge of a threat allows you to prepare a response instead of reacting to the impact of the threat, which at that point is too late. This is why threat intelligence has become and will continue to be a critical component of a successful security operations center.

This chapter dives into the world of threat intelligence. First, you will learn about general threat data and how it can be converted into threat intelligence. You will then learn about the different types of threat intelligence and how each type can be used within your SOC. This chapter organizes the different types of threat intelligence into four categories:

*   Strategic threat intelligence
*   Tactical threat intelligence
*   Operational threat intelligence
*   Technical threat intelligence

Intelligence is more than the data you collect. Intelligence is what you do with that data or what awareness it provides. That is why the term *actionable intelligence* is used often when describing cybersecurity threat intelligence data. Actionable intelligence provides guidance for choosing the best actions. You will learn how to leverage external resources for intelligence, including how to evaluate the return on investment. You will find that all threat intelligence data isn't going to benefit your SOC and, in some cases, adding the wrong data can overwhelm your SOC analysts and negatively impact your security tools.

Let's start this chapter with an overview of what threat intelligence is and how to plan for a threat intelligence project.

> **Note**
>
> Every SOC practice eventually incorporates threat intelligence as it works toward maturing its services. I am a firm believer that threat intelligence is a necessary ingredient for improving how a SOC makes decisions and, if properly used, can dramatically improve how and when threats are detected.

## Threat Intelligence Overview
