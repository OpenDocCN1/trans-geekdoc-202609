
## Post-Incident Activity

A full incident post-mortem should be conducted after a security incident is resolved, especially if it has affected customers or resulted in a data breach; the post-mortem process should be designed to identify technical lapses, procedural failures, manual errors, and other process flaws that might have contributed to or been identified during the incident response process. As part of the process, the following should be included:

- Identify opportunities for improving the security incident response process or system security by investigation and analyzing the root cause.
- Identify process, training, or technology improvement opportunities with product group subject-matter experts and security and privacy experts.
- New automated monitoring and detection mechanisms will be implemented to discover future issues.

## Continuous Improvement

The security response team should implement lessons learned from the security incident to prevent future security incidents and improve detection and response capabilities. The efficiencies and effectiveness of incident response depend on continuous improvement. To defend organizations and their customers from evolving threats, post-incident activities ensure that lessons learned are successfully implemented across the enterprise.

Following Microsoft's standard SDL, any findings are recorded as work items or bugs for product teams to address, and these items are assigned to the appropriate owner teams. In senior management's monthly security incident review meetings, the results of the post-mortem are discussed.

## Evaluate a Security Operations Strategy for Sharing Technical Threat Intelligence

An organization's threat intelligence team provides context and insights using a threat intelligence platform (TIP). Many different facets could be included in these insights, such as the following:

- How to respond to active incidents with technical research during the incident
- The study of attacker groups, attack trends, high-profile attacks, and emerging techniques in a proactive manner
- Analyses, research, and insights to guide priorities and processes in the business and security technical teams

A large, diverse set of threat intelligence data needs to be applied to your processes and tools to succeed, and Microsoft does both.

You must ensure that the data Microsoft collects from various sources is used only in ways agreed upon by our customers by passing it through a strict privacy/compliance boundary. It is a responsibility that Microsoft takes seriously.

The following are the sources of data:

- Specialized Microsoft security products
- Black market insights (criminal forums)
- Insights from Microsoft's incident response engagements

Disinformation, nation-states, ransomware, IoT, and operational technology (OT) security are some critical topics that Microsoft researches and helps solve. The Microsoft Digital Defense Report (MDDR) posts learnings and actionable recommendations.

The following are some notable parts of this process:

- In the data collection and analysis phase, the data is normalized, various analytics are applied (listed) to identify relevant security insights and findings, and APIs are published.
- In the data integration phase, Microsoft's security capabilities access the data to provide findings, context, and insights related to that capability. These findings are then automatically fed into other Microsoft products to enrich them.
- In addition to AI, human teams constantly use this intelligence to hunt for adversaries in Azure, Office 365, Microsoft IT, and Microsoft 365 Defender. Also, these teams are developing, tuning, and validating new analytics to improve detection.

Cybersecurity attacks are characterized by multiple complex malicious events, attributes, and contexts. Making the distinction between suspicious and nonsuspicious activities is a challenging task. When determining whether an observed behavior is suspicious, knowing known attributes and abnormal activities specific to your industry is crucial.

The Microsoft network provides organizations with access to various signals that can be used to collect cyberthreat intelligence. Cyberthreat intelligence can be obtained from many sources. An organization's security investigations may collect local intelligence through its open-source data feeds, threat intelligence-sharing communities, commercial intelligence feeds, and commercial intelligence feeds. Every second, Microsoft Intelligent Security Graph adds hundreds of gigabytes of data.

The following are the sources of this anonymized data:

- The Microsoft data center network spans the globe with more than 100 data centers.
- Threats faced by over 1 billion PCs updated by Windows Update each month.
- Microsoft conducts extensive research through Microsoft's Digital Crime Unit and Cybersecurity Defense Operations Center and partner with industry and law enforcement to collect external data points.

Threat intelligence in Azure provides monitoring insight from the various sources, helping to mitigate the threats with the help of the following:

- It utilizes billions of signals across the Microsoft network (signals mean information traffic).
- Machine learning and artificial intelligence are used.
- It integrates multiple data across different security products to address different attack scenarios.

Using the Intelligent Security Graph and other third-party feeds, Microsoft uses Windows, Azure, and Microsoft 365 to obtain signals. Microsoft integrates these signals for security services on one platform to communicate with security services on another. Any threat that is seen in Windows is automatically and quickly added to Azure's view of threats as a result. This design provides deep insight into the evolving cyberthreat landscape.

### Microsoft Sentinel's Threat Intelligence

A SIEM solution such as Microsoft Sentinel uses threat indicators, otherwise known as indicators of compromise (IoCs), as the most common form of cyberthreat intelligence (CTI). A threat indicator identifies observed artifacts, such as URLs, file hashes, or IP addresses, with known threats, such as phishing, botnets, or malware. To assist security investigators in determining how to respond to malicious activity observed in your environment, Microsoft Sentinel provides threat indicators to assess.

The following activities are used to integrate threat intelligence (TI) into Microsoft Sentinel:

- By enabling data connectors to various TI platforms and feeds, threat intelligence can be imported into Microsoft Sentinel.
- The Microsoft Sentinel threat intelligence page and logs allow you to view and manage the imported threat intelligence.
- Detect threats and generate security alerts and incidents based on threat intelligence imported into built-in Analytics rule templates.
- The threat intelligence workbook in Microsoft Sentinel allows you to visualize essential information about your imported threat intelligence.

### Defender for Endpoint's Threat Intelligence

You can track possible attack activities in your organization using Microsoft 365 Defender by creating custom threat alerts. You can flag suspicious events to gather clues and stop an attack chain by flagging suspicious events. Unlike generic threat alerts, these alerts will appear only within your organization and will flag only the events you have set up to track.

Knowing the concepts behind alert definitions and IoCs is essential before creating custom threat alerts.

### Alert Definitions

Alert definitions are contextual attributes that can collectively identify early clues on a possible cybersecurity attack. These indicators are typically a combination of activities and characteristics, that an attacker took actions to achieve the objective of an attack successfully. Monitoring these combinations of attributes is critical in gaining a vantage point against attacks. Monitoring based on these indicators can help interfere with the chain of events before an attacker’s objective is reached.

### Indicators of Compromise

IoC refers to known malicious events that indicate a network or device has already been compromised. IoCs are often visible after an attack has been carried out and the objective, such as exfiltration, has been achieved. In contrast to alert definitions, these indicators are considered evidence of a breach, and forensic investigations require them to be tracked. While it cannot intervene in the attack chain, the collection of these indicators can aid in the creation of better defenses for future attacks.

### Relationship Between Alert Definitions and IoCs

In Microsoft 365 Defender and Microsoft Defender for Endpoint, alert definitions are containers for IoCs and define the alert, including the metadata raised for a specific IoC match. In addition to identifying signals, alert definitions include a description, name, severity, and attack description.

Microsoft 365 Defender defines the concrete detection logic based on an IoC’s type, value, and action and how it’s displayed in an alert.

### Defender for IoT's Threat Intelligence

IoT and operations technology (OT) devices, vulnerabilities, and threats are identified and managed through a central interface with Microsoft Defender for IoT.

Microsoft Defender for IoT comes with native threat intelligence capabilities using threat intelligence packages, and it can be deployed in Azure-connected environments, hybrid environments, or on-premises. Defender for IoT and Microsoft Sentinel provide threat intelligence from Defender for IoT and enriched threat intelligence from Sentinel.

Defender for IoT offers both agent-based and agentless monitoring:

- Microsoft Defender for IoT offers agentless, network-layer monitoring for end-user organizations. You can deploy Microsoft Defender for IoT on-premises or in an Azure-connected hybrid environment.
- In addition, Microsoft Defender for IoT offers a lightweight micro-agent for IoT device builders that supports Linux and real-time operating system (RTOS) operating systems. With the Microsoft Defender device builder agent, you can ensure that IoT/OT projects are secure from the cloud.

### Defender for Cloud's Threat Intelligence

Defender for Cloud detects threats by collecting and analyzing information about your Azure resources. A security alert containing detailed information regarding the event, including suggestions for remediation, is triggered when Defender for Cloud detects a threat.
