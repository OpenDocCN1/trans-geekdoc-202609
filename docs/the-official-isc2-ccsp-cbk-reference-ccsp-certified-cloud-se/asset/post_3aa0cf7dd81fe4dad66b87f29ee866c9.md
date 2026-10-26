
- Identifying the current state of the department or area (which involves the evaluation of the department to understand current state, generally involving research and interviews of employees).
- Reviewing evidence and supporting documentation, including the verification of statements and data.
- Identifying the “gaps” between the framework and reality. This highlights the risks to the organization.
- Preparing a report detailing the findings and getting sign-off from the appropriate company leaders.

Since a gap analysis provides measurable deficiencies and, in some cases, needs to be signed off by senior leadership, it can be a powerful tool for an organization to identify weaknesses in their efforts for compliance.

## Audit Planning

Any audit, whether related to financial reporting, compliance, or cloud computing, must be carefully planned and organized to ensure that the results of the audit are relevant to the objectives. Audits generally consist of four phases, outlined in Figure 6.1.

## Audit Process

![](img/31b2d0f6902e5b79691e4de3b480b89a_275_0.png)

FIGURE 6.1 Four phases of an audit

The four phases of an audit consist of the following:

- **Audit planning**
  - Documentation and definition of audit objectives. This process is a collaborative effort to define what standards are being measured.

## Benefits of an ISMS

Though the function of an ISMS can vary from industry to industry, there are a number of benefits to implementation that hold true across all industries.

- **Security of data in multiple forms**: An ISMS will help protect data in all forms, whether paper, digital, or cloud based.
- **Cyber attacks**: Having an ISMS will make an organization more resilient to cyber attacks by having best practices in security in place throughout the operation.
- **Central information management**: An ISMS will put in place centralized frameworks for managing information, reducing shadow systems, and easing the burden of data protection.
- **Risk management**: Having a codified set of processes and procedures in place will reduce operational risks in a number of areas, including information security, business continuity, and adapting to evolving security threats.

As with any major organizational element, an ISMS requires buy-in from company leadership to be effective. In the cloud computing environment, an ISMS is extremely valuable in requiring detailed documentation on cloud provider environments and change logging.

## Internal Information Security Controls System

As we have detailed a number of times in this section, the International Standards Organization (ISO) provides an invaluable resource to security professionals in its ISO 27001:2013 information security standards. (See www.iso.org/obp/ui/#iso:std:iso-iec:27001:ed-2:v1:en.) Cloud security professionals should be intimately familiar with ISO 27001 controls, which can be mapped to address requirements for audit, ISMS, or other compliance measures. The 14 control sets of Annex A of ISO 27001 are as follows:

- **A.5 Information security policies**: How policies are written and reviewed
- **A.6 Organization of information security**: The assignment of responsibilities for specific tasks
- **A.7 Human resource security**: Ensuring that employees understand their responsibilities prior to employment and once they’ve left or changed roles
- **A.8 Asset management**: Identifying information assets and defining appropriate protection responsibilities
- **A.9 Access control**: Ensuring that employees can only view information that’s relevant to their job role
- **A.10 Cryptography**: The encryption and key management of sensitive information
- **A.11 Physical and environmental security**: Securing the organization’s premises and equipment
- **A.12 Operations security**: Ensuring that information processing facilities are secure
- **A.13 Communications security**: How to protect information in networks
- **A.14 System acquisition, development and maintenance**: Ensuring that information security is a central part of the organization’s systems
- **A.15 Supplier relationships**: The agreements to include in contracts with third parties and how to measure whether those agreements are being kept
- **A.16 Information security incident management**: How to report disruptions and breaches and who is responsible for certain activities
- **A.17 Information security aspects of business continuity management**: How to address business disruptions
- **A.18 Compliance**: How to identify the laws and regulations that apply to your organization

In addition, cloud security professionals in the United States should be familiar with the National Institute of Standards (NIST) cybersecurity framework (v1.1). This framework identifies controls in these five broad areas:

- Identify
- Protect
- Detect
- Respond
- Recover

A common mnemonic used to remember the NIST CSF control areas is “In Public, Drink Reasonably Responsibly.” See the following site for complete details: www.nist.gov/cyberframework/online-learning/five-functions.

## Policies

Policies are a key part of any data security strategy. Without a policy in place, it is impossible to enforce requirements in any systematic way. Policies ensure that employees and management are aware of what is expected of them and where their responsibilities lie. Policies are an important piece of standardizing practices in an organization.

From a cloud computing perspective, policies can be an important tool in preventing isolation of activities (for treating data stored in one cloud provider in a completely different way than others). Policies also provide a way for leadership to specify appropriate uses of cloud services to ensure the organization realizes business benefits without also taking on additional business risk.

## Organizational Policies

Companies use policies and procedures to outline rules as well as outline courses of action to deal with problems. Organizations use policies to make employees understand the organization’s views and values on specific issues, and what actions will occur if they are not followed. At the organizational level, policies are used to reduce the chances of the following:

- Financial losses
- Loss of data
- Reputational damage
- Statutory and regulatory compliance issues
- Abuse or misuse of computing systems and resources

## Functional Policies

A functional policy is a set of standardized definitions for employees that describe how they are to make use of systems or data. Functional policies typically guide specific activities crucial to the organization, such as appropriate handling of data, vulnerability management, and so on. These are generally codified in an operation ISMS and can consist of the following (not an exhaustive list):

- **Data classification policies**: Identifies types of data and how each should be handled
- **Network services policies**: How issues such as remote access and network security are handled
- **Vulnerability scanning policies**: Routines and limitations on internal scanning and penetration testing
- **Patch management policies**: How equipment is patched on what schedule
- **Acceptable use policies**: What is and is not acceptable to do on company hardware and networks
- **Email use policies**: What is and is not acceptable to do on company email accounts
- **Password policies**: Password complexity, expiration, reuse
- **Incident response policies**: How incidents are handled

## Cloud Computing Policies

Employee provisioned cloud services may present significant data management risks and may be subject to changes in risk with or without notice. Almost all cloud services require individual users to accept click-through agreements (which are rarely if ever read carefully). Agreements do not allow users to negotiate or clarify terms, often provide vague descriptions of services and safeguards, and often are subject to change without notice.

Cloud services should not be exempt from organizational policy application. These policies will define the requirements that users must adhere to in order to make use of the services. Because of the ease of provisioning cloud services, many organizations have specific policies in place that discourage or prohibit the use of cloud services by individuals outside of central IT oversight.

When pursuing cloud services, a security professional should pay close attention to the following:

- **Password policies:** If an organization has password policies around length, complexity, expiration, or multifactor authentication (MFA), it is important to ensure that these same requirements are met by a cloud service provider.
- **Remote access:** The same bar must be met for remote access to cloud providers as on-premises services. This may include items such as up-to-date patching, hard disk encryption, or MFA.
- **Encryption:** Policies about encryption strength and when encryption is required. Key escrow can be an important aspect of policy to focus on (for example who has the decryption keys?).
- **Data backup and failover:** Policies on data retention and backup must be enforced on cloud providers. If policies exist on data location for backups and redundancy, they must also be enforced on CSPs.
- **Third-party access:** What third parties might have access to data stored with the CSP? Can this access be logged and audited?
- **Separation of duties:** Can controls for the separation of key roles be enforced and maintained by the cloud provider?
- **Incident response:** What are the required steps in a response, including who is contacted for a variety of incidents?

In some instances, a cloud service provider cannot meet a company’s requirements when it comes to adhering to a specific policy. If this happens, it is important to consider the risks of using the provider, and any deviations from policy should be carefully documented.

## Identification and Involvement of Relevant Stakeholders

One key challenge in the provisioning of cloud computing resources is the identification of all company stakeholders that need to be involved in the decision process. Oftentimes,
