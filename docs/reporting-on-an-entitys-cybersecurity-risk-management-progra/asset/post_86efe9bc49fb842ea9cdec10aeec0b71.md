
The incident response sections of the CIRP have been created based on a threat scenario risk assessment performed annually as part of the review of the plan. The plan is focused on responding to those threat scenarios that have the highest impact and likelihood of occurring based on the business and markets in which the Company operates and the current technology environment. The incident response sections of the CIRP include the following key information:

- Response plan owners (those who can activate the plan), team members, and contact information for plan owners and team members
- Defined criteria required to activate the response plan
- Target business and IT performance metrics for operating in a "business as usual" environment
- Linkage to the business impact analysis and critical path recovery items within the disaster recovery (DR) and business continuity (BC) plans
- Alternate internal and external communication and operating methods to use when primary methods are unavailable
- Communication plan for notifying internal stakeholders (including legal, human resources, marketing, and investor relations), retained service providers (external counsel, forensics investigators, and the like), and external stakeholders (such as customers, vendors, regulators, and law enforcement) to manage expectations and information disclosure as part of the overall response effort. The communication plan also includes communication templates for certain formal internal and external communications, including, but not limited to, internal IT outage notifications and public press releases
- Facility recovery procedures providing linkage to the DR and BC plans regarding the hosted hot site facility located in Syracuse, NY, and the alternate call center located in Troy, MI
- Data response procedures providing linkage to the backup policies and procedures, as well as the DR plan, regarding offsite data storage and backup media
- Hardware and software access procedures enabling IT service and operations during response and recovery procedures
- Response and recovery metrics focused on the target response and recovery milestones to enable effective management, measurement, and monitoring of recovery activities
- Detailed incident response and recovery procedures to be executed based on the identification of the root cause, including operational steps to eradicate any infections, malicious code, unauthorized user accounts, and the like, and restore systems in accordance with priority and dependencies

It should also be noted that mitigating processes and controls are evaluated as part of the current CIRP-related processes and controls in place to detect and respond to security incidents and events. (These mitigation process and control factors may be directly related to the CIRP or may be part of other security monitoring related controls.)

The CIRP is reviewed annually and approved by the following members of management:

- CISO
- CIO
- CTO
- CRO
- GC
- Chief Marketing and Communications Officer
- Director, Security Operations
- Director, Crisis and Response Management

## Implementation Activities to Mitigate and Recover from Identified Security Incident

The plan activation process begins when one or more of the incident response and recovery plan owners are informed of a cybersecurity event for which incident response is imminent or underway. The plan owner will ensure details about the cybersecurity event are clearly understood and documented to the extent necessary to enable future communications. This includes the identification of security monitoring or other mitigating processes and control factors which may be present and reduce the overall impact of the identified security event. Should the plan owner decide to activate the plan, he or she will convene an emergency meeting of the CIRP leadership team (including the CIO, CISO, CRO, GC, VP of human resources, and CFO) to determine:

- Immediate tasks
- Departments and functions required to carry out the plan based on the cybersecurity event
- The initial communication plan and the individual assigned to execute the plan

Once agreement is made, the leadership team is responsible for notifying members of their teams and others, including external advisors (such as investor relations and external general counsel) about the plan activation, initial decisions made, and assigned actions.

Once activated, XYZ considers the current cybersecurity event and its effects on systems and business operations. The Company refers to the appropriate sections of the BC and DR plans, as well as the relevant and applicable data backup logs, to identify the following:

- Where the IT systems and IT infrastructure affected by the cybersecurity event reside within the asset prioritization hierarchy
- Where the business operations affected by the cybersecurity incident or event reside within the operations prioritization hierarchy
- The planned alternative IT systems (such as the failover or load-balanced servers and network devices) and business processing activities (for instance, manual sales order forms) for the effected components of the environment
- The time prior to the cybersecurity incident or event from when the Company will be able to respond to and recover from (recovery point objective [RPO]) for the affected IT systems and IT infrastructure
- The maximum length of time until IT systems, IT infrastructure, and business processes affected by the cybersecurity incident or event is returned to normal business operation, after which significant negative impact may occur (recovery time objective [RTO])

For each IT asset (hardware and software, including virtualized assets) affected by the cybersecurity event, an evaluation will be made to determine the appropriate response and recovery actions, such as the following:

- Decommission and replace
- Reconfigure with enhancements (firmware updates, vendor patches, configuration changes)
- Reconfigure with no enhancements

Recognizing that the Company may not be able to complete the chosen recovery action in a timely manner in relation to the RTO, an alternative solution will be determined to enable a return to normal processing.

Data restoration is based on the activities outlined in the backup and recovery policies and procedures. The backup procedures apply to the following:

- Network devices—such as configurations, access control lists, and firmware
- Physical and virtual servers (DNS servers, email servers, FTP servers, application servers, database servers, web servers)—operating systems, application programs, and application data
- Networked file shares
- End user computing (desktops, laptops, tablets, mobile devices) and peripherals (such as printers and copy machines)
- Telephone and voice-mail systems

XYZ Manufacturing leverages a global backup management solution to manage the backup processing and monitoring of all IT assets connected to the environment. The backup solution is connected to a virtual storage area network (SAN) and supplemented by real-time disk imaging to an offsite facility for the highest-value IT assets and data. Moderate- and lower-value information and IT assets are backed up to electronic, removable media and stored at a secure offsite facility for the period of time defined by the backup and recovery policies and procedures. Backup method and frequency is based on the volume and frequency of information processing and the importance of the data or IT asset.

Restoration of data, software, and configurations is made using the global backup management solution. Prior to restoring data, software, and configurations to the live environment, the Company will conduct tests in the security sandbox against the backup media to determine if the cybersecurity event is present. Based on results, the Company may seek to leverage an older backup or execute the eradication techniques that were successfully employed in the production environment.

Communications related to a cybersecurity event are governed by the CIRP leadership team. Throughout recovery efforts, XYZ will communicate to the extent possible, and as required, with employees, stakeholders, regulators, or law enforcement through formal written and verbal communications (email, press releases, mass voicemail) that are structured to be informative, easy to understand, and transparent and that address the following:
