
## Microsoft 365 Defender's Threat Intelligence

To assist incident response teams in investigating and remediating threats, Defender for Cloud provides threat intelligence reports. The threat intelligence report includes the following information:

- An attacker's identity or affiliations (if any)
- Objectives of attackers
- Information about current and historical attack campaigns (if available)
- Tools, techniques, and tactics used by attackers
- URLs and file hashes associated with indicators of compromise
- Identifying the risks to your Azure resources by taking a look at the victimology of your industry and geographical location
- Information on mitigation and remediation

In the Microsoft 365 Defender, threat investigation and response capabilities allow your organization's security team to protect its users from email- or file-based attacks. These insights can help your security team protect users. With these capabilities, you can monitor signals and gather data from multiple sources, including user activity, authentication, email, compromised PCs, and security incidents. Business decision-makers and your security operations team can use this information to understand and respond to threats against your organization and protect your intellectual property.

Microsoft 365 Defender includes a set of tools and response workflows for investigating threats.

- Explorer
- Incidents
- Attack simulation training
- Automated investigation and response

![](img/5ab9852bf401dd309bf0f81797a91445_132_0.png)

A workflow that integrates apps, data, services, and systems can be analyzed and run using Azure Monitor.

You can use Microsoft Sentinel to evaluate threat indicators in an Azure environment to detect malicious activity and inform security investigators about what to do.

To monitor security incidents, you can use other Azure services, such as Activity Logs, Azure AD Reporting, and Network Security Group flow logs.

## Summary

This chapter explored several topics related to the foundation of security operation centers and various strategies required to be adopted in your organization's security operation center.

As your organization moves to Microsoft Azure, you must define and deploy a SOC team that is enabled with the appropriate SOC strategy, resources, tools, and processes to manage and respond to cybersecurity incidents.

In this chapter, you learned about developing security operations for hybrid and multi-cloud environments, designing logging and auditing security strategies, and developing security operations for hybrid and multi-cloud environments. Develop an approach to security information and event management and security orchestration, automation, and response to evaluate security workflows, review security strategies to manage incidents, evaluate security operations for technical threat intelligence, and monitor sources to identify threats and mitigations.

## Exam Essentials

### Understand the security operations strategy.
Zero Trust security frameworks are characterized by a significant shift from trust-by-default to trust-by-exception as one of their considerable changes in perspectives. It is, however, still necessary to establish trust once it is required to prove the trustworthiness of a request at a point in time, you must select a means of attesting to its reliability. It is necessary to gain visibility into the activities associated with the request to perform this attestation.

### Understand the method to develop a logging and auditing security strategy.
Security operations teams are responsible for identifying, prioritizing, and triaging potential threats. It reduces the time it takes to resolve real incidents by reducing false positives and concentrating on real attacks. Adopt the MITRE ATT&CK framework.

### Understand the method to develop security operations for hybrid and multi-cloud environments.
Managing the hardware and infrastructure hosting the application is no longer the responsibility of the operations team due to the cloud. Operating a successful cloud application is still dependent on operations. The operations team is responsible for deploying, monitoring, escalating, responding to incidents, and performing security audits.

To ensure the application gives the operations team the data and insight they need, incorporate robust logging and tracing into its design and planning.

### Understand the method to develop SIEM and the SOAR method.
Through standard governance and operations management practices, unified operations consistently maintain one set of tools and processes to manage each cloud provider.

To use proactive and reactive detection tactics to manage threats, you should have a central console that allows SOC administrators to detect, investigate, remediate, and hunt threats; use threat intelligence; understand known vulnerabilities; rely on threat experts; and block threats across any of the six pillars. A seamless experience that increases the effectiveness of the SOC analyst is achieved when the tools required to support these phases are converted into a single workflow.

### Know the method to evaluate security workflows.
Microsoft recommends that security practitioners automate as many steps of those procedures as possible. These processes can include notifying relevant stakeholders, launching a change management process, and applying specific remediation steps. By automating the processes, you reduce overhead and improve your security by ensuring the steps are done in a timely, consistent manner and according to your predefined requirements.

### Review security strategies for incident management.
An incident of security occurs when customer data or personal information is destroyed, lost, altered, or accessed unauthorized due to a security breach. Security incidents include, for example, unauthorized access to infrastructure and exfiltration of customer data. Compliance events that do not affect confidentiality, integrity, or availability of customer data aren't considered security incidents.

A security incident should be investigated, and lessons learned implemented in conjunction with the security response team to prevent future incidents. Continuous improvement is essential for effective and efficient incident response programs.

### Know the method to evaluate security operations for technical threat intelligence.
Threat intelligence teams support all other functions such as security analysts in large organizations (for example, through threat intelligence platforms).

It takes a large, diverse set of data and the ability to apply it to your processes and tools to succeed at threat intelligence, and Microsoft does both. Microsoft collects data from various sources to ensure that our customers’ data is used only in ways they have agreed to. It passes through a strict privacy/compliance boundary.

### Know to monitor sources for insights on threats and mitigations.
As a result of accessing various signals across the Microsoft network, organizations use cyberthreat intelligence to gather information. It can be gathered from many different sources. It includes open-source data feeds, threat intelligence–sharing communities, commercial intelligence feeds, and local intelligence from security investigations. The Microsoft Intelligent Security Graph receives hundreds of gigabytes of data every second.

## Review Questions

- 1. Which of the following allows you to select, operate, maintain, and continually analyze threat data to find ways to improve the organization's security posture?
  - A. Security operations center
  - B. Incident management
  - C. Problem management
  - D. Forensic team

- 2. In general, traditional environments categorize applicable SOC activities and choose those relevant to the cloud environment for which of the following choices?
  - A. Preparation, planning, and prevention
  - B. Monitoring, detection, and response
  - C. Recovery, refinement, and compliance
  - D. All of the above

- 3. Microsoft recommends the SOC team be enabled with tools that support which type of detection?
  - A. Reactive and proactive
  - B. Reactive-only tools
  - C. Proactive-only tools
  - D. None of the above

- 4. As a Microsoft Cybersecurity Architect, you will need to consider a Microsoft security operations strategy with which of the following requirements?
  - A. Multiple engineering teams working in Microsoft Azure.
  - B. Multiple subscriptions to manage and secure.
  - C. Regulatory requirements must be enforced.
  - D. All of the above.

- 5. As a Microsoft Cybersecurity Architect, you will need to consider SOC functions in line with Microsoft definitions; which of the following will you consider in your SOC strategy?
  - A. Incident management, incident preparation, and threat intelligence
  - B. Change management, change preparation, and threat management
  - C. Incident management, change preparation, and threat intelligence
  - D. None of above
