
This initial `preparation` phase of the `incident management plan` deals with creating and training a `computer security incident response team (CSIRT)` and putting preventive controls in place to limit the number of incidents that occur based on the results of the organization's risk assessments. This involves four major activities:

1.  Creating and publishing the policies, procedures, processes, and guidelines to handle incidents in a format similar to that described in [Figure 10.7](#c10.xhtml#c10-fig-0006). To be effective, the IRP must include a process for personnel to identify, classify, and respond to cybersecurity incidents. This includes providing guidelines for personnel to use in determining whether the incident is a reportable cybersecurity incident.

2.  Creating the CSIRT along with a process for activating the team. This includes identifying appropriate people and assigning them roles and responsibilities to perform in the incident response process described in the IRP. The IRP typically includes requirements for how and in what timeframe to notify the CSIRT of a reportable incident. In critical ICS environments, these requirements may involve reporting to an external agency, such as the NERC's E-ISAC center in a given timeframe (such as within 24 hours).

3.  Develop a communication plan for all stakeholders. This includes identifying the interactions and communications that need to be performed. For example, the plan should establish criteria for when to report incidents and to whom, as well as how information is to be exchanged when an incident report is received.

4.  Train all personnel to understand the IRP and their role in it. Define how tasks are to be performed, how different processes in the plan relate, and how actions are coordinated—no matter who is performing the work.

5.  Ensure that any equipment that may be required to respond appropriately to any of the incident types is available.

During this phase, the organization should be conducting the following recommended practices for securing their networks, computing devices, and software assets:

*   Conducting risk assessments
*   Hardening and monitoring all host devices in the network
*   Hardening the networks' outer perimeters
*   Establishing and maintaining their malware prevention activities
*   Conducting cybersecurity awareness training for all users

### Creation of the Incident Response Team

The key to making the organization's IRP work efficiently is its computer security incident response team. This team is a group (or organization) that receives reports of suspected security incidents, conducts analyses of those reports, and responds to incidents to return operations to normal levels. According to NIST, the incident response team should be available for anyone in the organization who discovers or suspects that an incident involving the organization has occurred.

In most ICS organizations, the CSIRT is composed of a cross section of stakeholders, such as those described in [Figure 10.8](#c10.xhtml#c10-fig-0007). Depending on the size and nature of the organization, the CSIRT may be an established group of stakeholders or a group generated on an ad hoc basis when a security event or incident is reported.

![FIGURE 10.8 CSIRT members](images/c10f008.png)

**[FIGURE 10.8](#c10.xhtml#R_c10-fig-0007)** CSIRT members

For a given IRP, the roles and responsibilities of each CSIRT member should be clearly identified and assigned to specific people. In any particular organization, the CSIRT may specify personnel for any of the following team roles:

*   CSIRT team leader
*   Incident handlers
*   IR triage manager
*   IR forensic analysts
*   IR platform specialists
*   Vulnerability handlers

Important considerations for including specific people on the CSIRT include their availability and skill sets. The ability to quickly assemble and deploy the CSIRT when an incident is escalated is a key requirement for all members. The CSIRT must be able to come online, thens target and respond effectively to incidents to minimize their impact on the organization's operation and productivity. If the members of the team cannot be counted on to respond quickly when needed, alternative personnel should be appointed.

Likewise, the members of the team must have the necessary skill sets and tools that will enable the team to track down the root cause of the incident and neutralize it. They should also have the ability to identify the perpetrators for possible prosecution.

### Detection and Analysis

The foremost function of the detection and analysis phase is to identify and verify that a reported incident has occurred and that it is an actual incident. Incident reports can come from anywhere in the organization—users, administrators at different levels, monitoring tools, or even outside organizations.

When an individual detects an unusual event or incident occurring on the network, they must be trained to follow the organization's security policy that requires them to take appropriate action as part of an incident response. The individual's role in the response to an observed incident normally includes items such as contacting a designated member of the incident response team, documenting what activities were going on when the incident occurred, and keeping the attacked computer on.^(\*)

After a potential incident has been reported, it must be validated. As mentioned earlier, the IRP should specify what constitutes an incident, who to report it to, and how. So, this first step in the recognition phase is to report the suspected incident to the `incident handler` specified in the plan. At this point, the incident handler takes over ownership of the report.

Their next step is to gather information about the details of the incident report. Regardless of the source of the report, whether from an individual that makes a call or an IDS signal that reports an incident, the incident handler must investigate the incident for accuracy. The primary purpose of this initial investigation is to determine the severity of the incident and decide whether it needs to be escalated to the incident response team.

For example, if an unusual event is reported by one of the network's intrusion detection systems, the incident handler must determine whether the report is accurate or a false positive. This typically involves evaluating the IDS logs and clinical situation. If the IDS is configured correctly and functioning properly, the incident handler reports the incident to the network security administrator who, in turn, activates the CSIRT to carry out the IRP processes.

### Automated Intrusion Detection Tools

As with physical security efforts, preventing unauthorized access is the first line of security at the local computing and control device level. However, it is just as important at this level to be able to detect the occurrence of an intrusion and notify the proper authorities of its nature.

`Computer-based intrusion detection systems (IDSs)` can be implemented in two ways, as a `network-based IDS (NBIDS)` or as a `host-based IDS (HBIDS)`. In both cases, the system is designed primarily to monitor the system (local computer or network environment), log key events and policy violations, and report them as directed.

While an HBIDS is similar to a firewall in that it monitors inbound traffic, it is different in that it also monitors the outbound traffic leaving the device. All IDS devices are based on one of two strategies:

*   `Signature analysis`—Incoming and outgoing traffic is compared with a database of stored specific code patterns that have been identified as malicious threats.
*   `Anomaly analysis`—Incoming and outgoing traffic is compared to an established baseline of normal traffic for the system. The baseline is "learned" (generated) by applying mathematical algorithms to data the system obtains from the traffic flow.
