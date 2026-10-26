
## Internal and External Audit Controls

Internal audit and compliance have a key role in helping to manage and assess risk for both a cloud customer and provider. An organization may choose to keep internal audit functions within the company or outsource this function to a consultant or outside party.

Internal audit is an important line of defense for an organization. Many times, audits uncover issues with security or governance practices that can be corrected before more serious issues arise.

An internal auditor acts as a “trusted advisor” as an organization takes on new risks. In general, this role works with IT to offer a proactive approach with a balance of consultative and assurance services. An internal auditor can engage with relevant stakeholders to educate the customer about cloud computing risks (such as security, privacy, contractual clarity, Business Continuity Planning (BCP) and Disaster Recovery Planning (DRP) compliance with legal and jurisdictional issues). An internal audit also helps mitigate risk by examining cloud architectures to provide insights into an organization’s cloud governance, data classifications, identity and access management effectiveness, regulatory compliance, privacy compliance, and cyber threats to a cloud environment.

It is desirable for an internal auditor to maintain independence from both the cloud customer and the cloud provider. The auditor is not “part of the team” but rather an independent entity who can provide facts without fear of reprisals or political blowback. In addition to the advisory role, an internal auditor will generally perform audits in the traditional sense, making sure the cloud systems meet contractual and regulatory requirements and that security and privacy efforts are effective.

Security controls may also be evaluated by external auditors. An external auditor is defined as one who does not work for the firm being audited. An external audit can be required by various pieces of financial legislation as well as information security standards such as ISO 27001. An external auditor is focused on ensuring compliance and therefore does not take on the role of a “trusted advisor” but rather more of regulator with punitive capability.

## Impact of Audit Requirements

The requirement to conduct audits can have a large procedural and financial impact on a company. In a cloud computing context, the types of audit required are impacted largely by a company’s business sector, the types of data being collected and processed, and the variety of laws and regulations that these business activities subject a company to. Some entities operate in heavily regulated industries subject to numerous auditing requirements (such as banks or chemical companies). Others may be brokers of data from international data subjects (such as big tech companies like Facebook, Google, and Microsoft).

In a cloud relationship, oftentimes the ownership of security controls designed to reduce risk resides with a cloud service provider. An audit of the cloud service provider can identify if there are any gaps between what is contractually specified and what controls the provider has in place.

## Service Organization Controls

The American Institute of CPAs (AICPA) provides a suite of offerings that may be used to report on services provided by a service organization that customers can use to address risks associated with an outsourced service. See Table 6.2.

## TABLE 6.2 AICPA Service Organization Control Reports

| REPORT | USERS | CONCERNS | DETAILS REQUIRED |
|---|---|---|---|
| SOC 1 | User entities and the CPAs that audit their financial statements | Effect of the controls at the service organization on the user entities’ financial statements | Systems, controls, and tests performed by the service auditor and results of tests. |
| SOC 2 | Broad range of users that need detailed information and assurance about controls | Security, availability, and processing integrity of the systems the service organization uses to process users’ data and the confidentiality and privacy of the information processed by these systems | Systems, controls, and tests performed by the service auditor and results of tests. |
| SOC 3 | Broad range of users that need detailed information and assurance about controls but do not have the need for or knowledge to make effective use of SOC 2 reports | Security, availability, and processing integrity of the systems the service organization uses to process users’ data and the confidentiality and privacy of the information processed by these systems | Referred to as a “Trust Services Report,” SOC 3 reports are generally used and can be freely distributed. |

Table source: www.aicpa.org

The differences between the SOC reports are as follows:

- **Service Organizations Controls 1 (SOC 1)**: These reports deal mainly with financial controls and are intended to be used primarily by CPAs that audit an entity’s financial statements.

(SSAE 18) was made effective in May 2017, and added additional sections and controls to further enhance the content and quality of SOC reports.

The international counterpart of the AICPA, the International Auditing and Assurance Standards Board, issues the International Standard on Assurance Engagements (ISAE). There are a number of differences between the two standards, and a security professional should always consult the relevant business departments to determine which audit report(s) will be used when assessing cloud systems.

## Cloud Security Alliance

The Cloud Security Alliance (CSA) offers a Security Trust Assurance and Risk (STAR) certification that can be used by cloud service providers, cloud customers, or auditors and consultants to ensure compliance to a desired level of assurance. (See downloads .cloudsecurityalliance.org/assets/research/security-guidance/security-guidance-v4-FINAL.pdf.) STAR consists of three levels of certification:

- **Level 1:** Self-Assessment is a complimentary offering that documents the security controls provided by various cloud computing offerings, helping users assess the security of cloud providers they currently use or are considering using.
- **Level 2:** Attestation is a collaboration between CSA and the AICPA to provide guidelines for CPAs to conduct SOC 2 engagements using criteria from the AICPA (Trust Service Principles, AT 101) and the CSA Cloud Controls Matrix. STAR Attestation provides for rigorous third-party independent assessments of cloud providers.
- **Level 3:** Continuous monitoring through automated processes that ensure security controls are monitored and validated at all times.

## Restrictions of Audit Scope Statements

Audits are a fact of life to ensure compliance and prevent sometimes catastrophic effects of security failures. Though no employee relishes the thought of undergoing an audit, they are somewhat of a necessary evil to ensure that risks are adequately controlled and compliance is met. Any audit must be appropriately scoped to ensure that both the client and the auditor understand what is in the audit space and what is not. This is almost always driven by the type of report being prepared. An audit scope statement would generally include the following:

- Statement of purpose and objectives
- Scope of audit and explicit exclusions
- Type of audit
- Security assessment requirements
- Assessment criteria and rating scales
- Criteria for acceptance
- Expected deliverables
- Classification (for example, secret, top secret, public, etc.)

Any audit must have parameters set to ensure the efforts are focused on relevant areas that can be effectively audited. Setting these parameters for an audit is commonly known as the *audit scope restrictions*. Why limit the scope of an audit? Audits are expensive endeavors that can engage highly trained (and highly paid) content experts. In addition, the auditing of systems can affect system performance and, in some cases, require the downtime of production systems.

Scope restrictions can be of particular importance to security professionals. They can spell out the operational components of an audit, such as the acceptable times and time periods (for example, days and hours of the week) as well as the types of testing that can be conducted against which systems. Carefully crafting scope restrictions can ensure that production systems are not impacted adversely by an auditor's activity. Additionally, audit scope statements can be used to clearly define what systems are subject to audit. For example, an audit on HIPAA compliance would only include systems that process and store PHI.

## Gap Analysis

As a precursor to a formal audit process, a company may engage in a gap analysis to help identify potential trouble areas to focus on. A gap analysis is the comparison of a company's practices against a specified framework and identifies any “gaps” between the two. These types of analysis are almost always done by external parties or third parties to ensure that they are performed objectively without potential bias. Some industry compliance standards (such as HIPAA or PCI) may require an outside entity to perform such an analysis. The reasoning is that an outside consultant can often catch gaps that would not be obvious to personnel working in the area every day.

If a gap analysis is being performed against a business function, the first step is to identify a relevant industry-standard framework to compare business activities against. In information security, this usually means comparison against a standard such as ISO/IEC 27002 (best-practice recommendations for information security management). Another common comparison framework used as a cybersecurity benchmark is the NIST cybersecurity framework.

A gap analysis can be conducted against almost any business function, from strategy and staffing to information security. The common steps generally consist of the following:

- Establishing the need for the analysis and gaining management support for the efforts.
- Defining scope, objectives, and relevant frameworks.
