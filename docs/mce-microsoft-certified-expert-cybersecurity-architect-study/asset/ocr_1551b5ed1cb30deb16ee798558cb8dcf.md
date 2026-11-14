Identification and authentication consistently occur jointly as a single two-step process. Delivering an identity is the first step, and providing the authentication information is the second step. Without both, a subject cannot gain access to a system.

Let's now move into the Microsoft method to secure access against Azure resources. With cloud applications and the mobile workforce, security perimeters have been redefined. Employees bring their own devices and work remotely, and data is shared with external partners and vendors outside the corporate network. As corporate applications and data move into hybrid and cloud environments, traditional network security controls are no longer sufficient. Controls must move to where data is: on devices, apps, and partners.

Today's networks, endpoints, and applications are interconnected by identities representing people, services, and IoT devices. Identity functions as a powerful, flexible, and granular security control in the Zero Trust model. An organization must take the following steps before allowing an identity access to a resource:

+   - Use strong authentication to verify the identity.
+   - Maintain compliance with the identity and ensure access is appropriate.
+   - Follow the principle of least privilege access.

Identity needs to be verified, and then Microsoft can maintain that identity’s access to cloud resources based on organization policies, ongoing risk analysis, and other mechanisms.

To develop a successful access control strategy, you must consider more than one tactic or technology and take a pragmatic approach that embraces the right technology and tactics for the particular situation at hand.

Modern access control must complete the productivity requirements of the organization and also be all of the following:

+   - **Secure:** During access requests, verify the trustworthiness of users and devices using all available data and telemetry. This configuration prevents attackers from impersonating legitimate users without being detected. Implementing an access control strategy that eliminates unauthorized privilege escalation is also essential. For example, granting a privilege can be used to gain higher privileges. The section on securing privileged access contains more information about protecting privileged access.
+   - **Consistent:** The environment should be consistently and seamlessly secured. By implementing this standard, attackers cannot sneak in through weaknesses in a disjointed or complex access control implementation, improving the user experience. To avoid configuration inconsistencies and drift, you should use a single access control strategy that uses the fewest number of policy engines.
+   - **Comprehensive:** Enforcing access policies close to resources and access paths improves security coverage and allows security to fit seamlessly into the scenarios and expectations of users. Drive policy enforcement closer to the business assets of value with security controls for data, applications, identity, networks, and databases.
+   - **Identity-centric:** Utilize identity and related controls whenever possible. Identity controls provide rich information about access requests and application context that raw network traffic does not. Even though networking controls are necessary and sometimes