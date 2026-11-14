| Design and Deployment Consideration | Pass-Through Authentication and Seamless SSO | Password Hash Synchronization and Seamless SSO | Federation with AD FS |
| :--- | :--- | :--- | :--- |
| In what ways can conditional access be used? | Azure AD conditional access, with Azure AD Premium. | Azure AD conditional access, with Azure AD Premium | Azure AD conditional access, with Azure AD Premium. AD FS claim rules. |
| Can legacy protocols be blocked? | Yes. | Yes | Yes. |
| Do you have the option of customizing the logo, image, and description on the sign-in pages? | Yes, with Azure AD Premium. | Yes, with Azure AD Premium | Yes. |
| How are advanced scenarios handled? | Smart password lockout. | Smart password lockout Leaked credentials reports, with Azure AD Premium P2 | Multisite low-latency authentication system. AD FS extranet lockout. Integration with third-party identity systems. |

Source: adapted from https://learn.microsoft.com/en-us/azure/active-directory/hybrid/choose-ad-authn#comparing-methods

# Secure Authorization

Having successfully authenticated your users to your cloud resources, it’s now time to ensure they are limited to only performing the actions they are supposed to. End-user applications often handle authorization themselves. For example, a database row or document containing the access level of each user may be available. It makes sense because each application has its authorizing functions, but you need to check all applications to see what a user can access.

Separation of duties and least privilege are the most critical concepts for authorization. By definition, least privilege means that only the information your users, systems, and tools need to do their jobs should be accessible. This means you usually have a “deny by default” policy, which means identities can’t do anything unless you explicitly authorize it.

Regarding financial controls, where two signatures may be required for checks over a certain amount, separation of duties is a common practice. It usually means ensuring that no individual can completely undermine the security of an entire environment in the cloud. An individual who can change systems should not also be able to alter or review the logs from those systems.