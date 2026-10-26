
these. To understand this landscape, a CCSP must first recognize the difference between data protected by legal regulations and data protected by contract.

- **Statutory requirements** are required by law.
  - U.S. federal laws, such as HIPAA, GLBA, and SOX outlined in the previous section
  - Additional federal laws such as the Family Education Rights and Privacy Act (FERPA), which deals with privacy rights for students, and the Federal Information Security Management Act (FISMA), which protects federal data privacy
  - State data privacy laws, which now exist in all 50 states as well as U.S. territories
  - International laws, which we will discuss in a later section covering country-specific laws

- **Regulatory requirements** may also be required by law, but refer to rules issued by a regulatory body that is appointed by a government entity.
  - In the United States, many regulatory examples exist, mostly dealing with contractor compliance to do business with the government. An example would be security requirements outlined by NIST that are necessary to handle government data (such as NIST 800-171).
  - At the state level, several states use regulatory bodies to implement their cybersecurity requirements. One example is the New York State Department of Financial Services (NY DFS) cybersecurity framework for the financial industry (23 NYCRR 500).
  - There are numerous international requirements dealing with cloud legal requirements (including APEC and GDPR).

**Contractual requirements** are required by a legal contract between private parties. These are not laws, and breaching these requirements cannot result in imprisonment (but can result in financial penalties, litigation, and terminations of contracts). Common contractual compliance requirements include the following:

- Payment Card Industry Data Security Standard (PCI DSS)
- Financial Industry Regulatory Authority (FINRA)
- Service Organization Controls (SOC)
- Generally Accepted Privacy Principles (GAPP)
- Center for Internet Security (CIS) Critical Security Controls (CSC)
- Cloud Security Alliance (CSA) Cloud Controls Matrix (CCM)

any investigation? Can a law enforcement agency compel you to provide data housed in another country? All of these questions make cloud eDiscovery a distinct challenge.

## eDiscovery Considerations

When you’re considering a cloud vendor, eDiscovery should be considered during any contract negotiation phase. If you think about your cloud providers today, can you recall how many conversations you might have had with their support teams? Would you know who to contact if an investigation was needed?

To pose another question, do you actually know where the data is physically housed? Many companies make use of the incredible replication and fail-over technologies of the modern cloud, but that means data may be in different time zones, countries, or continents when an investigation is launched. As we have outlined, laws in one country or state may in fact clash or break with laws of another. It is the duty of the cloud security profession to exercise due care and due diligence in documenting and understanding to the best of their ability the relevant laws and statutes pertaining to an investigation prior to it commencing.

In some cases, proactive architectural decisions can simplify issues down the road. For example, if a company chooses to house customer data within their legally defined jurisdiction (for example, EU citizen data is always housed on cloud servers within the EU), it can simplify any potential investigations or jurisdictional arguments that might arise.

## Conducting eDiscovery Investigations

Where there is a problem in technology, there is usually a solution, and the marketplace for eDiscovery tools has grown commensurately with the explosion in the use of cloud service providers. There are a healthy number of vendors that specialize in this area. For a CCSP, it is important to learn about eDiscovery actors when evaluating contracts and service level agreements (SLAs) to determine what forms of eDiscovery are permissible. These are the main types of investigatory methods:

- **SaaS-based eDiscovery:** Why not use the cloud to perform eDiscovery on the cloud? These tools from a variety of vendors are used by investigators and law firms to collect, preserve, and review data.
- **Hosted eDiscovery:** In this method, your hosting provider includes eDiscovery services in the contractual obligations that can be exercised when and if necessary. This may limit a customer to a preselected list of forensic solutions, as CSPs are often wary of customer-provided tools due to the potential for affecting other cloud customers during the process.
- **Third-party eDiscovery:** When there are no obligations in a contract, a third party may be contracted to perform eDiscovery operations. In this model, the CCSP must work especially closely with the third party to provide appropriate access to necessary resources in the cloud.

## Cloud Forensics and Standards

As you can see, the forensic and eDiscovery requirements for many legal controls are greatly complicated by the cloud environment. Unlike on-premises systems, it can be difficult or impossible to perform physical search and seizure of cloud resources such as storage or hard drives. Standards from bodies such as the International Organization for Standardization (ISO)/International Electrotechnical Commission (IEC) and the Cloud Security Alliance (CSA) provide guidance to cloud security practitioners on best practices for collecting digital evidence and conducting forensics investigations in cloud environments. CCSPs should be familiar with the following standards:

- **Cloud Security Alliance:** The CSA Security Guidance Domain 3: Legal Issues: Contracts and Electronic Discovery highlights some of the legal aspects raised by cloud computing. Of particular importance to CCSPs are the guidance provided on negotiating contracts with cloud service providers in regard to eDiscovery, searchability, and preservation of data.
- **ISO/IEC 27037:2012:** This provides guidelines for the handling of digital evidence, which include the identification, collection, acquisition, and preservation of data related to a specific case.
- **ISO/IEC 27041:2014-01:** This provides guidance on mechanisms for ensuring that methods and processes used in the investigation of information security incidents are “fit for purpose.” CCSPs should pay close attention to sections on how vendor and third-party testing can be used to assist with assurance processes.
- **ISO/IEC 27042:2014-01:** This standard is a guideline for the analysis and interpretation of digital evidence. A CCSP can use these methods to demonstrate proficiency and competence with an investigative team.
- **ISO/IEC 27043:** The security techniques document covers incident investigation principles and processes. This can help a CCSP as a “playbook” for many types of incidents, including unauthorized access, data corruption, system crashes, information security breaches, and other digital investigations.
- **ISO/IEC 27050-1:** This standard covers electronic discovery, the process of discovering pertinent electronically stored information involved in an investigation.

## UNDERSTANDING PRIVACY ISSUES

The Internet age has brought with it an unprecedented amount of information flow. Knowledge (and cat videos) is shared by billions of Internet-connected humans at the speed of light around the world every day. The flow of information is two-way, however,

Regulations are put into place by governments and government-empowered agencies to protect entities and individuals from risks. In addition, they force providers and processors to take appropriate measures to ensure protections are in place while identifying penalties for lapses in procedures and processes.

One of the major differentiators between contracted and regulated privacy data is in breach reporting. A data breach of regulated data (or unintentional loss of confidentiality of data through theft or negligence) is covered by myriad state and federal laws in the United States. There are now data privacy laws covering PII in all 50 states, with legislative changes happening every year. Some states have financial penalties of as little as $500 for data privacy violations, while others have fines in the hundreds of thousands of dollars as well as prison time for company officers. The largest state fine for a data privacy breach was handed to Uber for a 2016 breach and totaled over $148 million dollars in fines to the state of California.

## Components of a Contract

As we have detailed, the outsourcing of services to a cloud service provider in no way outsources the risk to the company as the data owner. A CCSP must be familiar with key concepts when contracting with cloud service providers to ensure that both parties understand the scope and provisions when private data is concerned. Key contract areas include the following:

- **Scope of data processing:** The provider must have a clear definition of the permitted forms of data processing. For example, data collected on user interactions for a cloud customer should not be used by the CSP to inform new interface designs.
- **Subcontractors:** It is important to know exactly where all processing, transmission, storage, and use of data will take place and whether any part of the process might be undertaken by a subcontractor to the cloud service provider. If a subcontractor will be used in any phase of data handling, it is vital that the customer is contractually informed of this development.
- **Deletion of data:** How data is to be removed or deleted from a cloud service provider is important and helps protect against unintentional data disclosure. In the old days, data was often physically destroyed (with a screwdriver through a hard drive). In the cloud environment, that is next to impossible, so contracts must spell out the methods that data is to be securely removed from any environment (and subcontractor environment). One example is cryptoshredding, or rendering data inaccessible by cryptographic methods.
- **Data security controls:** If data requires a level of security controls when it is processed, stored, or transmitted, that same level of security control must be ensured
