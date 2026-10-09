
![](img/625475237d5c9b4148fda1077938a911_44_0.png)

The reference structure, depicted in Figure 2.4, defines five main “actors” concerning the functions and responsibilities as described in the list that follows:

- **Cloud user:** An individual or company that keeps a business relationship with, and utilizes services out of, CPs.
- **Cloud supplier:** An individual, company, or entity responsible for creating a service available to interested parties.
- **Cloud auditor:** It runs the individual assessment of cloud solutions, data system operations, functionality, and safety of the cloud execution.
- **Cloud agent:** An entity that manages the usage, functionality, and shipping of cloud solutions, and negotiates connections between CPs and cloud customers.
- **Cloud Inc.:** An intermediary that provides transport and connectivity of cloud solutions from CPs to cloud customers.

The functions of this cloud consumer and supplier have been discussed. To summarize, a CP can supply at least one of the cloud solutions to fulfill IT and business demands of cloud customers. For all the three service versions (SaaS, PaaS, and IaaS), the CP supplies the processing and storage facilities required to support the service version, together with a cloud port for cloud support customers. For SaaS that the CP deploys, it configures, maintains, and upgrades the performance of their software programs on cloud infrastructure, so the services are provisioned in the anticipated service amounts to cloud customers.

The customers of SaaS may be organizations that offer their members using applications, software applications, or applications program administrators who configure software for end users. For PaaS, the CP oversees the computing infrastructure to its platform and conducts the cloud applications that offer the parts of the platform, including runtime program implementation heap, databases, and other middleware components. Cloud users of PaaS can use the resources and implementation resources supplied by CPs to create, install, test, and manage the software hosted on a cloud atmosphere. For IaaS, the CP accelerates the computing tools underlying the support, such as the servers, storage, networks, and hosting infrastructure.

The IaaS cloud user consequently employs these computing tools, like computer, for their necessary computing requirements. The cloud provider is a media facility that offers transport and connectivity of cloud solutions between cloud customers and CPs. Usually, a CP will install SLAs using a cloud provider to provide services following the degree of SLAs provided to cloud customers and might require the cloud provider to offer secure and dedicated connections between cloud customers and CPs. A cloud agent is helpful when CPs are too complicated to get a cloud user to handle readily. A cloud agent could offer two regions of service:

- **Service aggregation:** The agent combines multiple cloud solutions to fulfill customer needs not addressed explicitly with one CP, to maximize performance, or to decrease cost.
- **Service arbitrage:** This is much like support aggregation except that the professional services being aggregated are not fixed. Support arbitrage means a broker has the flexibility to select services from several agencies. As an example, the cloud agent could utilize credit-scoring support to quantify and pick a service using the best score.

A cloud auditor may assess the services offered using a CP concerning security controllers, privacy impact, functionality, and so on. The auditor is an independent entity which could guarantee the CP conforms to some criteria. Figure 2.5 illustrates the connections between the “actors.”

A cloud user may ask cloud solutions out a CP directly or by using a cloud agent. A cloud auditor conducts independent audits and might get in touch with others to gather necessary information. This figure demonstrates

![](img/625475237d5c9b4148fda1077938a911_46_0.png)

Figure 2.5. Cloud “actors” connections

that cloud networking problems involve three distinct kinds of networks. For a cloud manufacturer, the system structure is that of a standard large information center, which is made up of racks of high-performance servers and storage apparatus, connected with high-speed top-of-rack Ethernet switches. The business network is very likely to possess a different structure, typically including numerous LANs, servers, workstations, PCs, and mobile devices, using a wide selection of network functionality, safety, and management problems. The concern of the consumer and producer concerning the cloud provider, which can be shared with many customers, is the capacity to create virtual networks, together with appropriate SLAs and safety guarantees.

## 2.10. CLOUD PROVIDER ARCHITECTURAL COMPONENTS

Figure 2.4 shows four primary architectural components of the CP. Service orchestration denotes the composition of program components to support the CPs' actions in structure, coordination, and management of computing resources to provide cloud services to cloud consumers. The orchestration is shown as a three-layer architecture. We see here the simple mapping of physical resources to consumer-visible services by a resource abstraction layer. Examples of resource abstraction elements include software elements, for example, hypervisors, virtual machines, virtual information storage, and other computing resource abstractions. Cloud service management contains each of the service-related functions that are essential for the management and operation of those services required by or proposed to cloud customers. It covers three main areas:

**Business service:** This comprises business-related services dealing with clients, such as bookkeeping, billing, reporting, and auditing.

**Provisioning/configuration:** This includes automated tools for rapid deployment of cloud systems for customers, adjusting resource and configuration assignment, and tracking and reporting on resource usage.

**Portability/interoperability:** Consumers are interested in cloud offerings which encourage data and system portability, and service interoperability. This is very useful in a hybrid environment, in which the consumer may wish to alter the allocation of information and software between on-premises and off-premises sites.

Security is a concern that crosses all layers of this reference architecture, which range from physical security to application security. As such, it is the joint responsibility of all of the cloud “actors,” not only CPs. Privacy additionally encompasses all layers of this reference architecture. The critical requirement concerning privacy is that CPs provide adequate and guaranteed protection of personal information (PI) and personally identifiable information (PII) from the cloud.

## 2.11. ITU-T CLOUD COMPUTING REFERENCE ARCHITECTURE

It is beneficial to check at an alternative reference structure, published in ITU-T Y.3502 (International Telecommunication Union 2014). This architecture is somewhat broader in scope compared to NIST structure and views it as a layered functional architecture.

### 2.11.1. CLOUD COMPUTING “ACTORS”

Before taking a look at the four-layer benchmark architecture, we need to understand the differences between NIST and ITU-T in defining cloud “actors.” The ITU-T document defines the three “actors” as follows:

- **Cloud support customer or consumer**: A party that is in a business relationship to utilize cloud solutions. The business relationship is using a cloud service provider or a cloud support spouse.

Critical actions for a cloud support customer include but are not limited to, utilizing cloud solutions, performing company administration, and administering utilization of cloud solutions.

- **Cloud service supplier**: A party that produces cloud services out there. The cloud service provider targets tasks that are necessary to provide a cloud service and actions that are necessary to ensure its delivery to the cloud service customer in addition to cloud support maintenance. The cloud service provider includes a comprehensive set of activities (e.g., provide service, deploy and track service, handle business plan, provide audit information, etc.) as well as many sub-roles (e.g., company manager, service manager, network provider, security and risk manager, and the like).

- **Cloud service partner**: A party that is engaged in service of, or auxiliary to, activities of either the cloud service provider or the cloud service client, or even both. A cloud service spouse's activities vary depending on the kind of spouse and their relationship with the cloud service provider and the cloud service customer. Cases of cloud service partners include cloud auditor and cloud support agent.

Therefore, the cloud service spouse combines but is not limited to, the NIST functions of agent and auditor. Figure 2.6 depicts the main “actors” with some of their possible characters in a cloud ecosystem.

![](img/625475237d5c9b4148fda1077938a911_48_0.png)

CSN = Cloud service partner
CSP = Cloud service provider
CSU = Cloud service user

Figure 2.6. Cloud ecosystem
