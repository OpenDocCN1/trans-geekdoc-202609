Azure AD Multifactor Authentication or conditional access custom controls must be used by organizations that require multifactor authentication with password hash synchronization. The organizations cannot use federated multifactor authentication methods on-premises or from third parties.

+   From a disaster recovery and business continuity perspective: As a cloud service that scales to all Microsoft data centers, password hash synchronization with cloud authentication is highly available. If password hash synchronization goes down for extended periods, deploy an Azure AD Connect server as a standby server in staging mode.

At the time of writing this book, password hash synchronization doesn’t immediately enforce changes in on-premises account states.

Cloud apps can be accessed until the user account state is synchronized with Azure AD. After administrator’s bulk update on-premises user account states, organizations may want to run a new synchronization cycle to overcome this limitation.

# Azure AD Pass-Through Authentication

The Azure AD pass-through authentication service validates passwords for Azure AD authentication services by utilizing a software agent on-premises. To ensure that password validation does not occur in the cloud, the servers validate users directly with your on-premises Active Directory.

An organization that requires immediate enforcement of on-premises password policies and sign-in hours may use this authentication method.

Figure 3.4 depicts the reference architecture for pass-through authentication.

# FIGURE 3.4 Microsoft Azure AD pass-through authentication reference architecture

![](bbox=[0.13, 0.57, 0.85, 0.87])