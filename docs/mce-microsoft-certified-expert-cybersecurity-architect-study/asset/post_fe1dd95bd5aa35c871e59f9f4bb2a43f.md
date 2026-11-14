
## Review Questions

- 1. In terms of security posture management, what are the three pillars? (Choose three.)
  - A. Protect
  - B. Detect
  - C. Respond
  - D. Monitor

- 2. How can Azure resources be secured so that they meet both security and compliance requirements?
  - A. Azure security benchmark
  - B. Azure blueprint
  - C. Azure Express Route
  - D. None of the above

- 3. In which approach can you improve your security posture quickly and with the least amount of effort?
  - A. Rapid Modernization Plan (RaMP)
  - B. Continuous improvement plan
  - C. Minimal viable plan
  - D. None of the above

- 4. Which of the following continuously monitors your resources, subscriptions, and organization for security concerns?
  - A. Defender for Cloud
  - B. Azure Active Directory
  - C. Azure Sentinel
  - D. None of the above

- 5. Based on the phases of which framework, can you create campaigns to remedy recommendations when evaluating your security posture?
  - A. Cloud adoption framework
  - B. Open group framework
  - C. MITRE ATT&CK framework
  - D. None of the above

- 6. Often, the IT security administrator needs the necessary privileges to expedite the remediation of recommendations. If the administrator does not have the required privileges and attempts to fix a recommendation using the Fix button, they will see that the Fix button is grayed out. What is the next step?
  - A. The workload reader has been assigned a ticket. The workload reader reviews the ticket and determines that this recommendation can be resolved quickly. As part of the change management process, the workload reader schedules and deploys the remediation.
  - B. The workload modifier has been assigned a ticket. The workload modifier reviews the ticket and determines that this recommendation can be resolved quickly. As part of the change management process, the workload modifier schedules and deploys the remediation.
  - C. The workload owner has been assigned a ticket. The workload owner reviews the ticket and determines that this recommendation can be resolved quickly. As part of the change management process, the workload owner schedules and deploys the remediation.
  - D. None of the above.

- 7. Which of the following is a Microsoft cloud security posture management solution that continuously assesses Azure Resources for achieving security hygiene and offers recommendations based on Azure Security Benchmarks?
  - A. Azure Security Center
  - B. Security Center Score
  - C. Azure Defender
  - D. None of the above

- 8. Which Microsoft Azure Services provide advanced protection for hybrid and Azure resources? By doing so, you can access additional policies, regulatory standards, and Azure Security Benchmarks that will enable you to customize your compliance analysis.
  - A. Azure Security Center
  - B. Security Center Score
  - C. Azure Defender
  - D. None of the above

- 9. An Azure landing zone results from a multisubscription Azure environment encompassing scalability, security governance, networking, and identity management. Which of the following features are enabled by Azure landing zones?
  - A. Application remediation and rationalization at enterprise-scale in Azure
  - B. Application migration, modernization, and innovation at enterprise scale in Azure
  - C. Application decommissioning at enterprise scale in Azure
  - D. None of the above

- 10. Regarding security operations design, which of the following Microsoft recommendations and best practices will you follow as a Cybersecurity Architect?
  - A. Security alerts and security logs
  - B. Security controls and vulnerability management
  - C. Shared responsibility and encryption and keys
  - D. All of the above

- 11. No one solution fits all technical environments. Despite this, a few Azure landing zone implementation options can help you meet your growing cloud portfolio's deployment and operational needs. Which two methods help to accomplish this?
  - A. Functional
  - B. Scalable
  - C. Modular
  - D. Reliable

- 12. As a Cybersecurity Architect, which of the following Microsoft recommendations, best practices, and frameworks will you review and adopt in your enterprise-grade security architecture as a foundation?
  - A. Azure landing zone
  - B. Cloud Adoption Framework
  - C. Azure landing zone accelerator
  - D. All of the above

- 13. You are considering using the Azure landing zone accelerator as a Cybersecurity Architect. Your customer is asking for a list of default tools; which of the following default tool sets is included in the Azure landing zone accelerator?
  - A. Microsoft Defender for Cloud, standard or free tier, and Microsoft Sentinel
  - B. Azure DDoS standard protection plan (optional) and Azure Firewall
  - C. Web Application Firewall (WAF) and Privileged Identity Management (PIM)
  - D. All of the above

- 14. Which of the following Azure services helps you to monitor threats and mitigate risks, with the result that context, relevance, and priority are offered to your team?
  - A. Security Center Score
  - B. Azure Defender
  - C. Threat intelligence
  - D. None of the above

- 15. Which Microsoft Azure services can help your team detect and respond to malicious cyber activity and provide context for cyber threat intelligence?
  - A. Security Center Score
  - B. Microsoft Sentinel
  - C. Threat intelligence
  - D. None of the above

- 16. As per Microsoft, there are four phases to risk management; which of the following are they?
  - A. Identification, assessment, response, monitoring, and reporting
  - B. Identification, estimation, answer, monitoring, and reporting
  - C. Identification, analyze, detect, monitoring, and reporting
  - D. Identification, assessment, response, logging, and documentation

- 17. Which threat intelligence solution from Microsoft helps to protect works by monitoring security information from your Azure resources, the network, and connected partner solutions?
  - A. Security Center Score
  - B. Microsoft Defender for Cloud
  - C. Threat intelligence
  - D. None of the above

- 18. As a Cybersecurity Architect, if you want to increase the security score of your organization, which page must you review in Defender for Cloud for remediation issues?
  - A. Secure Score recommendations
  - B. Home page
  - C. Summary
  - D. None of the above

- 19. Which Azure service can enhance the governance of Azure workloads by enforcing secure configuration using Azure Policy?
  - A. Defender for Cloud
  - B. Threat intelligence
  - C. Microsoft Sentinel
  - D. None of the above

- 20. As a Cybersecurity Architect, you must select the appropriate security capability for an upcoming risk scenario. You must provide customized remote access to your employees based on several conditions, including limiting access upon evidence of abnormal behavior. What Azure services will you likely adopt in your solution?
  - A. Azure AD conditional access
  - B. Adopt Sign-in risk-based conditional access policy
  - C. Azure WAF
  - D. Both A and B

![](img/5ab9852bf401dd309bf0f81797a91445_274_0.png)

## Chapter 6

## Define a Strategy for Securing Infrastructure

### THE MICROSOFT SC-100 EXAM OBJECTIVES COVERED IN THIS CHAPTER INCLUDE:

- Specify security baselines for server and client endpoints
- Specify security requirements for servers, including multiple platforms and operating systems
- Specify security requirements for mobile devices and clients, including endpoint protection, hardening, and configuration
- Specify requirements to secure Active Directory Domain Services
- Design a strategy to manage secrets, keys, and certificates
- Design a strategy for secure remote access
- Design a strategy for securing privileged access.

![](img/5ab9852bf401dd309bf0f81797a91445_275_0.png)

In this chapter, we will focus on understanding architecture, best practices, and how both are changing with the cloud.

Work to ensure that information systems and data are secured and that confidentiality, integrity, and availability are assured. In this chapter, you'll learn how architecture best practices can help you design a more secure environment and how cloud computing is changing the way architects perform design thinking.

To ensure that servers and client endpoints are protected, to ensure that they are continually assessed to ensure their security postures are updated, and to get enterprise-wide visibility into attack dynamics, a security strategy needs to be established.

In this chapter, you will review how to plan and deploy a security strategy across teams, establish a process for proactive and continuous evolution of a security strategy, and specify security baselines for server and client endpoints. You'll also learn how to specify security baselines for servers, including multiple platforms and operating systems, and specify security requirements for mobile devices and clients, including endpoint protection, hardening, and configuration. Finally, you'll learn how to specify requirements for securing Active Directory Domain Services; design a strategy to manage secrets, keys, and certificates; design a strategy for secure remote access; and design a strategy for securing privileged access.

## Plan and Deploy a Security Strategy Across Teams

As with the move from mainframes to desktops, your switch from enterprise servers to the cloud for security is more than a technical change. To navigate the change successfully and increase the effectiveness of your security team, you need to adopt the right mindset and expectations. Although these could be included in any security modernization plan, the rapid change in the cloud makes their adoption urgent.

A partnership between business and IT with common goals is essential. Today, security cannot adopt an arm's-length approach to being able to approve or deny changes to the environment due to fast-paced decisions and constant process evolution. To achieve productivity, reliability, and security, security teams must work closely with business and IT teams.

By integrating security earlier in the process, this partnership represents the ultimate form of shifting left, a method for resolving security issues more effectively and efficiently. To accomplish this, all involved (security, business, and IT) need to learn the cultures and
