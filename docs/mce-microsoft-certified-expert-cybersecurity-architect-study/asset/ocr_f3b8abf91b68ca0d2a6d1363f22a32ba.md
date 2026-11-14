Because of potential security implications, several capabilities should be prioritized first.

+   - **Identity:** Security assurances can be achieved only by developing user directories and other authentication functions. Instead of using homegrown authentication solutions, choose mature capabilities such as Using Azure Active Directory (Azure AD), AAD B2B for Azure, and a B2C version of Azure AD. Users, partners, customers, applications, services, and other entities can be authenticated and granted permission through third-party solutions.
+   - **Data protection:** To encrypt and protect data, developers should use cloud services that include native encryption. There are many examples in the security world of failed attempts to protect data or passwords that cannot withstand attacks. Developers should only attempt to create their own cryptographic algorithms if they can directly use cryptography.
+   - **Key management:** Instead of directly handling keys, prefer identity authentication. A key management service such as Azure Key Vault or AWS Key Management Service, can access services requiring keys. As opposed to attempting to handle keys in application code safely, this will help you manage and secure these keys.
+   - **Application configurations:** Inconsistent configurations can create security risks for applications. The Azure App Configuration service helps mitigate this risk by centrally managing application settings and feature flags.

![](bbox=[0.14, 0.49, 0.22, 0.56])

From the SC-100 exam standpoint, remember that two popular standards, STRIDE and OWASP, can identify more potential risks. When designing an app or system, developers can spot threats using the STRIDE threat model. OWASP is a nonprofit organization dedicated to improving software security.

# Specify a Security Strategy for Applications and APIs

Continuous integration/continuous delivery (CI/CD) for applications and API development should be incorporated into the DevOps life cycle as rapidly as possible to avoid a waterfall development cycle.

What is a waterfall model? The *waterfall model* was the first process model to be introduced. It is also referred to as a *linear-sequential life-cycle model* and is very simple to understand and use. In a waterfall model, each phase must be completed before the next step can begin, and there is no overlapping of the stages.

Continuous delivery of value to end users is enabled by the union of people, processes, and tools in DevOps. As a result of the merging of Dev and Ops, multidisciplinary teams