
## Business Continuity, Disaster Recovery, and COOP

*   **Business continuity (BC) plans** focus on keeping an organization functional when misfortune or incidents occur. In the context of IR processes, BC plans may be used to ensure that systems or services impacted by an incident can continue to function despite any changes required by the IR process. That might involve ways to restore or offload the services or use of alternate systems. Business continuity plans have a significant role to play for larger incidents, whereas smaller incidents may not impact an organization's ability to conduct business in a significant way.

*   **Disaster recovery (DR) plans** define the processes and procedures that an organization will take when a disaster occurs. Unlike a business continuity plan, a DR plan focuses on natural and man-made disasters that may destroy facilities, infrastructure, or otherwise prevent an organization from functioning normally. A DR plan focuses on restoration or continuation of services despite a disaster.

In addition to these types of plans, **continuity of operation planning (COOP)** is a federally sponsored program in the United States that is part of the national continuity program. COOP defines the requirements that government agencies need to meet to ensure that continuity of operations can be ensured. Those requirements include how they will ensure their essential functions, the order of succession for the organization so that staff know who will be in charge and who will perform necessary functions, how authority will be delegated, how disaster recovery can function using continuity facilities, and a variety of other requirements. COOP defines how federal agencies build a complete disaster recovery and business continuity plan.

[Figure 14.2](#c14.xhtml#c14-fig-0002) shows the four phases of the Continuity of Operations as defined by the Federal Emergency Management Agency (FEMA) as part of COOP.

### Policies

Organizations define policies as formal statements about organizational intent. In short, they explain why an organization wishes to operate in a certain way, and they define things like the purpose or objective of an activity or program. **Incident response policies** are commonly defined as part of building an IR capability.

![FIGURE 14.2 Federal Continuity of Operations Planning stages](images/c14f002.png)

[**FIGURE 14.2**](#c14.xhtml#R_c14-fig-0002) Federal Continuity of Operations Planning stages

Well-written incident response policies will include important components of the IR process. They will identify the team and the authority that the team operates under. They will also require the creation and maintenance of incident handling and response procedures and practices, and they may define the overall IR process used by the organization. In some cases, they may also have specific communication or compliance requirements that are included in the overall policy based on organizational needs.

An IR policy isn't the only policy that your organization may rely on to have a complete incident response capability. In fact, organizations often have many IT policies that can impact response. The Security+ exam outline focuses on one specific additional policy, however: **retention policies**. A retention policy determines how long you keep data and how it will be disposed of. A retention policy is important to incident responders since it may determine how long the organization keeps incident data, how long logs will be available, and what data is likely to have been retained and thus may have been exposed if a system or data store is compromised or exposed.

## Attack Frameworks and Identifying Attacks

Incident responders frequently need ways to describe attacks and incidents using common language and terminology. Attack frameworks are used to understand adversaries, document techniques, and to categorize tactics. The Security+ exam outline covers three major frameworks: MITRE's ATT&CK, the Diamond Model of Intrusion Analysis, and Lockheed Martin's Cyber Kill Chain.

### MITRE ATT&CK

MITRE provides the **ATT&CK**, or Adversarial Tactics, Techniques, and Common Knowledge, knowledgebase of adversary tactics and techniques. The ATT&CK matrices include detailed descriptions, definitions, and examples for the complete threat lifecycle from initial access through execution, persistence, privilege escalation, and exfiltration. At each level, it lists techniques and components, allowing threat assessment modeling to leverage common descriptions and knowledge.

ATT&CK matrices include pre-attack, enterprise matrices focusing on Windows, macOS, Linux, and cloud computing, as well as iOS and Android mobile platforms. It also includes details of mitigations, threat actor groups, software, and a host of other useful details. All of this adds up to make ATT&CK the most comprehensive freely available database of adversary techniques, tactics, and related information that the authors of this book are aware of.

[Figure 14.3](#c14.xhtml#c14-fig-0003) shows an example of an ATT&CK technique definition for attacks against cloud instances via their metadata APIs. It provides an ID number, as well as classification details like the tactic, platforms it applies to, what user permissions are required, the data sources it applies to, who contributed it, and the revision level of the specific technique.

The ATT&CK framework is the most popular of the three models discussed here and has broad support in a variety of security tools, which means that analysts are most likely to find ATT&CK-related concepts, labels, and tools in their organizations. You can find the full ATT&CK website at `attack.mitre.org`.

### The Diamond Model of Intrusion Analysis

The **Diamond Model of Intrusion Analysis** describes a sequence where an adversary deploys a capability targeted at an infrastructure against a victim. In this model, activities are called events, and analysts label the vertices as events are detected or discovered. The model is intended to help analysts discover more information by highlighting the relationship between elements by following the edges between the events.

![FIGURE 14.3 MITRE's ATT&CK framework example of attacks against cloud instances](images/c14f003.png)

[**FIGURE 14.3**](#c14.xhtml#R_c14-fig-0003) MITRE's ATT&CK framework example of attacks against cloud instances

The Diamond Model ([Figure 14.4](#c14.xhtml#c14-fig-0004)) uses a number of specific terms:

*   **Core Features** for an event, which are the adversary, capability, infrastructure, and victim (the vertices of the diamond)
*   **Meta-Features**, which are start and end timestamps, phase, result, direction, methodology, and resources, which are used to order events in a sequence known as an activity thread, as well as for grouping events based on their features
*   **Confidence Value**, which is undefined by the model but that analysts are expected to determine based on their own work

![FIGURE 14.4 The Diamond Model of Intrusion Analysis](images/c14f004.png)

[**FIGURE 14.4**](#c14.xhtml#R_c14-fig-0004) The Diamond Model of Intrusion Analysis

The Diamond Model focuses heavily on understanding the attacker and their motivations, and then uses relationships between these elements to allow defenders to both understand the threat and think about what other data or information they may need to obtain or may already have available.

### The Cyber Kill Chain

Lockheed Martin's **Cyber Kill Chain** is a seven-step process, as shown in [Figure 14.5](#c14.xhtml#c14-fig-0005).

![FIGURE 14.5 The Cyber Kill Chain](images/c14f005.png)

[**FIGURE 14.5**](#c14.xhtml#R_c14-fig-0005) The Cyber Kill Chain

Here are the seven stages of the Cyber Kill Chain:
