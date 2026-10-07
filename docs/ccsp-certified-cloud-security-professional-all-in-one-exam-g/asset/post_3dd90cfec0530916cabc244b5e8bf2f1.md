
[content]
# CCSP Certified Cloud Security Professional All-in-One Exam Guide
360

C. Baselines are set configuration standards and requirements that apply to a system or application. Baselines are often part of regulatory or legal requirements and oftentimes followed by industry standard guidelines.

A is incorrect because images form the basis for virtual machines, but are the end result of applied configurations and requirements, not the mechanism for applying or ensuring their compliance.

B is incorrect because repudiation deals with the verifiability of an individual and proof of their activities, and does not have any impact or bearing on system configurations or regulatory requirements, though repudiation and nonrepudiation may be terms of regulatory requirements.

D is incorrect because interoperability has to do with the ability of systems or applications to reuse components or code to make development simpler, more granular and efficient, and less costly. It does not have anything to do with regulatory requirements or their enforcement.

- 50. Your company has been served with an eDiscovery order to collect event data and other pertinent information from your application during a specific period of time, to be used as potential evidence for a court proceeding. Which of the following, apart from ensuring that you collect all pertinent data, would be the MOST important consideration?
  - A. Encryption
  - B. Chain of custody
  - C. Compression
  - D. Confidentiality

B. When a company is dealing with eDiscovery orders, the chain of custody is extremely important as it pertains to official legal proceedings. The chain of custody documents everyone who has possession of the data, in what format, and for what reasons. For data to be admissible for legal proceedings, the chain of custody is vital in showing that nothing has been tampered with and that everyone in possession of the data can be questioned and investigated, if needed.

A is incorrect although encryption may be used as part of eDiscovery to sign, preserve, and protect any evidence that is collected and turned over, especially if the data is sensitive, in general it is not a required element of eDiscovery.

C is incorrect although compression may be used when preserving and submitting evidence pursuant to the order, it is not a requirement element and will have no bearing on the overall process of eDiscovery.

D is incorrect because confidentiality may or may not be a factor with eDiscovery, depending on the nature of the data requested and the types of systems involved.

# 51. Which of the following concepts will ensure that no single host or cloud customer can consume enough resources to impact other users on the same system?
  - A. Limits
  - B. Multitenancy
  - C. Reservations
  - D. Shares

A. Limits are put in place to enforce the maximum amount of compute resources that any one tenant or system can consume. The limits can be placed on various levels and units, ranging from a specific virtual machine to a cloud customer for the aggregate of their utilization across all systems. They are designed to ensure that no single host or cloud customer utilize enormous resources that would ultimately make the cloud provider unable to properly allocate resources and serve the needs of other customers.

B is incorrect because multitenancy is the larger concept that deals with hosting multiple, different cloud customers within the same cloud environment. While it is certainly the driving reason why the need for balancing allocations is necessary, concept itself does not play into the specific details of implementations like this.

C is incorrect because a reservation is the minimum amount of resources guaranteed to a cloud customer within the environment. Typically guarantee to a cloud customer that they will have the minimum required resources necessary to power and operate their services within the environment. Reservations also offer insurance against denial-of-service (DoS) attacks or other customers using such large amounts of resources that the cloud cannot operate their services.

D is incorrect because shares are focused on cloud customers requesting resources for allocation and provisioning than are currently available in the environment. Shares establish a prioritization and weighting system, defined by the cloud provider, that determines which systems, applications, and customers will receive priority for additional resource requests when utilization is high and limited.

# 52. Which of the following roles is responsible in many organizations for overseeing access requests for data utilization and ensuring that policies are followed and proper approvals are granted?
  - A. Data owner
  - B. Data steward
  - C. Data processor
  - D. Data controller

# CCSP Certified Cloud Security Professional All-in-One Exam Guide
362

B. The data steward is responsible for overseeing an organization's policy in regard to data access, as well as for evaluating access requests and matching them with organizational policy to ensure compliance and proper use. If the business process is acceptable, the data steward is responsible for ensuring that appropriate approvals have been obtained and documented well.

A is incorrect because the data owner has final authority and responsibility over data policies, and the data steward is the position designated for directly carrying out those duties. The data owner is responsible for establishing the risk management approach to data security and access in conjunction with management and then matching this to the organizational policies or regulatory requirements.

C is incorrect because the data processor is the one who actually uses the data within an application or service. As the consumer of the data, the data processor does not play a role in granting data access or policy enforcement.

D is incorrect because the term data controller is synonymous with data owner; they have the same duties and responsibilities.

- 53. Which of the following is directly part of the "metered" costs associated with PaaS?
  - A. Staffing
  - B. Development
  - C. Licensing
  - D. Auditing

C. With PaaS, the cloud provider is giving the cloud customer a fully functioning environment, including the operating system and any middleware or application framework components. As part of the services, the licensing costs and tracking are the responsibility of the cloud provider and are factored into the metered costs of the cloud customer.

A is incorrect because staffing comes in many different forms, with many different parties involved. Within cloud computing, although the cloud provider has staffing to maintain the environment, due to self-service provisioning, staffing is not needed as additional virtual machines are brought online or new services provided; this is all handled through automated processes.

B is incorrect because development is not part of the services from a cloud provider, nor is it included in the costs of the cloud provider for cloud services. Development would be done under its own contract, or possibly even under contracts that incorporate the costs of the cloud hosting services as well. However, it would not be a direct part of the metered services from the cloud provider as additional resources are allocated or provisioned.

D is incorrect because auditing is part of all cloud server categories and is documented in the contract and SLA requirements. It is not a specific part of any one category over another, though it can differ in scope based on the specific category used. Regardless, it does not relate to the metered costs of any cloud category.

54. Many highly regulated data types and systems will have specialized regulatory requirements that extend further than the regulatory requirements that apply to all data. Which of the following is *NOT* a specialized regulatory framework that has compliance requirements?
  - A. FedRAMP
  - B. HIPAA
  - C. FIPS 140-2
  - D. PCI DSS

C is incorrect because FIPS 140-2 is a certification for cryptographic modules based on the specific needs and requirements for the level of encryption and the protection of it. It is based on both software and hardware requirements and the level of control, features, and protections each have. It is not a regulatory framework with compliance requirements.

A is incorrect because FedRAMP is a regulatory framework that the United States federal government uses to assess and certify cloud services for their use by federal agencies. As of FedRAMP, there is a certification process for low and moderate systems, as well as high systems of 2016, to meet requirements and auditing. One aspect of FedRAMP is that it was designed for use by any federal agency once proper been certified, removing the need for each to conduct their own certifications and audits of the cloud services providers. FedRAMP is available for civilian agencies and can be used for data and systems other than for national defense.

B is incorrect because HIPAA relates to regulated healthcare and personal data within the United States, and sets strict and extensive requirements for how it must be protected. It is specialized for healthcare and supersedes any other regulatory requirements to which a system or data might be subjected. As part of HIPAA regulations, data controllers are subjected to increased scrutiny for the methods and processes they use to protect personal and patient data.

D is incorrect because PCI DSS is an industry-specific regulation and oversight framework, established by the major credit card companies and networks, and is a requirement for any business that conducts transactions over those networks.
