
# Objective 6.5: Conduct or facilitate security audits

In this objective we discussed conducting security audits. Auditing is an ongoing business process that looks for wrongdoing and anomalies in operations. However, an audit is also an event used to review compliance standards for systems, processes, and other activities. Audits can be performed by one of three types of audit teams: internal teams, external teams, and third-party teams. Internal teams are more cost-effective but lack independence from the organization and may not have access to the right audit tools and techniques. External teams work for a business partner or other stakeholder and audit processes and activities as required by a contract. Third-party audit teams are more expensive but allow some level of independence from organizational stakeholders and may be required in the event of regulatory audits.

## 6.5 QUESTIONS

**[1](#ch06.xhtml#ch6ques5-1).** You are a cybersecurity analyst for your company. You have been tasked with auditing account management in another division of the company. Which of the following types of auditing would this be considered?

**A.** Third-party audit

**B.** External audit

**C.** Internal audit

**D.** Second-party audit

**[2](#ch06.xhtml#ch6ques5-2).** Your company must be audited for compliance with regulations that protect healthcare information. Which of the following would be the most appropriate type of auditors to perform this task?

**A.** External auditors

**B.** Internal auditors

**C.** Second-party auditors

**D.** Third-party auditors

## 6.5 ANSWERS

**[1](#ch06.xhtml#r_ch6ques5-1).** C An internal audit uses auditors from within an organization to assess another part of the organization.

**[2](#ch06.xhtml#r_ch6ques5-2).** D For a compliance audit, third-party auditors are usually the most appropriate type of audit team to conduct the effort, due to their independence.

![Images](f0285-01.jpg)

# Security Operations

## Domain Objectives

• 7.1 Understand and comply with investigations.

• 7.2 Conduct logging and monitoring activities.

• 7.3 Perform Configuration Management (CM) (e.g., provisioning, baselining, automation).

• 7.4 Apply foundational security operations concepts.

• 7.5 Apply resource protection.

• 7.6 Conduct incident management.

• 7.7 Operate and maintain detective and preventative measures.

• 7.8 Implement and support patch and vulnerability management.

• 7.9 Understand and participate in change management processes.

• 7.10 Implement recovery strategies.

• 7.11 Implement Disaster Recovery (DR) processes.

• 7.12 Test Disaster Recovery Plans (DRP).

• 7.13 Participate in Business Continuity (BC) planning and exercises.

• 7.14 Implement and manage physical security.

• 7.15 Address personnel safety and security concerns.

Domain 7 is unique in that it has the most objectives of any of the CISSP domains, and it accounts for approximately 13 percent of the exam questions. You’ll find that many of the objectives covered in this domain, Security Operations, have also been briefly discussed throughout the entire book. This is because security operations are diverse and overarching activities that span multiple areas within security.

In this domain we will examine a wide range of subjects, including those that are reactive in nature, such as investigations, logging and monitoring, vulnerability management, and incident management. We will also look at the details of how to ensure a secure change and configuration management process that is supported by patch management.

We will review some of the foundational security operations concepts that we also discussed in Domain 1 and apply some of those concepts to resource protection. We will also look at some of the more technical details of detective and preventive measures, such as firewalls and intrusion detection systems. Four of the objectives address business continuity planning and disaster recovery, and we will discuss the strategies involved with each topic as well as how to implement and test the plans associated with these processes. Finally, we will review physical and personnel safety and security concerns.

## Understand and comply with investigations

In Objective 1.6 we briefly touched on the types of investigations you may encounter in security, and we also reviewed the related topics of legal and regulatory issues in Objective 1.5. These two objectives go hand-in-hand with Objective 7.1, which carries our discussion a bit further by focusing on *how* investigations are conducted.

### Investigations

Recall from Objective 1.6 that the four primary types of investigations are administrative, regulatory, civil, and criminal investigations. Regardless of the type of investigation, however, most of the activities, processes, and techniques that are used are common across all of them. This includes how to collect and handle evidence; reporting and documenting the investigation; the investigative techniques that are used; the digital forensics tools, tactics, and procedures that are implemented; and the artifacts that are discovered on computing devices using those tools, tactics, and procedures. These common activities are the focus of this objective.

#### Cross-Reference

The types of investigations you may encounter in cybersecurity were discussed at length in Objective 1.6.

#### Forensic Investigations

Computers, mobile devices, network devices, applications, and data files all contain potential evidence. In the event of an incident involving any of them, they must all be investigated. Computing devices can be part of an incident in three different ways:

• As the target of the incident (e.g., as an attack on a system)

• As the tool of the incident (used to directly perpetrate a crime, such as a hacking attack)

• Incidental to the event (part of the event but not the direct target or tool used, such as researching how to commit a murder, for instance)

*Computer forensics* is the science of the identification, preservation, acquisition, analysis, discovery, documentation, and presentation of evidence to a court of law (either civil or criminal), corporate management, or even to a routine customer. Computer forensic investigations are carried out by personnel who are uniquely qualified to perform them. *E-discovery* is another term with which you should be familiar; it is the process of discovering digital evidence and preparing that information to be presented in court. The most important part of the computer forensics process is how evidence is collected and handled, discussed next.

#### Evidence Collection and Handling

Evidence preservation is the most crucial part of an investigation. Even if an unskilled investigator is not properly trained to analyze evidence, the investigation can be saved by ensuring that the evidence is preserved and protected at all stages of the investigation. Evidence preservation involves proper collection and handling, including chain of custody, physical protection, and logical protection. We will discuss proper collection and handling procedures in the next few sections. However, chain of custody is an important one to discuss first.
