As cloud services and internal applications become more popular, centralized authorization is becoming more critical. Authorization verifies the identity attempting to connect has the necessary permissions to access a service, feature, function, object, or method. In the absence of authentication, a connection fails before any authorization check is performed, and authorization always occurs after successful authentication. Authenticating a connection successfully may not allow a specific action if the user or group does not possess the necessary authorization.

To enforce Zero Trust, administrators should understand the following authorization methods:

+   - Security group membership
+   - Role-based access control
+   - Access levels
+   - Feature flags
+   - Security namespaces and permissions

From the SC-100 exam perspective, keep the following in mind: pass-through authentication, password hash synchronization, and federation are the three types of password synchronization. Azure AD does not store passwords in clear text or encrypt them with a reversible algorithm, and custom controls do not yet support device registration in Azure AD conditional access. The Azure AD hybrid identity solution must be deployed using one of Azure AD Connect's supported topologies.

# # Design a Strategy for Conditional Access

Identity-driven signals can be used as part of an organization's access control decisions to extend its security perimeter beyond its network. As part of the new identity-driven control plane, Microsoft Azure Active Directory conditional access integrates signals to make decisions and enforce policies.

If-then statements are the primary form of conditional access policies. Users must perform a specific action if they want access to a resource.
Administrators are faced with two primary goals.

+   - Enhance user productivity wherever they are.
+   - Ensure the assets of the organization are protected.

To keep your organization secure, use conditional access policies. Zero Trust relies heavily on conditional access, because it ensures the right user has access to the right resources based on computed risk and preconfigured policies. Azure Active Directory can make access