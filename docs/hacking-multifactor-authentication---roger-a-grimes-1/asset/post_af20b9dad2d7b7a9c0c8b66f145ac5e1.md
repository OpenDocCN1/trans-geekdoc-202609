
## Chapter 23 Selecting the Right MFA Solution

Table 23.1: MFA migration phase timeline estimates

| Phase | Estimated time to complete |
| :--- | :--- |
| Put together a project team. | 1 day |
| Create a project plan. | 1 week |
| Educate the project team. | 1 week (preparing and teaching) |
| Research current systems needing protection. | 1 month |
| Select desired features. | 2 weeks |
| Research MFA vendor solutions. | 1 month |
| Select multiple vendors for a pilot program. | 1 week |
| Pilot project | 3 months |
| Select a winning system. | 1 week |
| Performing a full-scale implementation | 2 to 6 months |

## Educate

Start by educating yourself about MFA. You've certainly done at least part of that by reading this book. Now share some of what you know with your fellow project team members. Everyone needs to have a basic understanding of MFA, the different types and features, and the strengths and weaknesses of each phase. The project should have a common baseline understanding so that they can help with the rest of the project. The actual project education is likely to be an hour long or whatever your organization can put aside for such things. I've been teaching computer security topics for over 30 years. Research and preparing a slide presentation on technical topics lasting an hour takes about a week to create and do right in most cases.

After the MFA solution is selected, you'll need to train users, instructors, department leaders, and help desk support, although the topic of education session will be the specific MFA product you selected versus the general education I'm talking about here.

## Determine What Needs to Be Protected

No MFA solution can protect everything. In fact, this is the biggest limitation. So your first task is determining what you want your final MFA solution to protect. Does it involve all users, just administrators, or some other smaller subset of employees? What are the protection scenarios? For a lot of administrators, an MFA solution is used to protect network logons, device logons, server logons, or email. For others, it is used to protect a handful of critical company applications. For others, it is protecting a single high-risk application or project, or a single scenario like building entry or car systems.

## Hacking Multifactor Authentication

For many companies, it's different MFA solutions for different applications, scenarios, projects. For example, by my last employer, we had a few different MFA solutions for different things with an SSO portal dropped so that one of the MFA solutions could handle dozens of our corporate applications that would otherwise not have MFA protection. And we had a few different 1FA/MFA options for other things like building and parking lot entry. The step of defining what needs to be protected is crucial. The performance of this step drives everything.

## Choose Required and Desired Features

The next step is to decide what are the required versus the nice-to-have features.

## MFA Requirements

Start with the basic types of MFA, form factors, and other starting decisions, as shown in the main requirements checklist in Table 23.2. You can use this as a starting point during your MFA solution research and evaluation. These questions can be downloaded as a Microsoft Excel spreadsheet from wiley.com/go/hackingmultifactor.

These requirements drive everything else. If an MFA solution you are interested in doesn't support something, you drop it from consideration or explain why it's still in contention.

**Table 23.2:** MFA solution main requirements checklist

| MFA solution absolute requirements | Answer |
| :--- | :--- |
| Does the MFA solution support required use cases? | |
| Does the MFA solution support required platforms? – OS | |
| Does the MFA solution support required platforms? – Client devices | |
| Does the MFA solution support required platforms? – Cloud | |
| Can the solution be cloud-based or must it be on-premises? If cloud-based, can the cloud be multi-tenancy? | |
| Does the MFA solution support required platforms? – Languages | |
| Can the MFA solution be used in all required countries? | |
| Does the MFA solution support required platforms? – Browsers | |
| Does the MFA solution work with Microsoft Active Directory, Azure AD, or RADIUS (if those are required?) | |

## Selecting the Right MFA Solution

**NOTE** An interesting website to check out is multiauth.org. It lists hundreds of features. Next, as shown in Table 23.3.

**Table 23.3:** MFA solution traits

| MFA solution traits | Answer |
| :--- | :--- |
| Hardware-based or software-based? | |
| Number of factors? | |
| Something you know, something you have, something you are? | |
| Biometric (fingerprint, face, iris, voice, etc.)? | |
| Push notifications, SMS, or codes (TOTP/HOTP)? | |
| Support for specific OS (Android, iOS, Windows, etc.)? | |
| Support for specific devices (mobile, desktop, etc.)? | |
| Integration with SSO (Single Sign-On)? | |
| Integration with directory services (Active Directory, LDAP)? | |
| Integration with PAM (Privileged Access Management)? | |
| Works with VPN or remote admin tools? | |
| FIDO compliance? | |
| Regulatory or certification requirements? | |
| Privacy and data concerns? | |
| Connection methods (USB, Bluetooth, NFC, Ethernet, etc.)? | |
| Out-of-band authentication? | |
| Recovery methods? | |
