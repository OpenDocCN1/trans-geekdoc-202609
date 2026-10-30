
## 2.1 Three-Level Control Framework

Different terms designate the means that are deployed to protect information confidentiality, availability and integrity: measure, control, protection, countermeasure, and so on. We will use the term control, which, a priori, can be taken as a synonym for all the other terms commonly used.

Controls can be classified into different categories; for example:

- By nature: regulatory, physical, technical, human
- By security domain: information, physical (safety), human
- By protected target: information systems, physical premises, human integrity
- By characteristics: preventive, corrective, detective
- And so on.

When we look at security standards’ recommendations, the immediate question that arises is: how can the various controls be broken down by level of responsibility? Board members cannot be expected to read the standards to identify the controls under their responsibility. So, we need a model that groups controls under different levels of responsibility, enabling the rapid identification of who is responsible for what in the governance process.

**EXAMPLE**

In ISO 27001, A.9 Access Control, the following control objectives can be considered from different levels regarding accountability:

- A.9.1.1 Access control policy (should be under the responsibility of the board of directors).
- A.9.2.5 Review of user access rights (should be under the responsibility of business units).
- A.9.2.2 User access provisioning (should be under the responsibility of IT operations).

Since security responsibility today is essentially shared by several actors in an organization, what we need is a model that allows us to quickly identify the following three classes of vertical controls: governance (orientations, assurance), management (steering, oversight), and operations (technical controls or processes). This makes it easier to identify the responsible authorities and any gaps in the governance and management process. It is still not uncommon today to see operational or technical controls put in place in response to incidents or to overcome a visible threat without worrying about the managerial- or governance-level impact. This usually leads to a waste of resources, misunderstanding among the different stakeholders, and poor alignment with business needs. The Sherwood Applied Business Security Architecture (SABSA) framework mentioned in Chapter 1 can help set up security architecture that facilitates the implementation of operational controls in line with business needs. However, this approach also requires a high level of governance maturity.

**EXAMPLE**

Take the example of setting up a new system of identity and access management (IAM) based on business roles (role/rule-based access control [RBAC]). Setting up such a system means taking different levels of control into account, not just technical ones. It is not enough to simply install a software solution that automates the provisioning of user privileges from the human resources (HR) database on target platforms. The expected organization of responsibilities in role management must also be taken into account, along with elaborating specific policies in this field, defining the accountability of oversight or incident management. There is certainly a hierarchy of controls and a vertical distribution system that must be respected. This hierarchy of controls could be presented as follows (not exhaustive):

| Level | Control (excerpt) | Responsibility |
|---|---|---|
| Governance | Policy, organizations | Governing body |
| Management | Risk management, program management | Chief information security officer (CISO) or IAM officer |
| Operations | Role and privilege management, periodic certifications of access | Business |
| Technical | Incident management, monitoring | IT operations |

This vertical distribution of the control groups is of paramount importance in setting up IS governance and management. It emphasizes the need to share responsibility at different levels, which is a prerequisite for establishing adequate security. Every level of responsibility must be concerned by IS. In this context, any significant adaptation of the system, such as the one just observed, can have repercussions on governance, managerial, operational, or technical controls. Some changes in technical controls, however, such as replacing one intrusion detection system with another, will most likely have little or no impact on guidelines or risk management. Nevertheless, the scope of any change to IS governance and management should always be reviewed.

### Why not use the standards?

![](img/90693339cd50db9a18259ad447383b45_42_0.png)

**Figure 2.1 Structure of ISO 27001/2 standards.**

Each of the standards has adopted a system of grouping and distributing controls in sets of its own. The NIST 800-53 standard presents a catalog of controls and classifies them into 18 families and three classes: managerial, operational, and technical. ISO 27001 groups the requirements that an ISMS must meet into seven clauses containing 22 recommendations. In its appendix it presents 14 Groups containing 25 Control Objectives with 114 controls. The ISO 27002 standard (Code of practice for information security controls) reiterates the Objectives and Controls and adds, for each control, a guide to good practices (Figure 2.1).

The following observations can be made:

- The grouping and naming of groups, control objectives, and the controls themselves evolve from one version to another.
- Groups and objectives in ISO do not refer to the same level of responsibility. For example, A.5 "Information security policy"/A.5.1 "Management direction for information security" is not at the same level of responsibility as A.13 "Communication security"/A.13.1 "Network security management."
- Some groups refer to generic controls or processes (e.g., A.6 "Organization of information security"), while others mention controls linked to the means of protection (e.g., A.10 "Cryptography").

This is quite understandable. In fact, to avoid unnecessary complications, the standards seek to present the completeness of the controls in the smallest possible format, perhaps to the detriment of a certain vertical (hierarchy) and horizontal (domains) distribution of the control objectives. The formalism of presentation is not oriented toward governance but toward the completeness of the processes. Changes or adaptations to the content from one version to another are mainly due to evolution in the threats or protection techniques.

Therein lies the importance of proposing additional methods of grouping controls other than the standards. We need a simpler model allowing the consolidation of governance, management, and operational controls into building blocks for an entire ISMS or for a particular security domain (mobility, IAM, continuity) or technology (encryption, cloud). This will allow decision-makers to focus immediately on the sets of controls that affect them. Indeed, as we have just presented in the example of IAM, some control objectives have to be taken into account regardless of the scope of the system under observation. These control objectives are: strategy, policy and guidelines, security organization, risk management, security program management, reporting and oversight, asset management, compliance, and metrics.

### What is the main purpose of such a framework?

Such a framework should allow management and security practitioners to ask pertinent questions about governance for IS as a whole, a specific security domain, or during major IS changes. These questions are the following:

1. Do we have a strategy?
2. Have we established our policies?
3. Is our security organization adequate?
4. What are the risks and how are they managed?
5. How is our IS program managed?
6. Is the reporting and oversight system adequate?
7. Which assets (data, applications, etc.) are impacted, and who is responsible for them?
8. Are we in compliance with the legal and regulatory framework?
9. Do we have metrics or key performance indicators (KPIs) to track the adequacy of our protection system?

**EXAMPLE**

Suppose a company wants to outsource some of the operations of a business line onto the cloud of an external provider. This initiative or project is obviously not only a technical matter and requires management approval. The security risks faced by the company must also be considered. The questions that management should ask are the following:

1. Do we have a strategy in the domain of cloud computing?
2. How should our security policy evolve following this change?
3. Is our security organization suitable? Who is responsible for it: IT or the business line?
4. What are the security risks that ensue?
5. What specific controls should be put in place or adapted?
