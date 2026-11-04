
Merchants are required to comply with the PCI DSS. Traditionally, a merchant is defined as a seller. It is important to note that the PCI DSS definition is a departure from the traditional definition. For the purposes of the PCI DSS, a merchant is defined as any entity that accepts American Express, Discover, JCB, MasterCard, or Visa payment cards as payment for goods and/or services (including donations). The definition does not use the terms *store, seller*, and *retail*; instead, the focus is on the payment side rather than the transaction type. Effectively, any company, organization, or individual that accepts card payments is a merchant. The mechanism for collecting data can be as varied as an iPhone-attached card reader, a parking meter, a point-of-sale checkout, or even an offline system.

## Compliance Validation Categories
PCI compliance validation is composed of four levels, which are based on the number of transactions processed per year and whether those transactions are performed from a physical location or over the Internet. Each payment card brand has the option of modifying its requirements and definitions of PCI compliance validation levels. Given the dominance of the Visa brand, the Visa categorization is the one most often applicable. The Visa brand parameters for determining compliance validation levels are as follows. Any entity that has suffered a breach that resulted in an account data compromise may be escalated to a higher level.
*   A Level 1 merchant meets one of the following criteria:
    *   Processes over six million Visa payment card transactions annually (all channels).
    *   A merchant that has been identified by any card association as a Level 1 merchant.
    *   Any merchant that Visa, at its sole discretion, determines should meet the Level 1 requirements to minimize risk to the Visa system.
*   A Level 2 entity is defined as any merchant—regardless of acceptance channel—processing one million to six million Visa transactions per year.
*   A Level 3 merchant is defined as any merchant processing 20,000 to 1,000,000 Visa e-commerce transactions per year.
*   A Level 4 merchant is defined as any merchant processing fewer than 20,000 Visa e-commerce transactions per year, and all other merchants—regardless of acceptance channel—processing up to one million Visa transactions per year.

An annual onsite compliance assessment is required for Level 1 merchants. Level 2 and Level 3 merchants may submit a self-assessment questionnaire (SAQ). Compliance validation requirements for Level 4 merchants are set by the merchant bank. Submission of an SAQ is generally recommended but not required. All entities with externally facing IP addresses must engage an ASV to perform quarterly external vulnerability scans.

## What Is a Data Security Compliance Assessment?
A ***compliance assessment*** is an annual onsite evaluation of compliance with the PCI DSS conducted by either a Qualified Security Assessor (QSA) or an Internal Security Assessor (ISA). The assessment methodology includes observation of system settings, processes, and actions, documentation reviews, interviews, and sampling. The culmination of the assessment is a Report on Compliance (ROC).

### Assessment Process
The assessment process begins with documenting the PCI DSS cardholder environment and confirming the scope of the assessment. Generally, a QSA/ISA will initially conduct a GAP assessment to identify areas of noncompliance and provide remediation recommendations. Post-remediation, the QSA/ISA conducts the assessment. To complete the process, the following must be submitted to either the acquiring financial institution or payment card brand:
*   ROC completed by a QSA or ISA
*   Evidence of passing vulnerability scans by an ASV
*   Completion of the Attestation of Compliance by the assessed entity and the QSA
*   Supporting documentation

### What Are QSAs, ISAs, and ASVs?
The PCI Security Standards Council operates a number of programs to train, test, and certify organizations and individuals to assess and validate adherence to PCI Security Standards. These programs include QSA, ISA, and ASV.

***Qualified Security Assessors (QSAs)*** are organizations that have been qualified by the PCI Security Standards Council to have their employees assess compliance to the PCI DSS standard. Employees of those organizations must be certified by the PCI Security Standards Council to validate an entity’s adherence to the PCI DSS.

***Approved Scanning Vendors (ASVs)*** are organizations that validate adherence to certain DSS requirements by performing vulnerability scans of Internet-facing environments of merchants and service providers.

***Internal Security Assessors (ISAs)*** are sponsor companies that have been qualified by the council. The PCI SSC ISA Program consists of internal security audit professionals of sponsor organizations who are qualified through training from the council to improve their organization’s understanding of the PCI DSS, facilitate the organization’s interactions with QSAs, enhance the quality, reliability, and consistency of the organization’s internal PCI DSS self-assessments, and support the consistent and proper application of PCI DSS measures and controls.

*Source*: PCI Security Standards Council ([www.pcisecuritystandards.org/approved\_companies\_providers/](http://www.pcisecuritystandards.org/approved_companies_providers/)).

### Report on Compliance
As defined in the PCI DSS Requirements and Security Assessment Procedures, the ROC standard template includes the following sections:
*   Section 1: “Executive Summary”
*   Section 2: “Description of Scope of Work and Approach Taken”
*   Section 3: “Details about Reviewed Environment”
*   Section 4: “Contact Information and Report Date”
*   Section 5: “Quarterly Scan Results”
*   Section 6: “Findings and Observations”
*   Section 7: “Compensating Controls Worksheets” (if applicable)

Sections 1–5 provide a detailed overview of the assessed environment and establish the framework for the assessor’s findings. The ROC template includes specific testing procedures for each PCI DSS requirement.

Section 6, “Findings and Observations,” contains the assessor’s findings for each requirement and testing procedure of the PCI DSS as well as information that supports and justifies each finding. The information provided in “Findings and Observations” summarizes how the testing procedures were performed and the findings achieved. This section includes all 12 PCI DSS requirements.

## What Is the PCI DSS Self-Assessment Questionnaire (SAQ)?
The SAQ is a validation tool for merchants that are not required to submit to an onsite data security assessment. Each PCI DSS SAQ includes the following components:
*   Questions correlating to the PCI DSS requirements, as appropriate for different environments.
*   Attestation of Compliance, which is your declaration of eligibility for completing the applicable SAQ and the subsequent results of a PCI DSS self-assessment.

Per the May 2016 PCI DSS SAQ Instructions and Guidelines, there are eight SAQ categories. The number of questions varies because the questionnaires are designed to be reflective of the specific payment card channel and the anticipated scope of the cardholder environment.
*   **SAQ A:** Applicable to merchants who retain only paper reports or receipts with cardholder data, do not store cardholder data in electronic format, and do not process or transmit any cardholder data on their systems or premises. This would never apply to face-to-face merchants.
*   **SAQ A-EP:** Applicable only to e-commerce channels who outsource all payment processing to PCI DSS validated third-party providers.
*   **SAQ B:** Applicable to merchants who process cardholder data only via imprint machines or standalone, dial-out terminals. This does not apply to e-commerce merchants.
