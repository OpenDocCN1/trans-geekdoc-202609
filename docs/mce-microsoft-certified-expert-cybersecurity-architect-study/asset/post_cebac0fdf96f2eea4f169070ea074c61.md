
It is only possible for ransomware to extort data and destroy systems when all legitimate access has been lost. Suppose attackers are unable to remove your ability to resume operations without payment. In that case, your business will be protected, and the monetary incentive for attackers to attack your business will be undermined.

## Accountabilities of Members of Programs and Projects

According to the sponsorship/program management/project management hierarchy, Table 9.6 provides an overview of how your data will be protected from ransomware.

| Lead | Implementor | Accountability |
| :--- | :--- | :--- |
| Central IT operations or CIO | | Executive sponsorship. |
| Program lead from central IT infrastructure | Central IT infrastructure/backup | Drive results and cross-team collaboration. |
| | Central IT productivity/end user | Enable infrastructure backup. |
| | Business/application | Analyze critical business assets. |
| | Security architecture | Enable OneDrive Backup. |
| | Security policy and standards | Advise on configuration and standards. |
| | Security compliance management | Update standards and policy documents. Monitor to ensure compliance. |
| | User Education | Update guidance for users based on policy changes. |

## Deployment Checklist

Apply the best practices in Table 9.7 to protect your organization's data.

| Task | Description |
| :--- | :--- |
| Embrace the cloud by migrating your organization:<br>- Use cloud solutions such as OneDrive/SharePoint to manage user data and do versioning.<br>- Make sure that the users are taught how to recover their files independently to reduce the cost and time of the recovery process. | User data in the Microsoft cloud can be protected by built-in security and data management features. |
| Set up protected folders. | Makes it more difficult for unauthorized applications to modify the data in these folders. |
| Make sure you have the right permissions.<br>A broad write/delete permission is defined as the number of users with write/delete permissions for business-critical data on file shares, SharePoint, and other solutions.<br>Reduce broad permissions for critical data locations while meeting business collaboration requirements.<br>Audit and monitor critical data locations to ensure broad permissions are not reapplied. | Reduces risk from ransomware activities that rely on broad access. |

> Ransomware is a cybersecurity attack that encrypts or destroys files and folders, preventing users from accessing their data. The first thing you should do for these attacks is to prepare your organization so that it has an alternative to paying the ransom. Even though attackers control your organization by using various methods to pressure you into paying, the most common demands are to pay to regain access and avoid disclosure.

## Protect Assets from Ransomware Attacks

Keeping the scope of damage to a minimum is the second phase of ransomware protection. This phase involves protecting privileged roles to prevent attackers from gaining access to sensitive data and systems.

## Strategy for Privileged Access

It is essential that you implement a comprehensive strategy for reducing the risks associated with privileged access compromises. The attacker with privileged access can easily invalidate all other security controls in your environment. Ransomware attackers use privileged access to control all critical assets in the organization.

## Accountabilities of Members of Programs and Projects

Table 9.8 provides an overview of how your data will be protected from ransomware specifically from a privileged access perspective, according to the sponsorship/program management/project management hierarchy.

### TABLE 9.8 Privileged Access Perspective

| Lead | Implementor | Accountability |
| :--- | :--- | :--- |
| CISO or CIO | | Executive sponsorship. |
| Program lead | | Drive results and cross-team collaboration. |
| | IT and security architects | Prioritize components to integrate into architectures. |
| | Identity and key management | Implement identity changes. |
| | Central IT productivity/end-user team | Implement changes to devices and Office 365 tenant. |
| | Security policy and standards | Update standards and policy documents. |
| | Security compliance management | Monitor to ensure compliance. |
| | User education team | Update any password guidance. |

## Deployment Checklist

Build a multipart strategy using the guidance at aka.ms/SPA that includes the checklist shown in Table 9.9.

| Task | Description |
| :--- | :--- |
| Enforce end-to-end session security. | Access to administrative interfaces is explicitly validated (using Azure Active Directory conditional access) before users and devices are granted access. |
| Protect and monitor identity systems. | Protects directories, identities, administrator accounts, groups, and consent grant configurations from privilege escalation attacks. |
| Mitigate lateral traversal. | A single compromised device does not immediately lead to the control of many or all other devices using local account passwords, service account passwords, or other secret information. |
| Ensure rapid threat response. | Limits adversary access and time. |

## Deployment Results and Timelines

Within 30 to 90 days, try to achieve the following results:

- All administrators must be using secure workstations.
- All passwords on local workstations/servers are randomized.
- A 100 percent privilege escalation mitigation is in place.

## Detection and Response

To limit the attacker's ability to make their way around your organization laterally, you must quickly detect and remediate common attacks on endpoints, email, and identities—minutes matter.

## Accountabilities of Members of Programs and Projects

Table 9.10 provides an overview of how your data will be protected from ransomware specifically from a detection and response time perspective, according to the sponsorship/program management/project management hierarchy.

### TABLE 9.10 Detection and Response Time Perspective

| Lead | Implementor | Accountability |
| :--- | :--- | :--- |
| CISO or CIO | | Executive sponsorship. |
| Program lead from security operations | | Drive results and cross-team collaboration. |
| | Central IT infrastructure team | Implement client and server agents/features. |
| | Security operations | Integrate any new tools into security operations processes. |
| | Central IT productivity/end-user team | Enable features for Defender for Endpoint, Defender for Office 365, Defender for Identity, and Defender for Cloud Apps. |
| | Central IT identity team | Implement Azure AD security and Defender for Identity. |
| | Security architects | Advise on configuration, standards, and tooling. |
| | Security policy and standards | Update standards and policy documents. |
| | Security compliance management | Monitor to ensure compliance. |

## Deployment Checklist

Apply the best practices shown in Table 9.11 for improving your detection and response.

### TABLE 9.11 Deployment Checklist

| Task | Description |
| :--- | :--- |
| Put the following entry points at the top of the priority list: | Ransomware operators prefer end-points, email, identity, and RDP as entry points. |
| Monitor for brute-force attacks like password spraying using integrated Extended Detection and Response (XDR) tools like Microsoft 365 Defender. | |
| Password spraying is an example of a brute-force attack. | |
| Monitoring for adversaries disabling security (often as part of an attack chain) includes the following:<br>- The PowerShell Operational log and the Security Event log must be cleared.<br>- Tool and control disabling. | For a safer attack, attackers target security detection facilities. |
| The threat of commodity malware should not be ignored. | From dark markets, ransomware attackers regularly purchase access to target organizations. |
| The Microsoft Detection and Response Team (DART) can be integrated into processes to complement expertise. | To detect and recover, experience is crucial. |
| With Defender for Endpoint, you can quickly isolate compromised computers. | It's easy to do this with Windows 11 and 10. |

> > Security must be a top priority for organizations to protect privileged access due to the significant potential business impact of hackers compromising this level of access. Strategy requires a Holistic approach combining multiple technologies to protect and monitor those authorized escalation paths using Zero Trust principles, including explicit validation, least privilege and assumed breach from ransomware attacks.

## Recommend Microsoft Ransomware Best Practices

To protect against ransomware, phase 3 makes it hard for attackers to gain access. This phase involves incrementally removing the risks at the entry points of your on-premises or cloud infrastructure to make the attackers work much harder.

A ransomware attack can be prevented by hardening your infrastructure in four main areas.

- Remote access
- Email and collaboration
- Endpoints
- Accounts
