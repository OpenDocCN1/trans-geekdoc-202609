
## 2. The transmission, routing, provision of connections, or copying must be carried out by an automated technical process without selection of material by the service provider.

## 3. Any intermediate copies must not ordinarily be accessible to anyone other than anticipated recipients and must not be retained for longer than reasonably necessary.

## 4. The transmission must be originated by a person other than the provider.

### 14. Which one of the following laws is not designed to protect the privacy rights of consumers and internet users?

1.  Health Insurance Portability and Accountability Act
2.  Identity Theft Assumption and Deterrence Act
3.  USA PATRIOT Act
4.  Gramm-Leach-Bliley Act

### 15. Which one of the following types of licensing agreements does not require that the user acknowledge that they have read the agreement prior to executing it?

1.  Standard license agreement
2.  Shrink-wrap agreement
3.  Click-wrap agreement
4.  Verbal agreement

### 16. What industry is most directly impacted by the provisions of the Gramm-Leach-Bliley Act?

1.  Healthcare
2.  Banking
3.  Law enforcement
4.  Defense contractors

### 17. What is the standard duration of patent protection in the United States?

1.  14 years from the application date
2.  14 years from the date the patent is granted
3.  20 years from the application date
4.  20 years from the date the patent is granted

### 18. Which one of the following is the comprehensive EU law that governs data privacy that was passed in 2016 and goes into effect in 2018?

1.  DPD
2.  GLBA
3.  GDPR
4.  SOX

### 19. What compliance obligation relates to the processing of credit card information?

1.  SOX
2.  HIPAA
3.  PCI DSS
4.  FERPA

### 20. What act updated the privacy and security requirements of the Health Insurance Portability and Accountability Act (HIPAA)?

1.  HITECH
2.  CALEA
3.  CFAA
4.  CCCA

# Chapter 5: Protecting Security of Assets

**THE CISSP EXAM TOPICS COVERED IN THIS CHAPTER INCLUDE:**

*   **Domain 2: Asset Security**
    *   2.1 Identify and classify information and assets
        *   2.1.1 Data classification
        *   2.1.2 Asset classification
    *   2.2 Determine and maintain information and asset ownership
    *   2.3 Protect privacy
        *   2.3.1 Data owners
        *   2.3.2 Data processors
        *   2.3.3 Data remanence
        *   2.3.4 Collection limitation
    *   2.4 Ensure appropriate asset retention
    *   2.5 Determine data security controls
        *   2.5.1 Understand data states
        *   2.5.2 Scoping and tailoring
        *   2.5.3 Standards selection
        *   2.5.4 Data protection methods
    *   2.6 Establish information and asset handling requirements

The Asset Security domain focuses on collecting, handling, and protecting information throughout its lifecycle. A primary step in this domain is classifying information based on its value to the organization.

All follow-on actions vary depending on the classification. For example, highly classified data requires stringent security controls. In contrast, unclassified data uses fewer security controls.

## Identify and Classify Assets

One of the first steps in asset security is identifying and classifying information and assets. Organizations often include classification definitions within a security policy. Personnel then label assets appropriately based on the security policy requirements. In this context, assets include sensitive data, the hardware used to process it, and the media used to hold it.

### Defining Sensitive Data

Sensitive data is any information that isn’t public or unclassified. It can include confidential, proprietary, protected, or any other type of data that an organization needs to protect due to its value to the organization, or to comply with existing laws and regulations.

#### Personally Identifiable Information

`Personally identifiable information (PII)` is any information that can identify an individual. National Institute of Standards and Technology (NIST) Special Publication (SP) 800-122 provides a more formal definition:

> Any information about an individual maintained by an agency, including
>
> (1) any information that can be used to distinguish or trace an individual’s identity, such as name, social security number, date and place of birth, mother’s maiden name, or biometric records; and
>
> (2) any other information that is linked or linkable to an individual, such as medical, educational, financial, and employment information.

The key is that organizations have a responsibility to protect `PII`. This includes `PII` related to employees and customers. Many laws require organizations to notify individuals if a data breach results in a compromise of `PII`.

#### Protected Health Information

`Protected health information (PHI)` is any health-related information that can be related to a specific person. In the United States, the Health Insurance Portability and Accountability Act (HIPAA) mandates the protection of `PHI`. HIPAA provides a more formal definition of `PHI`:

> Health information means any information, whether oral or recorded in any form or medium, that—
>
> (A) is created or received by a health care provider, health plan, public health authority, employer, life insurer, school or university, or health care clearinghouse; and
>
> (B) relates to the past, present, or future physical or mental health or condition of any individual, the provision of health care to an individual, or the past, present, or future payment for the provision of health care to an individual.

Some people think that only medical care providers such as doctors and hospitals need to protect `PHI`. However, HIPAA defines `PHI` much more broadly. Any employer that provides, or supplements, healthcare policies collects and handles `PHI`. It’s very common for organizations to provide or supplement healthcare policies, so HIPAA applies to a large percentage of organizations in the United States (U.S.).

#### Proprietary Data

Proprietary data refers to any data that helps an organization maintain a competitive edge. It could be software code it developed, technical plans for products, internal processes, intellectual property, or trade secrets. If competitors are able to access the proprietary data, it can seriously affect the primary mission of an organization.

Although copyrights, patents, and trade secret laws provide a level of protection for proprietary data, this isn’t always enough. Many criminals don’t pay attention to copyrights, patents, and laws. Similarly, foreign entities have stolen a significant amount of proprietary data.

As an example, information security company Mandiant released a report in 2013 documenting a group operating out of China that they named APT1. Mandiant attributes a significant number of data thefts to this advanced persistent threat (APT). They observed APT1 compromising 141 companies spanning 20 major industries. In one instance, they observed APT1 stealing 6.5 TB of compressed intellectual property data over a ten-month period.

In December 2016, the U.S. Department of Homeland Security (DHS) and the Federal Bureau of Investigation (FBI) released a joint analysis report documenting Russian malicious cyber activity. This report focused on activities of APT 28 and APT 29, also known as Fancy Bear and Cozy Bear, respectively. These groups primarily targeted US government entities and others involved in politics. Cybersecurity firms such as CrowdStrike, SecureWorks, ThreatConnect, and FireEye’s Mandiant have all indicated that APT 28 is sponsored by the Russian government and has probably been operating since the mid-2000s.
