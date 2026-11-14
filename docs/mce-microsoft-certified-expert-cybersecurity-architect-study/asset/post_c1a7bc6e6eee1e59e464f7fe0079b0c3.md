
### FIGURE 3.7 Microsoft recommends end-to-end security.

![](img/5ab9852bf401dd309bf0f81797a91445_172_0.png)

Organizations can deploy these critical protections rapidly using these levels because they provide straightforward technical guidance. The privileged access strategy recognizes that organizations have unique needs and that custom solutions create complexity that causes higher costs and lower security over time.

To balance this requirement, the strategy supplies firm prescriptive direction for each level and flexibility by permitting organizations to determine when each role is mandated to meet the needs of that level.

Even though the underlying technology is complex, it is essential to keep things simple rather than create custom solutions that are difficult to maintain.

The guided privileged access security strategy implements a simple three-level system of guarantees that span areas such as all devices, accounts, intermediaries, and interfaces that are subject to the same security levels.

### Enterprise Security
Security for enterprise users and productivity scenarios is suitable for all enterprise users.

In advance of the rapid modernization plan, the enterprise also functions as the starting point for technological and privileged access as they progressively build on the security controls in enterprise security.

### Specialized Security
Specialized security controls provide increased protection if an attacker or malicious insider compromises a role with a high business impact.

Identify all roles and accounts meeting your organization’s specialized and privileged criteria. Typical specialized roles include the following:

- Business-critical system developers
- Business roles with sensitive business information, including SWIFT terminal users, researchers who have access to sensitive data, payroll administrators, and approvers of sensitive business processes, among others
- Those who regularly handle sensitive information, such as executives and personal assistants/administrative assistants
- High-impact social media accounts, which could damage a company’s reputation

This group includes administrators of individual high-impact workloads with significant privileges that are not enterprise-wide. They typically have significant privileges and impact. (Examples are an administrator of an enterprise resource planning system, a bank administrator, a help-desk administrator, and so on).

Privileged security is further built upon with specialized account security.

### Privileged Security
Security at the highest level is referred to as *privileged security*. It is designed for roles that can cause significant damage and potentially lead to a significant incident in the organization if the attacker or malicious insider gets their hands on them. Technical roles at this level typically have administrative permissions to most or all enterprise systems (sometimes including business-critical ones). Security is the first priority for privileged accounts, while productivity is defined as the ability to quickly and securely complete a fixed set of sensitive job tasks.

## Securing Privileged Access

For privileged access to be secured, the following changes are required:

- Knowledge management, administrative practices, and processes
- A host defense, account protection, and identity management component

In the case of on-premises administrator accounts, manage and report your privileged access.

Let’s discuss Microsoft Azure AD Privileged Identity Management (PIM) capabilities.

The Azure Active Directory (Azure AD) service Privileged Identity Management provides a way to manage, control, and monitor access to your organization’s essential resources. To minimize the risk of compromising secure information or resources, organizations should reduce the number of people who have access to resources.

As a result, there is less chance of the following happening:

- Access by a malicious actor
- An authorized user accidentally impacting a sensitive resource

Organizations can grant privileged users just-in-time privileged access to Azure. Azure AD resources monitor what privileged users do with their privileges. Azure AD, Azure, Microsoft 365, or SaaS apps still need to be used by privileged users to carry out privileged operations. Azure AD Premium P2 licenses are required to use the PIM feature.

In Privileged Identity Management, Azure AD roles can be managed only by users with the Privileged Role Administrator or Global Administrator roles. In Privileged Identity Management, Azure AD roles can be viewed by Global Administrators, Security Administrators, Global Readers, and Security Readers.

Privileged Identity Management allows subscription administrators, resource owners, or resource user access administrators to assign Azure resource roles to other administrators. Users who are Privileged Role Administrators, Security Administrators, or Security Readers cannot view Azure resource role assignments by default in Privileged Identity Management. Here are some of the critical features of Privileged Identity Management for mitigating the risks of excessive, unnecessary, or misused access permissions on your resources:

- Just in time: Azure AD and Azure resources can be accessed just in time.
- Time-bound: Using start and end dates, assign resources time-bound access.
- Approval: Activating privileged roles requires approval.
- Multifactor: Activate any role with multifactor authentication.
- Justification: Understanding why users activate can be achieved by using justification.
- Notifications: Activate privileged roles and receive notifications.
- Access reviews: Ensure users’ roles are still needed by conducting access reviews.
- Audit history: This includes internal or external audits and downloading the audit history.
- Last active global administrator and privileged role administrator: This prevents the last active global administrator and privileged role administrator role assignments from being removed.

## Develop a Road Map

Microsoft recommends developing a road map to prevent cyberattackers from accessing privileged resources. As your organization develops its capabilities and requirements, you can continuously adjust your road map to secure privileged access against cyberattackers. Microsoft recommends four stages in its road map to make it more challenging and costlier for adversaries to gain privileged access to your on-premises, cloud, or hybrid assets. Implementations that are most effective and fastest should be scheduled first. At a very high level, this is the objective of each stage:

- The first stage (24–48 hours): Microsoft recommends that you take care of critical items right away.
- The second stage: Mitigate the most commonly used attacks (2–4 weeks).
- The third stage (1–3 months): Building visibility and controlling administrator activity.
- The fourth stage (six months and beyond): Further hardening your security platform.

### Stage 1: Critical Items to Do Right Now

Stage 1 of the road map focuses on the fast and easy implementation of critical tasks. To achieve a fundamental class of secure privileged access, Microsoft recommends that you complete these few tasks within 24–48 hours. The following actions are included in this stage of the road map for Secured Privileged Access:

- Enable Privileged Identity Management in Azure AD.
- Recognize and categorize accounts with high privileges.
- Provide emergency access to at least two people.
- Register all highly privileged, nonfederated single-user administrator accounts with multifactor authentication.

### Stage 2: Mitigate Frequently Used Attacks

Stage 2 of the Secured Privileged Access road map addresses the most commonly used attack methods of credential stealing and misuse. It can be implemented within 2–4 weeks and includes the following actions:

- A service, owner, and administrator inventory should be conducted.
- Determine which Microsoft accounts need to be switched from administrative roles to work or school accounts.
- Maintain separate user accounts for Global Administrators and forward their email.
- Recent password changes should be made for administrative accounts.
- Enable synchronization of password hashes.
- Ensure that users with privileged roles and those exposed to security risks require multifactor authentication.
- Protect your identity by configuring Identity Protection.
- Prepare an incident/emergency response plan; identify owners.
- Ensure that on-premises privileged administrative accounts are secure.
- Configure conditional access policies.

### Stage 3: Take Control of Administrator Activity

As part of this Secured Privileged Access road map stage, the following components will be implemented within approximately 1–3 months.

- Access reviews should be completed for users in administrator roles.
- Continue to roll out stronger authentication to all users.
- Dedicated workstations should be used for Azure AD administration.
- Identify incident handling recommendations from the National Institute of Standards and Technology (NIST).
- Increase the number of administrative roles using Privileged Identity Management for JIT.
- If you use Exchange Online, determine whether you are exposed to password-based login protocols.
- Your virtual machines' privileged accounts should be inventoried.
- Azure AD administrators should implement PIM.
- Monitor activity in connected cloud apps.
- Configure conditional access.
