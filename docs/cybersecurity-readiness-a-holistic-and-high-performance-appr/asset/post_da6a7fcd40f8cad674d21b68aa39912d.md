
Organizations that are seriously committed to proactively gather and act on operational, tactical, and strategic security intelligence have in place a Security Operations Center (SOC). The SOC team is charged with gathering threat intelligence data from various sources and acting on them. They are expected to keep the organization informed of threat urgency levels and guide appropriate action. This group is also entrusted with the responsibility of deciding on external service providers who would aid intelligence gathering, vulnerability testing, and defense activities. The selection process must be rigorous and service provider performance closely monitored and regularly reviewed.78

With the advancements in artificial intelligence and big data analytics, today's threat detection and response (TDR) solutions are quite sophisticated. By monitoring and mining network traffic and user behavior data, these tools are able to detect anomalies and abnormal patterns (which often go undetected by firewalls and antivirus software) and raise an alarm. When the automatic alert is triggered, the responsible security team personnel are able to evaluate the seriousness of the threat, eliminate false positives, and respond. The nature of response can range from conducting more in-depth forensic analysis to banning malicious files, quarantining affected devices, and stopping malicious processes.79

Splunk's on-premise and cloud-based Security Information and Event Management (SIEM) platform80 is representative of the state-of-the-art software solutions that leverage structured and unstructured data to offer security monitoring, advanced threat detection, incident investigation and response, and other security operation services.

Considering the plethora of sophisticated detection tools, an organization must have a clear and deliberate plan on what to use and how to create an integrated technology architecture to optimize detection effectiveness.81 In the absence of a holistic plan, organizations end up with numerous and disparate tools and managing them becomes a challenge. Often the functionalities are overlapping with each tool offering certain types of detection capabilities, which range from endpoint detection and response, to network traffic analysis, to malware sandboxes, and cyber threat intelligence. According to cybersecurity expert and analyst J. Oltsik:

> Each of these tools must be deployed, configured, and operated daily. Furthermore, each tool provides its own myopic alerting and reporting. Security analysts are then called upon to stitch together a complete threat management picture across endpoint security tools, network security tools, threat intelligence, etc.

This is a manual process that doesn’t scale. Little wonder then why malware is often present on a network for hundreds of days before being discovered.^82

Organizations are best served by investing in an integrated detection and response platform. Check Point, Splunk, Cisco, Fidelis, FireEye, McAfee, Palo Alto Networks, Symantec, and Trend Micro are representative of vendors offering such integrated capabilities. Supplementing the integrated platform with “best-of-breed” tools that provide unique capabilities is always an option.

Maintaining, monitoring, and analysis of audit logs are another important detection control. Data breaches often go undetected for long periods because organizations do a poor job of maintaining comprehensive logs and regularly analyzing and reviewing the results.

Logging capabilities on all systems and networking devices must be enabled. The settings should be appropriately configured so that the log report includes detailed information ranging from event source to data, user, timestamp, source address, and destination address. To ensure timestamp consistency, it is recommended that all servers and network devices retrieve information from at least three synchronized time sources. There should be a process in place, preferably automated, to regularly collect, suitably aggregate, and transmit log data to a central log management system for analysis and review.

Following is a list of questions to guide the planning and implementation of detection processes and tools.

## Detecting Anomalies and Events: Guiding Questions

- 1. Is there a formal and well-documented cyber intelligence gathering process in place?
- 2. To what extent is the cyber intelligence gathering plan comprehensively written, addressing each of the four phases—planning, collection, processing and analysis, and dissemination?
- 3. To what extent are the various intelligence-gathering sources clearly identified and a plan in place on how to leverage those resources?
- 4. Does the organization deploy a Security Information and Event Management (SIEM) platform for security monitoring, advanced threat detection, incident investigation and response, and other related services?
- 5. Is a security operations center (SOC) and team in place to lead the threat intelligence gathering initiatives?
- 6. Is a formal and rigorous process in place to select external expertise to assist with intelligence gathering and threat detection activities?
- 7. Considering the plethora of sophisticated detection tools, is a rigorous process in place to implement an integrated detection and response platform?
- 8. Is a baseline of network operations and expected data flows for users and systems established and managed?
- 9. Are detected events analyzed to understand attack targets and methods?
- 10. Are event data aggregated and correlated from multiple sources and sensors?
- 11. Is there a process in place to determine the impact of events?
- 12. Are incident alert thresholds established?
- 13. To what extent are roles and responsibilities for detection well defined to ensure accountability?
- 14. How often are detection processes tested?
- 15. Is event detection information communicated to appropriate parties?
- 16. How often are detection processes reviewed and updated?

## 6.4 Respond and Recover

With the threat of cyberattack constantly looming over their heads, organizations must be ever prepared to effectively deal with a real threat incident.

The ability to a) quickly identify and isolate affected devices and systems, b) expeditiously restore normal business operations, c) meticulously gather evidence and secure the attack domain for further investigation, and d) effectively communicate with various stakeholders—customers, employees, regulators, business partners, and investors—are some attributes of a highly prepared and response-ready organization.⁸³ The next two subsections are devoted toward understanding how to develop and sustain incident response and disaster recovery capabilities.

### 6.4.1 Incident Response Capability

According to investigation reports, the massive Equifax breach was caused by the negligence of a senior management person who didn’t take necessary action upon receiving good intelligence. As discussed in Chapter 3, one of the lessons from the Equifax incident is to develop the discipline and routine of promptly reviewing intelligence reports and making informed decisions on whether to act or not.

The effectiveness of an organization’s incident response capability (IRC) depends on many factors—from senior management commitment and mindset to organization-wide support, suitable governance structures and mechanisms, appropriate technology solutions, adequate resources, and well-trained personnel.

Crisis management preparation must be driven by a top management mindset that recognizes cybersecurity to be more than an IT issue and requires the expertise and involvement of personnel from multiple functions and varied skillsets. Technical and forensic skills are essential to detect the source and cause of the cyberattack. Legal representation will guide organizational response from the standpoint of dealing and communicating with law enforcement, customers, employees, shareholders, regulatory agencies, business partners, and investors. Communications personnel must also be part of the cross-functional crisis management team to drive the messaging plan. Members from the various operating units will enlighten the crisis management team on the business implications of the attack. From a technology standpoint, both proactive and responsive tools must be available to the team to mitigate the possibility of similar attacks in the future. The personnel assigned to deploy, support, and maintain these tools must be well trained. If third-party services are going to be utilized, then the individual or team dealing with the external agency must have the experience and ability to provide strong oversight.
