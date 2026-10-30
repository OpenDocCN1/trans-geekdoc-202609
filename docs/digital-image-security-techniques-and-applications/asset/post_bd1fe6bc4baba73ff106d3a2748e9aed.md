
## Table 9.1 Frequent data sources of CTI

| CTI data source | Brief Description | Source | Examples | Value |
|---|---|---|---|---|
| OSINT | Data that can be collected from the internet or other CTI companies | External | Vulnerability/exploit feeds, social media, Darknet data, public statements, threat feeds | Provides a comprehensive view of an organization's external threat landscape |
| Internal Intelligence | Data collected from internal cyber assets | Internal | Network logs, database access events, Intrusion Detection Systems (IDS) logs, Intrusion Prevention Systems (IPS) logs | Provides information about activities internal to an organization |
| Human Intelligence | Manual research and data collection | Internal and External | Direct hacker interactions | Provides very precise and deep knowledge |
| Counter Intelligence | Provides false information to deceive hackers | Internal and External | Honeypots, anti-human intelligence | Safely identifies tools and methods used by attackers |
| Finished Intelligence | Finished Intelligence ready for dissemination | Internal and External | Commercial data feeds | Refines and analyzes intelligence |

## Table 9.2 Incident response for CTI and its derived capabilities

| Category | Core concept | Derived capabilities |
|---|---|---|
| General | Aggregability | Information Sharing, Semantics |
| General | Categorization | Comprehensibility, Delimitation |
| General | Granularity | Structuring |
| General | Versioning | Data Quality, Maintenance |
| General | Referencing | Usability, Separation |
| General | Extensibility | Customization, Sustainability |
| General | Readability | Comprehensibility, Interpretability |
| General | Unambiguous Semantics | Clarity, Interorganizational Understanding and Application |
| Structural | Workflow | Sequencing, Operations |
| Structural | Actuator | Actionability |
| Structural | Action | Atomicity |
| Structural | Artifact | CTI Integration |
| Technological | Community | Usability, Acceptance, Maintenance |
| Technological | Application | Technical Integration, Interoperability |
| Security | Serialization | Data Storage, Data Transfer |
| Security | Confidentiality | Information Sharing, Operations |
| Security | Authorization | Misuse Prevention, Operations |
| Security | Prioritization | Information Importance, Operations |

## Table 9.3 Description of the core concepts of IR

| Core Concept | Description |
|---|---|
| Aggregability | Grouping of related incident response |
| Categorization | Distinguishable objectives of incident response |
| Granularity | Different levels of incident response |
| Versioning | Documenting incident response information updates and revocations |
| Referencing | Referral to incident response elements with unique IDs |
| Extensibility | Provision of additional IR information |
| Readability | Legibility of IR elements |
| Unambiguous Semantics | Distinct meaning of different incident response elements |
| Communality | Supporting elements of incident response standardizations |
| Applications | Technological dependencies of IR standardizations |
| Serializations | Encoding of incident response information |
| Confidentiality | Sensitivity aspect of IR information |
| Authorization | Control measures of IR procedures |
| Prioritizations | Urgency of IR actions |

## 9.7 CYBER THREAT INTELLIGENCE FRAMEWORK FOR ENERGY CLOUD ENVIRONMENTS

A CTI-based security framework can develop better risk identification capabilities and an immediate response process of any smart city-based organization that uses the cloud. This framework is considered as the fundamental architecture of CTI-integrated security services of the organizations. It is composed of several nodes for generating a demand response system that performs production of essential intelligence based on IOCs. This framework follows several patterns in a hierarchical form, as shown in Figure 9.6. CTI Sharing Procedure: This section demonstrates the data collection for the IoC with the purpose of generating a CTI in each layer of the framework. Each of the steps is mentioned in detail below and shown in Figure 9.7. The design of the final CTI report of the information is given in Figure 9.8.

![](img/6e4271af21d9a195003ab8711aa79d27_204_0.png)

Figure 9.6 Architecture of the CTI framework.

![](img/6e4271af21d9a195003ab8711aa79d27_205_0.png)

Figure 9.7 The dissemination process of policies on energy cloud of CTI.

- Step 1 (Gathering of data from the devices): The local layer incorporates multiple home area networks or HAN that transfers the functioning status, energy production, and consumption data to the smart meters. Then the status data and energy information of the diverse devices in the connected home area network (HAN) are collected and transmitted to the connected data concentrator. This communication requires small-range wired/wireless communications for communicating between devices, data concentrator, and smart meters.
- Step 2 (Identification of compromise indicators from object data): The data concentrators mark the received network data and action statuses of the device and further modify the data into CTI.
- Step 3 (Threat identification in local range): The local CTI server recognizes the IoC from the CTI data obtained from the data concentrator. Consequently, the local CTI server questions the database to the central CTI server to acquire data for the detected IoC data. After making the IoC attribute data secure, the local CTI server transforms the CTI data into the HIN (Heterogeneous Information Network) format and calculates and checks the CTI data specifying the presence of a cyber threat applying a pre-learned Graph Convolutional Network (GCN) model; then the local CTI server sends the result and CTI data to the centrally present CTI server.

![](img/6e4271af21d9a195003ab8711aa79d27_206_0.png)

Figure 9.8 Design of CTI of energy cloud environment.

- Step 4 (CTI triggering and response to threats in global prospect): The central CTI server aggregates all the data received from numerous local CTI servers. It also collects added data from OSINT using the CTI's IoC resources delivered to collect a variety of cyber threat-related data. The action policy of the CTI is made by the core CTI servers that can directly be implemented by the devices and smart meters. It finally synthesizes the CTI analysis result that is received by the core server. These action policies are distributed in the form of a list of IPs that need to be blocked, domains updated, etc. The CTI synthesized by the core CTI server is distributed to local CTI servers.

## 9.8 BENEFITS OF CTI

Several groups of associations and partakers nowadays adopt the significance of threat information distribution for many significant causes. The interchange of crucial threat information failed to be exposed to avert the impending cyberattacks and to alleviate potential attacks. Benefits of sharing data embraces a better awareness of the threat vertical, a profound perception of threat actors and their TTPs, and a superior position to protect against surfacing risks [29].

Additionally, sharing threats perks up synchronization for a cooperative knowledge, response to original pressure, and reduction of the probability of cascading effects across complete sectors, system, industry, or across sectors [29–33]. The major benefits of CTI are:

- Offers a greater insight to possible cyber threats.
- Prevents loss of knowledge by identifying cause of knowledge discharge.
- Performs knowledge/data analysis to discover exploitable data points.
- Gathers and shares knowledge to spread threat awareness.
- Identifies security breaches at a preliminary stage.
- Utilizes the compromise indicators for modeling a proactive defense line before any system compromise.
- Boosts threat detection through prioritized event inspections.
- Leverages a comprehensive vision to the threat scenario.
- Situational awareness to potential threats in the enterprise.
- Forms a landscape that provides strategic decisions to the threat vertical.
- Associative approach for threat vertical for complete cyber protection.

CTI supports organizations to overcome severe threat and security breaches, facilitates threat information processing to identify and understand threat horizon, quickly reacts to any stressed situation, and anticipates any further operation of the adversary. It enables investors to intelligently invest in any enterprise by minimizing the risk for faster and efficient outcome. Alternatively, it assists the security team to make an effective judgement for revealing the approach, movement, techniques, and procedures that enable effective security by making the goals of the attackers unattainable. Additionally, it decreases the cost and resource requirement and thus enhances the accuracy of the analysis.

## 9.9 CHALLENGES OF CTI

Generally, security teams cannot formulate valuable use of their threat data because it presents lots of threat intelligence, which in turn causes inconvenience. The everyday deposit of indicators seems to become much distrustful occurrence in internet. It offers approximately 250 million indicators in a single day [30]. It enables consumers to assemble their own intelligence. The essential brain power is always required to examine the production speed of the threat data [34]. Timeliness or aptness of threat data is also crucial when defending against destructive attackers and zero-day utilizations.
