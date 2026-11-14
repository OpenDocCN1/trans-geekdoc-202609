
the only available option (such as in operational technology environments), identity should always be the first option. It will be easier for the user to resolve a problem without contacting a help desk if a failure dialog is displayed during application access from the identity layer.

This building block in Figure 3.1 shows an enterprise access solution based on Zero Trust, which is applicable to all types of internal and external users, services, applications, and privileged accounts with administrative access.

## Deployment Objectives for Identity Zero Trust

Organizations are often troubled by their approach to identity before they begin their Zero Trust journey. Identity providers on-premises are used, SSO between cloud and on-premises apps is not present, and visibility into identity risk is limited.

As a first step in deploying an end-to-end Zero Trust identity framework, Microsoft recommends focusing on the following goals:

- 1. Ensure integration between cloud identity and on-premises identity.
- 2. Provide remediation activities through conditional access policies.
- 3. Enhance visibility with analytics.
- 4. Manage identities and access privileges through identity governance.
- 5. Perform real-time analysis of user, device, location, and behavior to determine risks and provide ongoing protection.
- 6. Detect, protect, and respond to threats using other security solutions.

For example, today many organizations start with limited (or zero) segmentation of internal traffic at their network ingress/egress points (along with other supporting security elements such as intrusion detection and prevention, proxies, and so on).

Using this standard configuration, any device connected to another device on the network could directly communicate with any other device (regardless of trust level or asset sensitivity). Even though this creates no productivity barriers, it creates a significant risk where a single compromised device can quickly attack any other resource (often with privileged internal credentials stolen from the compromised device, for example, from a successful phishing attack).

In many organizations, seemingly low-impact initial attack vectors (phishing attacks, user device compromises, and so on) quickly become significant incidents due to the lateral traversal allowed by this de facto architecture.

It is common for organizations (including Microsoft) to implement dedicated security controls for privileged access. These controls include separate accounts, privileged access workstations (PAWs, aka .ms/PAW), and just-in-time (JIT) solutions utilizing privileged identity/access management (PIM/PAM).

A Zero Trust approach focuses on reducing risk by explicitly validating the trust of users and devices before allowing access to resources. To enable remote work and contain the damage from attacks, users and devices must prove safe (without impacting the user experience and productivity).

## FIGURE 3.1 Enterprise access solution based on Zero Trust

| Privileged Access | Privileged Accounts (and PIM/PAM Systems) | Admin Devices and Workstations | Intermediary(ies) | | |
|---|---|---|---|---|---|
| Control Plane | Networks often provide a rudimentary control plane for legacy devices like Operational Technology | | | | Tier 0 Control Plane |
| Management Plane | Asset Management, Monitoring. Security<br>Data/Workload Plane ML, Apps & websites, API | | | | Tier 1 Split<br>• Management<br>• Plane<br>• Data/Workload<br>• Plane |
| User Access | User Accounts | User Devices and Workstations | Intermediary(ies) | External Access | Tier 2 Split<br>• User Access<br>• App Access |

As a result of the changes to access control architecture, managed devices are allowed access to cloud resources and on-premises resources only after they have been explicitly validated (configuration is compliant, the computer is not infected, and so on). As part of the Azure AD authentication process, conditional access validates a user against the organization’s policy.

![](img/5ab9852bf401dd309bf0f81797a91445_145_0.png)

Using Azure AD Identity Protection, your organization will receive a consolidated view of potential vulnerabilities and risk detections. As well as using Azure Active Directory’s existing anomaly detection capabilities (available through Azure AD’s Anomalous Activity Reports), Identity Protection introduces new risk detection types that can detect anomalies in real-time.

## Microsoft’s Method to Identity Zero Trust Deployment

Security perimeters are redefined in today’s mobile workforce and cloud-based applications. Employees bring their own devices and work remotely. Data is accessed outside the corporate network and shared with partners and vendors outside the network. Organizations cannot rely on traditional network controls for security as corporate systems are constantly in use from anywhere. Devices, apps, and partners should be empowered with controls wherever the data resides.

In today’s many networks, endpoints, and applications, identities represent people, services, or IoT devices. In the Zero Trust security model, identity functions as a decisive, adaptable, and acceptable way to control access to data.

An overview of the steps involved in managing identities in a Zero Trust security framework follows.

### Step 1: Integration Between Cloud Identity and On-Premises Identity

Azure Active Directory (AD) enables strong authentication, endpoint security integration, and the core of user-centric policies to ensure the least privileged access. Based on user identity, environment, device health, and risk, Azure AD’s conditional access capabilities determine how resources can be accessed.

Microsoft’s integration method between cloud identity and on-premises identity consists of four stages.

In Stage 1 (“Connect all of your users to Azure AD and federate with on-premises identity systems”), ensure that your cloud identities and controls are consistent by maintaining a healthy pipeline of employee identities as well as the necessary security artifacts (groups for authorization and endpoints for access policy controls).

To get started, follow these steps:

- 1. Choose an authentication option. Azure AD provides the best protection against brute-force attacks, DDoS attacks, and password spray attacks. Create the proper determination for your organization and compliance requirements.
- 2. Take advantage of going to the cloud to leave behind accounts that make sense on-premises only. Leave behind privileged roles from on-premises.
- 3. If your company has more than 100,000 users, groups, and devices combined, build a high-performance sync box that will keep organization lifecycle stay current.

In stage 2 (“Establish identity foundation with Azure AD”), in a Zero Trust strategy, you must verify explicitly, use least privileged access principles, and assume breaches. Azure AD can act as your policy decision point for enforcing your access policies based on insights about your users, endpoints, and target resources.

Microsoft recommends taking this step:

- 1. Every access request should be sent to Azure AD. Azure AD receives the signal from this identity control plane to determine the best authentication/authorization risk for each user and each app or resource. The use of a single sign-on and a consistent policy guardrail improves the user experience and increases productivity.

In stage 3 (“Integrate all your applications with Azure AD”), by using single sign-on, users are prevented from leaving copies of their credentials in various apps and from surrendering their credentials to excessive prompting.

You should also make sure your environment does not have more than one identity access management (IAM) engine. With two or more IAM engines, Azure AD does not see as much signal, allowing bad actors to live between the IAM engines. It can also result in poor user experiences and your business partners questioning your Zero Trust strategy for the first time.

Microsoft recommends following these steps:

- 1. Implement OAuth2.0 or SAML-enabled enterprise applications.
- 2. Use Azure AD Application Proxy to integrate Kerberos and form-based authentication applications.
- 3. Integrate Azure AD with most major application delivery networks/controllers (such as Citrix, Akamai, and F5) if you publish legacy applications.
- 4. Understand you should migrate your applications from existing/older IAM engines using Azure resources and tools.
- 5. Provide a tighter integration of identity life cycles between your various cloud applications.

In stage 4 (“Verify explicitly with strong authentication”), Microsoft recommends taking the following steps:

- 1. As a foundational component of reducing user session risk, roll out Azure AD MFA (Premium 1). The ability for users to respond to a multifactor authentication (MFA) challenge as they move around the world is one of the most direct ways they can convince us that these are familiar devices and locations (without having administrators parse individual signals) as they appear on new devices and from unknown locations.
- 2. Malicious actors frequently exploit legacy authentication mechanisms, such as SMTP, that can’t handle modern security challenges, such as stolen or replayed credentials.
