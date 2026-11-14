For instance, Company XYZ hired people worldwide to manage and reset passwords for its Azure AD clients. Global Administrators and Privileged Role Administrators can create a group called CompanyXYZHelpdeskAdministrators and assign the role to the group instead of assigning the role individually to all employees. People who join a group are assigned roles indirectly.

To ensure only legitimate users are members of the group, help-desk individual users are assigned the Helpdesk Administrator role. Your existing governance workflow can perform the approval process and audit the group’s membership.

Using Azure AD Privileged Identity Management (PIM), you can assign roles to groups. Each group member can activate the role assignment for a fixed time frame. Here are the best practices for using Azure Active Directory role-based access control (Azure AD RBAC):

**Least privilege management.** As a best practice, managing your access control strategy to the least privilege possible is best. The least privilege means giving administrators the permissions they need to do their jobs. When assigning administrators a role, you need to consider three aspects: a specific set of permissions, a specified scope, and a specified period. Initially it seems easier to assign broader roles at broader scopes. It would be best if you avoided them. Azure AD RBAC supports more than 65 built-in roles. In the event of a breach of a security principle, you limit the resources at risk by limiting roles and scopes. A few of Azure AD’s roles include the management of directory objects, groups, and applications, as well as the management of Microsoft 365 services such as Exchange, SharePoint, and Intune.

**Access can be granted just in time using privileged identity management.** There should be a limited period of time for which access should be granted under the principle of least privilege. Microsoft recommends enabling Azure AD Privileged Identity Management (PIM) to grant administrators just-in-time access. In Azure AD, PIM allows an individual to become an eligible member for a limited-time role and activate the role as needed. Privileged access is automatically removed when the timeframe expires. Activating highly privileged roles can also require approval or be notified via email via PIM settings. Notifications alert you when new users have been added.

**For all administrator accounts, enable MFA.** Based on Microsoft studies available in the below link, there is a 99.9 percent reduction in the likelihood of your account being compromised if you use MFA.

The chance of your account being compromised is 99.9 percent lower if you use multi-factor authentication (MFA).

+   Two methods are available for enabling MFA on Azure AD roles:
+   - Setting up roles in PIM
+   - Conditional Access

**Restrict access over time by configuring recurring access reviews.** Access reviews should ensure that only the system engineers or administrators can access your organization’s systems or services. Regular audits are essential for several reasons.