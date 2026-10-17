
but may lack the expertise in detecting threats. Using the same criteria previously mentioned for determining the most important needs in an outsourced relationship, companies should evaluate the breadth and, importantly, the depth of the services provided by each of the vendor candidates.

No matter which MSSP is chosen, it is important to remember that the vendor is providing baseline services to multiple clients. It is unlikely that a third party will have the same intimate knowledge of your corporate network, the company’s business processes and strategies, or who are all the key stakeholders across IT and the business. Even with an outsourced model, the CISO still needs to build a capable, internal team of security professionals to investigate alerts, translate them into realistic threats to your organization, and remediate them. Much like a cloud outsourcing model, security cannot be fully provided to a third party with the expectation that a full-service security program will follow. A strong relationship between the service provider and the client is vital. Ensuring that service levels are agreed upon, open communication between the two entities is well established, and actionable metrics/alerts are provided to the client helps in this assurance. This relationship, unlike many others, is truly an extension of the internal team.

MSSPs are a considerable target for adversaries with the hope that in breaching the provider’s infrastructure, the threat actor may be able to traverse to client networks. Significant resources from Nation-state adversaries are focused on these suppliers with this goal in mind and while cyber security focused MSSPs deploy significant controls to protect their offering, the increased targeting is a consideration to be weighed in deciding on which partner a company should engage to perform their monitoring services.

Cyber security vendors have expanded their portfolio of services that extend well beyond detection. As mentioned earlier, there may be cases in which highly experienced outsourced partners can be a good alternative to building these non-monitoring, highly technical services within your company. But as with most things, an argument can be made where building internal capabilities may make good financial sense, particularly for large corporations. As I write this, I have seen hourly rates for vendors providing deep security analysis services ranging from $300 to $600 (U.S. dollars). If a large enterprise has a high demand for these niche services on an ongoing basis, the CISO could rightly argue that they are able to do it at an internal rate of $70–$150 per hour, fully burdened, along with some technology additions, and potentially some specialized training for the security staff. Speaking of the security employees, this deep and challenging work is what they want to do – it is why they entered the field.

CISOs require assistance in carrying out their duties, and security vendors are an important part of building a holistic security program. At the same time, the security product/service industry has saturated executives with

## Chapter 10: Security service management

It may be quite easy to conjure up an image of a corporate cyber security team and the way they carry out their important duties each day. If the stereotypical image comes to mind, no doubt they are assembled somewhere (either virtually or in an office) secretly performing “behind the curtain” functions that few outside of the team are aware of. While this is an exaggerated view (many security teams have evolved from this typecast), delivering cyber security services is indeed a novel concept that isn’t easily understood. Promoting the team as an enabler of the business and showcasing the services that are provided to the enterprise are great ways to shine light on this functional area that historically may have operated in the dark. We’ll discuss this more in the chapter on security awareness. For our purposes in this chapter, we’ll review the importance of service delivery for an information security organization and what it means for those outside the cyber team.

Directors should seek out details in the security strategy that highlight the operating capabilities for the cyber security organization. A good way to demonstrate these capabilities is through a strong security service management program created by the CISO and their team. The program highlights its activities and explains the delivery and ongoing operations for each of its capabilities. In doing so, employees outside of the security organization can better understand how the security organization supports them. What follows are some general tips and guidelines that have proven successful for me across different companies. Remember that this is general information to enable the director to ask questions of the plan for his or her company and should not be seen as a complete service management program with all the elements that a professional in the service management field could provide. We’ll leave that to those experts. What follows is more than enough though to show the importance of a basic service management program for cyber security and its benefits.

### Security Service Towers

Leveraging the organizational structure of the security organization, each service tower consists of several buckets of service areas. For example, if one of the teams is security operations, potential buckets could include vulnerability management, endpoint security, monitoring/detection, server/system security, cloud security, application security, OT/IoT security, threat intelligence, and penetration testing, to name a few possible examples. Another team may be focused on governance, risk, and compliance (GRC) and its buckets may include security awareness, risk management, policy management, metrics, third-party risk, and possibly compliance. How many service towers exist is dependent on the company, but the above areas serve as a good sample for our purposes here. When assembled, the service towers may look as in Figure 10.1.

| Security Operations | Governance, Risk, & Compliance | Identity Access Mgmt |
|---|---|---|
| Vulnerability Management<br>Endpoint Security | Policy Management<br>Security Awareness | Multi-Factor Authentication<br>Privileged Access |
| Server/System Security<br>Monitoring & Detection | Compliance<br>Risk Management | Federation & Single Sign-On<br>Identity Access Lifecycle |
| Cloud Security<br>Application Security | — | ERP Security<br>Architecture Services |
| OT/IoT Security<br>Threat Intelligence | — | Data Loss Prevention<br>IAM Governance |

*Figure 10.1* Security service towers.

Each block within each service tower represents a bucket of services, with each block containing five to ten discrete services related to the service area. For example, under GRC there is a block called “security awareness,” and within that block contains individual services such as role-based training, annual security compliance training, security awareness articles, internal phishing campaigns, reporting, as well as other potential services. It is important to capture as many of the services the team provides and after identifying all the services within all the buckets across the different security towers, an information security service catalog begins to emerge.

The next step is to create a work breakdown structure (WBS) that breaks down the enormous work areas performed by the cyber security team into manageable increments. A standard numbering system is sufficient to group smaller services with the larger service buckets within the security service tower. For example:

- 1.0 **GRC Services**
  - 1.1 Security Awareness
    - 1.1.1 Role-Based Training
    - 1.1.2 Annual Security Compliance Training
    - 1.1.3 Security Awareness Articles
    - 1.1.4 Internal Phishing Campaigns
    - 1.1.5 Metrics and Reporting
  - 1.2 Policy Management
    - 1.2.1 Policy Development
    - 1.2.2 Policy Approval
    - 1.2.3 Exception Process
    - 1.2.4 Annual Policy Review
  - 1.3 Compliance
    - 1.3.1 PCI Compliance
      - 1.3.1.1 Evidence Collection
      - 1.3.1.2 Assessment Facilitation
      - 1.3.1.3 Delivery and Reporting
    - 1.3.2 Sarbanes-Oxley Compliance
      - 1.3.2.1 Evidence Collection
      - 1.3.2.2 Facilitation with Third-Party Auditors
      - 1.3.2.3 Reporting
  - 1.4 Risk Management
    - 1.4.1 Third-Party Risk Evaluations
    - 1.4.2 Enterprise Risk Management Support
    - 1.4.3 Risk Register Maintenance

With the foundations in place, the service catalog is ready to be built out through the creation of service descriptions for each discrete service. Although they could vary depending on need, potential elements of the service descriptions could include the following.

### SERVICE NAME

As it suggests, this is the name of the service. Because the service catalog is geared for non-security personnel, industry or very technical terms should be avoided. For example, a service name should not be Static Application Security Testing. Instead, leveraging a simple descriptor such as Software Security Testing may be easier for readers to understand. Within the service description, any differentiation between the specific types of software testing can be explained.

### SHORT DESCRIPTION

This is a quick reference for the user to understand a summary of the service. Containing a few sentences, the short description provides an executive overview of the service being documented.

### LONG DESCRIPTION

Expanding on the short description, this section highlights more specifics related to the service, what is included, and a brief highlight of the steps involved in providing the service. Keeping with the security awareness
