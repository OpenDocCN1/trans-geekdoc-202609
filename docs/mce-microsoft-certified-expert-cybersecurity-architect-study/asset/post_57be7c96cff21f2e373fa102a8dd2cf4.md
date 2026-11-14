
Azure AD Multifactor Authentication or conditional access custom controls must be used by organizations that require multifactor authentication with password hash synchronization. The organizations cannot use federated multifactor authentication methods on-premises or from third parties.

- From a disaster recovery and business continuity perspective: As a cloud service that scales to all Microsoft data centers, password hash synchronization with cloud authentication is highly available. If password hash synchronization goes down for extended periods, deploy an Azure AD Connect server as a standby server in staging mode.

At the time of writing this book, password hash synchronization doesn’t immediately enforce changes in on-premises account states.

Cloud apps can be accessed until the user account state is synchronized with Azure AD. After administrator’s bulk update on-premises user account states, organizations may want to run a new synchronization cycle to overcome this limitation.

## Azure AD Pass-Through Authentication

The Azure AD pass-through authentication service validates passwords for Azure AD authentication services by utilizing a software agent on-premises. To ensure that password validation does not occur in the cloud, the servers validate users directly with your on-premises Active Directory.

An organization that requires immediate enforcement of on-premises password policies and sign-in hours may use this authentication method.

Figure 3.4 depicts the reference architecture for pass-through authentication.

## FIGURE 3.4 Microsoft Azure AD pass-through authentication reference architecture

![](img/5ab9852bf401dd309bf0f81797a91445_155_0.png)

While you design Azure AD pass-through authentication, consider the key elements for Azure AD pass-through synchronization.

- From an effort's perspective: To use pass-through authentication, you must install one or more lightweight agents on existing servers (Microsoft recommend three). You must provide the agents access to Active Directory Domain Services, including your AD domain controllers on-premises. For this reason, deploying the agents in a perimeter network is not recommended, and they require outbound Internet access and access to your domain controllers.
- In pass-through authentication, domain controllers must have unrestricted network access, and all network traffic must be encrypted and limited to authentication requests.
- From a user experience perspective: Pass-through authentication improves users' sign-in experience by removing the unnecessary prompts. Seamless SSO avoids needless prompts after a user's login.
- From an advanced use case perspective: At the time of sign-in, pass-through authentication enforces the on-premises account policy. An on-premises user's login attempt may be denied access if their account is disabled or locked out, if their password expires, or if the login attempt falls outside the sign-in hours.

Azure AD MFA or CA custom controls are required for organizations that require multi-factor authentication with pass-through authentication. These organizations can't use multi-factor authentication that relies on federation. Password hash synchronization is needed for advanced features, whether you choose pass-through authentication or not.

For disaster recovery and business continuity, Microsoft recommends deploying two more pass-through authentication agents. In addition to the Azure AD Connect server agent, these additional agents ensure high availability for authentication requests. Even with three agents deployed, one agent can still fail if another agent is down for maintenance.

Combining password hash synchronization with pass-through authentication also makes sense since it serves as a backup authentication method in the case of a failed primary authentication attempt. Suppose a significant on-premises failure prevents the agents from validating a user's credentials. In that case, password hash synchronization can work as a backup authentication mechanism for pass-through authentication. It would help if you used Azure AD Connect to manually switch to password hash synchronization.

## Federated Authentication

When you use this authentication method, Azure AD passes the authentication process to an external authentication system, such as AD FS. Smartcard-based or multifactor authentication by third parties can be provided as additional advanced authentication requirements.

Figure 3.5 depicts the reference architecture for federated authentication.

## FIGURE 3.5 Microsoft federated authentication reference architecture

![](img/5ab9852bf401dd309bf0f81797a91445_157_0.png)

While you design federated authentication, consider the following.

- **From an effort's perspective:** Authentication is handled by an external trusted system in a federated authentication system. A hybrid identity solution based on Azure AD allows some companies to reuse existing investments in federated systems. Azure AD is not responsible for maintaining and managing the federated system; the organization’s responsibility is to use the federated system securely and handle the authentication load.
- **From a user experience perspective:** The user experience of federated authentication depends on how the federation farm’s topology, configuration, and features are implemented. Some organizations must be flexible enough to adapt and configure federation farm access based on their security requirements. For example, internally connected users and devices can be configured to sign in automatically without prompting for credentials since they have already logged in. Advanced security features sometimes make the sign-in process more difficult for users.
- **From an advanced use case perspective:** Customers with authentication requirements that Azure AD does not support natively should consider using federated authentication. Here are some common scenarios to consider:
  - Require smartcards or certificates for authentication.
  - Require federated identity providers for on-premises or third-party multifactor authentication servers.
  - Provision an authentication solution provided by a third party.
- Install a sign-in protocol that, rather than using a User Principal Name (UPN) (for instance, user@domain.com), requires a SAMAccountName (for example, DOMAIN\username).
- From a disaster recovery and business continuity perspective: The federated authentication system typically requires a load-balanced array of servers, called a *farm*, configured in a topology that ensures high availability for authentication requests.

For example, deploy password hash synchronization and federated authentication as backup methods when on-premises servers are unavailable. Providing low-latency authentication requests at multiple Internet ingress points configured with geo-DNS is a requirement for some large enterprise organizations requiring a federation solution.

Most organizations use this choice if they currently have an on-premises federation infrastructure investment and if using only one identity provider is a vital business requirement. By default, federated systems require a higher investment in infrastructure, and the federation is more challenging to operate and troubleshoot than cloud authentication solutions.

Figure 3.6 depicts the decision tree; using it you can decide which authentication method is best for you as a Microsoft Cybersecurity Architect. Using it, you can decide whether to use federated or cloud authentication to manage your Azure AD hybrid identity.

## Comparison of Authentication Methods

Table 3.1 compares various authentication methods, which will help Microsoft Cybersecurity Architects define the identity control plane.

The following are the high-level guidelines provided by Microsoft to design an identity layer:

- It protects your organization's sensitive data by controlling access to the cloud and line-of-business apps that you migrate and make available in the cloud.

Regardless of the authentication method you choose, Microsoft recommends it would be best if you used or enabled password hash synchronization for the following reasons:

**High Availability and Disaster Recovery Consideration** On-premises infrastructure is required for pass-through authentication and federation. Pass-through authentication includes the server hardware and networking that the agents need. When you use federation, your on-premises footprint is even more critical. It would help if you had proxy servers in the perimeter network to proxy authentication requests and had internal federation servers to handle federation.

By deploying redundant servers, you can prevent single points of failure. In both pass-through authentication and federation, authentication requests are handled if any of the components fail, and domain controllers can also fail to respond to authentication requests. Maintenance is essential to keep these components healthy; when care isn't planned and implemented correctly, outages are more likely. Microsoft Azure AD cloud authentication service scales globally and is always available, so password hash synchronization can be used to avoid outages.
