
level of strategic significance to all tasks and activities enables the identification of the areas where strategically significant knowledge is being created. It also identifies those tasks that rely on knowledge sharing or transfer and those that rely on a high quality of knowledge. Benefits of a data audit include:

### Awareness of data holdings
- Promote capacity planning
- Facilitate data sharing and reuse
- Monitor data holdings and avoid data leaks

### Recognition of data management practices
- Promote efficient use of resources and improved workflows
- Increase ability to manage risks – data loss, inaccessibility, compliance
- Enable the development/refinement of a data strategy

## Data Storage and Archiving
Data storage and archiving address those aspects of data management related to the housing of data. This element includes considerations for digital/electronic data and information as well as relevant hardcopy data and information. Without careful planning for storage and archiving, many problems arise that result in the data becoming out of date and possibly unusable as a result of not being properly managed and stored.

Some important physical dataset storage and archiving considerations for electronic/digital data include:
- **Server Hardware and Software** – What type of database will be needed for the data? Will any physical system infrastructure need to be set up or is the infrastructure already in place? Will a major database product be necessary? Will this system be utilized for other projects and data? Who will oversee the administration of this system?
- **Network Infrastructure** – Does the database need to be connected to a network or to the Internet? How much bandwidth is required to serve the target audience? What hours of the day does it need to be accessible?
- **Size and Format of Datasets** – The size of a dataset should be estimated so that storage space can properly be accounted for. The types and formats should be identified so that no surprises in the form of database capabilities and compatibility will arise.
- **Database Maintenance and Updating** — A database or dataset should have carefully defined procedures for updating. If a dataset is live or ongoing, this will include such things as additions, modifications, and deletions, as well as frequency of updates. Versioning will be extremely important when working in a multi-user environment.
- **Database Backup and Recovery Requirements** — The requirements for the backing up or recovery of a database in case of user error, software/media failure, or disaster, should be clearly defined and agreed upon to ensure the longevity of a dataset. Mechanisms, schedules, frequency and types of backups, and appropriate recovery plans should be specified and planned. This can include types of storage media for onsite backups and whether off-site backing up is necessary.

Archiving of data should be a priority data management issue. Organizations with high turnovers of staff and data stored in a distributed manner need sound documenting and archiving strategies built into their information management chain. Snapshots (versions) of data should be maintained so that rollback is possible in the event of corruption of the primary copy and backups of that copy.

In addition, the security professional needs to consider the costs associated with the deployment and management of the data throughout its lifecycle in the organization. For instance, the hardware cost for a deployment of a dataset managed on a Microsoft SQL server cluster or an Oracle server cluster will be higher if that deployment is done onsite versus through a cloud provider via an IaaS solution. However, the operational costs associated with providing access to the dataset over the lifecycle of its use will be potentially higher for the cloud-based deployment than for the onsite deployment. It is up to the security architect and the security professional to work together to document and help the organization understand the cost issues associated with the security solution but also the overall costs associated with platform choices due to security considerations.

## Longevity and Use

### Data Security
Security involves the system, processes, and procedures that protect a database from unintended activity. Unintended activity can include misuse, malicious attacks, inadvertent mistakes, and access made by individuals or processes, either authorized or unauthorized. Physical equipment theft or sabotage is another consideration. Accidents and disasters (such as fires, hurricanes, earthquakes, or even spilled liquids) are another category of threat to data security. Efforts should be made by the security practitioner to stay current on new threats so that a database and its data are not put at risk. Appropriate measures and safeguards should be put in place for any feasible threats.

Security should be implemented in layers using a defense in depth architecture and should never rely on a single method. Several methods should be used: for example, uninterruptible power supply, mirrored servers (redundancy), backups, backup integrity testing, physical access controls, network administrative access controls, firewalls, sensitive data encryption, up-to-date software security patches, incident response capabilities, and full recovery plans. Where possible, any implemented security features should be tested to determine their effectiveness.

Risk management is the process that allows Information Technology (IT) managers to balance the operational and economic costs of protective measures with gains in mission capability by protecting the IT systems and data that support their enterprises’ missions. Risk management encompasses three processes:
- 1. Risk Assessment
- 2. Risk Mitigation
- 3. Evaluation and Assessment

Minimizing negative impact on an enterprise and the need for a sound basis in decision making are the fundamental reasons enterprises implement a risk management process for their IT systems.

Risk assessment is the first process in the risk management methodology. Enterprises use risk assessment to determine the extent of the potential threat and the risk associated with an IT system throughout its system development life cycle. The output of this process helps to identify appropriate controls for reducing or eliminating risk during the risk mitigation process. Risk is a function of the likelihood of a given threat-source’s exercising of a particular potential vulnerability and the resulting impact of that adverse event on the enterprise. To determine the likelihood of a future adverse event, one must analyze threats to an IT system in conjunction with the potential vulnerabilities and the controls in place for the IT system. Impact refers to the magnitude of harm that could be caused. The level of impact is governed by the potential mission impacts and in turn produces a relative value for the IT assets and resources affected (e.g., the criticality and sensitivity of the IT system components and data).

Risk mitigation, the second process of risk management, involves prioritizing, evaluating, and implementing the appropriate risk-reducing controls recommended from the risk assessment process. Because the elimination of all risk is usually impractical or close to impossible, it is the responsibility of senior management and functional and business managers to use the least-cost approach and implement the most appropriate controls to decrease mission risk to an acceptable level, with minimal adverse impact on the enterprise’s resources and mission.

In most enterprises, the information system itself will continually be expanded and updated, its components changed, and its software applications replaced or updated with newer versions. In addition, personnel changes will occur and security policies are likely to change over time. These changes mean that new risks will surface and risks previously mitigated may again become a concern. Thus, the risk management process is ongoing and evolving.

## Data Access, Sharing, and Dissemination
Data and information should be readily accessible to those who need them or those who are given permission to access them. Some issues to address with access to data and a database system include:
- Relevant data policy and data ownership issues regarding access and use of data
- The needs of those who will require access to the data
- Various types and differentiated levels of access needed and as deemed appropriate
- The cost of actually providing data versus the cost of providing access to data
- Format appropriate for end-users
- System design considerations, including any data (if any) that requires restricted access to a subset of users
- Issues of private and public domain in the context of the data being collected
- Liability issues should be included in the metadata in terms of accuracy, recommended use, use restrictions, etc.
- A carefully worded disclaimer statement can be included in the metadata so as to free the provider, data collector, or anyone associated with the dataset of any legal responsibility for misuse or inaccuracies in the data.
- Where the data is when at rest, and if there are legal or jurisdictional issues specific or peculiar to that geography that must be taken into account.
