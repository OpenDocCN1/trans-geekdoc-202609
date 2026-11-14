
TABLE 4.1 Azure Compliance (continued)

| Classification | Compliance offering |
| :--- | :--- |
| | - FSA (Denmark)<br>- GLBA (US)<br>- KNF (Poland)<br>- MAS and ABS (Singapore)<br>- NBB and FSMA (Belgium)<br>- OSFI (Canada)<br>- OSPAR (Singapore)<br>- PCI 3DS<br>- PCI DSS<br>- RBI and IRDAI (India)<br>- SEC 17a-4 (US)<br>- SEC Regulation SCI (US)<br>- SOX (US)<br>- TruSight |
| Healthcare and life sciences | - ASIP HDS (France)<br>- EPCS (US)<br>- GxP (FDA 21 CFR Part 11)<br>- HIPAA (US)<br>- HITRUST<br>- MARS-E (US)<br>- NEN 7510 (Netherlands) |
| Media | - CDSA<br>- MPA<br>- FACT (UK)<br>- DPP (UK) |
| Energy | - NERC (US) |
| Education | - FERPA (US) |
| Automotive | - TISAX |
| Telecommunications | - GSMA |
| Azure Regional – Americas | Argentina PDPA |
| | Canada privacy laws |
| | Canada Protected B |
| | US CCPA |
| Azure Regional – Asia Pacific | Australia IRAP |
| | China GB 18030 |
| | China DJCP (MLPS) |
| | China TCS |
| | India MeitY |
| | Japan CS Gold Mark |
| | Japan ISMAP |
| | Japan My Number Act |
| | Korea K-ISMS |
| | New Zealand ISPC |
| | Singapore MTCS |
| Azure Regional – EMEA | EU Cloud CoC |
| | EU EN 301 549 |
| | ENISA IAF |
| | EU GDPR |
| | EU Model Clauses |
| | Germany C5 |
| | Germany IT-Grundschutz workbook |
| | Netherlands BIR 2012 |
| | Qatar NIA |
| Azure Policy regulatory compliance built-in initiatives | Australian Government ISM PROTECTED |
| | Canada Federal PBMM |
| | CIS Azure Foundations Benchmark |
| | FedRAMP High |
| | HIPAA HITRUST |
| | IRS 1075 |
| | ISO 27001 |
| | PCI DSS |
| | NIST SP 800-171 |
| | UK OFFICIAL and UK NHS |

Table 4.1 shows that compliance is fundamental to Azure. Microsoft put a lot of effort into providing Microsoft customers with the most extensive and comprehensive compliance offerings available in the cloud computing industry.

The compliance resources include audit reports, privacy information, compliance implementations, mappings, white papers, and analyst reports. You must log in to your Azure cloud service to access Azure Resources. Country and region privacy and compliance guidelines are also available.

A workload may be subject to regulatory requirements that require operational data, such as application logs and metrics, to remain within a particular geographical region.

In addition to requiring strict security measures, these requirements impact the selection, configuration, and scheduling of specific PaaS and SaaS services. They also have implications for how workloads should be operationalized.

As a true lasting transformation doesn't happen overnight, cloud governance results from an ongoing adoption effort. In some industries, third-party compliance affects initial policy creation, so assessing risk tolerance is critical in creating minimally invasive policies governing cloud adoption and managing risks.

The purpose and scope of these standards and regulations vary. Regulatory organizations frequently publish standards and updates that define good security practices to prevent negligence. However, data protection and retention design, network access, and system security can be influenced by security requirements.

## Review the Organization Requirements

To help organizations avoid negligence, regulatory organizations should regularly review and publish standards and updates that define good compliance practices. Nevertheless, compliance requirements can influence the design of data protection and retention, network access, and system security. These standards and regulations’ purpose and scope vary according to industry or country.

Today's globalized world demands that you know if your cloud resources comply with country standards mandated by governments or industry organizations.

For example, credit card transactions are governed by Payment Card Industry (PCI) standards, which prohibit Internet access into any system component storing cardholder data.

The following options can be used to deploy a restrictive environment:

- Provide your own virtual network (VNet) for the workload hosted in a different Azure compute option.
- By using private endpoints, you can remove all Internet-facing endpoints.
- Inbound and outbound access rules should be defined using network security groups (NSGs).

There may be more business impacts if you don't comply with a standard. Review the standard thoroughly to learn each requirement's intent and literal wording.

- What are the methods for measuring compliance?
- The workload must meet the requirements, but who approves it?
- Attestations can be obtained through what processes?
- What are the documentation requirements?

## Microsoft-Recommended Action

Assess your current compliance score with Microsoft Defender for Cloud and identify the gaps. With Microsoft Defender for Cloud, you can streamline the process of meeting regulatory compliance requirements using the regulatory compliance dashboard. Defender for Cloud continually assesses your hybrid cloud environment to identify the risk factors based on the controls and best practices applied to your subscriptions. Your compliance status is reflected on the dashboard.

Microsoft cloud security benchmarks are automatically assigned to Azure subscriptions when Defender for Cloud is enabled. Based on CIS, PCI-DSS, and NIST controls, this widely acknowledged benchmark emphasizes cloud-centric security controls.

Your regulatory compliance dashboard summarizes all the assessments for the standards and regulations you have selected in your environment. You will improve your compliance posture as you implement the recommendations and reduce the risk factors in your environment.

This regulatory compliance dashboard displays all the requirements associated with your selected compliance standards and the corresponding security assessments. Compliance with the standard is reflected in the status of these assessments.

You can use the regulatory compliance dashboard to assist you in identifying gaps in compliance with the standards and regulations you have chosen. By focusing on compliance within dynamic cloud and hybrid environments, you will also be able to monitor compliance over time.

The regulatory compliance dashboard can be used to investigate any issues that may be impacting your compliance.

There are both automated and manual assessments within regulatory compliance that may require remediation. Resolve regulatory compliance recommendations directly within the regulatory compliance dashboard using the information provided.

## Design a Compliance Strategy

A Microsoft Cybersecurity Architect can develop a regulatory compliance strategy once the business risks are mapped and converted into policy statements. Additionally, this strategy considers the type of transaction an organization performs or the industry to which it belongs. A good compliance strategy needs to ensure that security controls are implemented to map regulatory compliance requirements directly; that’s why it’s crucial to establish a regulatory compliance strategy with a thorough understanding of the type of business, transactions, and overall business requirements.

Working with your regulators and carefully reviewing the standard to understand the language and intent of each requirement is key to avoiding fines or other business impacts down the road.

The corporate policy creates the working definition of governance in traditional and incremental governance.

Figure 4.1 depicts the value exchange between business risk, policy, compliance, monitoring processes, and enforcement processes to create a governance strategy.

## FIGURE 4.1 Microsoft's five cybersecurity disciplines of cloud governance

![](img/5ab9852bf401dd309bf0f81797a91445_199_0.png)

Most IT governance actions strive to deploy technology that monitors, enforces, operates, and automates those organization policies; and cloud governance is built on similar concepts. You can use the five disciplines shown in Figure 4.1 to develop a cloud governance strategy.

**Cost Management** Developing cost control policies for all cloud platforms is a primary concern for cloud users.

**Security Baseline** A company’s security requirements are unique. Once these requirements are established, cloud governance policies and enforcement apply the conditions across networks, data, and assets.

**Resource Consistency** Managing onboarding, drift, discoverability, and recovery risks in the cloud requires consistent resource configuration. With governance tooling, resources can be configured consistently.

**Identity Baseline** By applying identity requirements consistently across cloud adoption efforts, the Identity Baseline discipline reduces the risk of breach.

**Deployment Acceleration** Centralization, standardization, and consistency in deployment and configuration methods improve governance approaches. When delivered through cloud-based governance tooling, they complete a cloud factor that can accelerate deployment actions.

In the organization policy definition phase, you will consult with the organization to coordinate risk tolerance and cost mitigation. You will investigate current cloud adoption plans and data classification in this phase.

To create minimally intrusive policies to govern cloud adoption and manage risks, you must determine the business risks and assess risk tolerance. Remember that third-party compliance can affect some industries’ initial policy creation process. As adoption and innovation activities progress, policy violations will naturally occur, and monitoring and enforcing policy compliance will be easier if relevant processes are executed.
