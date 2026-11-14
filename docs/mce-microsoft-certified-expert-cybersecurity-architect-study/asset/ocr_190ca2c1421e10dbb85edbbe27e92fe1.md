+   - Numbering scheme: Make sure the numbering scheme is predictable and standard.
+   - Policy types: Microsoft recommends considering five main kinds: base protection, identity protection, data protection, app protection, and attack surface reduction.
+   - Standard policy components: Apps, platform types, grant control types, and names are all components that need to be defined in advance so that all policies are consistent.

# Conditional Access Zero Trust Architecture

In terms of conditional access architecture, Microsoft recommends adopting either targeted or Zero Trust in your enterprise design.

This architecture is a good fit for Zero Trust principles. In a conditional access policy, if you select the All Cloud Apps option, all endpoints will be protected by the provided grant controls, such as known users and compliant devices. The policy applies to all endpoints with which the user interacts, not just those supported by conditional access.

Various new PowerShell and Microsoft Graph tools use a device-login flow endpoint. Device-login flow enables signing in from devices that do not have a sign-in screen, such as IoT devices.

The user is shown a code after executing a device-based sign-in command on their device. To use the same code on the next device, the user has to go to aka.ms/devicelogin and enter their username and password. The sign-in on the IoT device in the same user context will succeed after the sign-in from the other device.

This sign-in does not support device-based conditional access, which presents a challenge. If you apply a baseline policy requiring a known user and a known device for all cloud applications, nobody can use the tools and commands. The same problem occurs with device-based conditional access for other applications.

Another architecture is the targeted model, in which you target only the apps you wish to protect in conditional access policies. As a result, conditional access policies do not protect device login for endpoints already covered by all cloud applications (for example, graph calls to Azure Active Directory).

To distinguish the two architectures, you can authenticate with a device login. Suppose each application is targeted and can be excluded from a conditional access policy that requires device-based login. In that case, device login could be allowed for one or a few individual applications.

In a targeted architecture, you may forget to protect all of your cloud applications. Nevertheless, you would select all the selectable applications in conditional access policies, leaving unprotected access to applications not selectable. Several very sensitive portals are accessible to users, such as the Office portal, Azure Enterprise Agreement (EA) portal, and security information portal.

Microsoft and its partners are releasing new features, and your IT admins are integrating various applications with Azure Active Directory (Azure AD) over time, so the number of Office 365 and Azure Active Directory (Azure AD) applications keeps growing. Conditional Access can be protected only by a script that detects new apps and applies a policy automatically, and developing and managing such a script may be super complex.