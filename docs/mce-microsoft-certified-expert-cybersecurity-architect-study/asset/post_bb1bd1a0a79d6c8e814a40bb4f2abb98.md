
Here’s a description of the workflow depicted in Figure 6.5:

- 1. The user attempts to authenticate via the Outlook app with Azure AD.
- 2. When authenticating for the first time, the user is directed to the application store to deploy a broker app. Broker apps include Microsoft Authenticator for iOS and Microsoft Company portal for Android.
- 3. If users try to access a native email app, they’ll be redirected to the app store to deploy the Outlook app.
- 4. Get the broker app installed on your device.
- 5. The broker app creates the Azure AD registration process, which makes a device record in Azure AD. It differs from the MDM enrollment process, but the conditional access record is necessary to enforce the policies on this device.
- 6. Azure AD sign-in servers validate access to the requested service based on the Azure AD device ID, user, and application information.
- 7. The broker app transfers the App Client ID to Azure AD as part of user authentication to verify its approval.
- 8. Azure AD authenticates and grants access to the app based on the approved apps list. If the app is not on the list, Azure AD denies access.
- 9. Activating Exchange Online is accomplished through Outlook Cloud Service.
- 10. Outlook Cloud Service obtains a user’s Exchange Online service access token through Azure AD.
- 11. A user’s corporate e-mail is retrieved by Outlook using Exchange Online.
- 12. Users receive corporate emails in their mailboxes.

Using app protection, you could enforce your mobile device’s security requirements, which might include the following:

- Ensure that work files are encrypted.
- Make access to work files require a PIN; after five failed attempts, the PIN must be reset.
- Prevent work files from being backed up into public cloud services such as iTunes, iCloud, or Android backup services.
- Require the saving of work files only to OneDrive or SharePoint.
- Prevent jailbroken or rooted apps from loading work files.
- After 720 minutes of being offline, block access to work files.
- After 90 days of inactivity, work files will be removed.

## Device Settings

Along with app isolation and protection, you also need to secure the device’s settings. When an end-user mobile device is enrolled to your Microsoft 365 organization, you can manage and connect it using the Mobility and Security feature. Employees can get their work done anywhere, anytime, with mobile devices like smartphones and tablets that can access work email, calendars, contacts, and documents. Therefore, providing security policies and rules for mobile devices and wiping them if they’re lost or stolen is critical to protecting your organization’s information.

With Basic Mobility and Security, your organization can secure and manage mobile devices like iPhones, iPods, Androids, and Windows Phones. Microsoft 365 email and documents can be accessed using supported mobile devices and apps under MDM policies with settings that can help control access. It is possible to remotely wipe a lost or stolen device to remove sensitive organizational data if it is lost or stolen.

Mobile devices must be hardened following the following requirements:

- Require passwords.
- Ensure that simple passwords are not used.
- Passwords must be alphanumeric.
- Passwords must have a minimum length.
- Before a device is wiped, the number of failed sign-in attempts is counted.
- Set the number of minutes before the device is locked after inactivity.
- Establish the expiration date for password (number of days).
- Prevent reusing passwords by remembering password history.
- Encrypt devices that contain data.
- Do not support rooted or jailbroken devices.
- Block screen captures.
- Require a password for access to the application store.

You should ensure that the security settings you want to manage are available for the type of devices your organization uses when setting up your security requirements.

## Client Requirements

Your client workstation should be domain-joined. Many environments use Active Directory (AD) on-premises. A hybrid Azure AD-joined device is an AD domain-joined device that is also part of Azure AD. You can enroll hybrid Azure AD joined devices in Intune using Windows Autopilot. Enrolling would be reasonable if you had a domain join configuration profile.

It is then possible to start planning the security requirements for the operating system configuration once you have determined if the client is domain-joined. Security baselines can also include these requirements applied to devices and groups running Windows 10/11.

Intune can be used to deploy security baselines to groups or devices. The MDM Security Baseline automatically enables BitLocker for removable drives; passwords are automatically required to unlock devices, basic authentication is disabled, and more. Use a customized baseline to apply the settings you need when a default value does not work.

Security policies for clients should manage the following settings:

- Disk encryption
- Antivirus
- Windows firewall
- Attack surface reduction
- Endpoint detection and response
- Account protection

![](img/5ab9852bf401dd309bf0f81797a91445_298_0.png)

The endpoint security node in Intune provides several settings that can help protect your devices. Security admins can configure device security and manage security tasks when devices are at risk using the endpoint security node in Intune. Using endpoint security policies, you can protect your devices and mitigate risk while focusing on their security.

As recommended by the relevant Microsoft security teams for the product, security baselines in Intune are preconfigured groups of settings. The Microsoft Intune platform allows you to create security baselines for Windows 10/11 device settings, Microsoft Edge, Microsoft Defender for Endpoint Protection, and others.

Establish conditions for devices and users to access network resources and your organization network through a device compliance policy.

## Specify Requirements for Securing Active Directory Domain Services

With Active Directory Domain Services (AD DS), organizations can simplify user and resource management; create scalable, secure, and manageable infrastructure; and simplify user and resource management. AD DS can manage branch offices, Microsoft Exchange Server, and multiple autonomous environments, also known as forests.

For your AD DS deployment strategy to be successful, you must conduct a high-level assessment and identify your deployment tasks correctly. Depending on your existing network configuration, you may need to adapt your AD DS deployment strategy.

If you want to specify the requirements to secure Active Directory Domain Services, you must first recognize that threat actors often perform credential theft and target some specific accounts. As part of a credential theft attack, an attacker gains access to a computer on a network using the highest level of privilege (root, administrator, or SYSTEM, depending on the operating system) and then extracts credentials from other logged-on accounts using freely available tools. Depending on the system’s configuration, these credentials can be removed as hashes, tickets, or plaintext passwords.

Administrators must be aware of activities that increase the likelihood of a credential-theft attack because high-privileged domain accounts and VIP accounts are usually targets of credential theft. Although attackers also target VIP accounts, stealing their credentials requires other attacks, such as social engineering the VIP to provide secret information.

The core vulnerability that allows credential theft attacks to succeed is logging on to computers that are not secure with accounts that are widely and deeply privileged throughout the environment. So you need to minimize the attack surface as part of securing AD DS, which includes the following tasks:

- **Deploy Least-Privilege Administrative Models** Explores the risks associated with using highly privileged accounts for the day-to-day administration and provides recommendations for reducing those risks.

- **Deploy Secure Administrative Hosts** Provides examples of approaches to deploying secure administrative hosts and principles for deploying secure administrative systems.

- **Defending Domain Controllers to Prevent Attack** Describes policies and settings that, although similar to recommendations for implementing secure administrative hosts, provide some domain controller–specific recommendations to help ensure that domain controllers and their management systems are secure.

A trusted system (for example, a domain controller) should never be administered from a less trusted host (a workstation that doesn’t have the same level of security as the systems it manages). When performing privileged activities, you should rely on more than one authentication factor; for example, usernames and passwords should not be considered acceptable authentication because they represent only a single factor (what you know). Credentials generated in administrative scenarios should be cached or stored somewhere.

## Securing Domain Controllers Against Attack

As well as providing the physical storage for the Active Directory Domain Services (AD DS) database, domain controllers enable enterprises to effectively manage their servers, workstations, users, and applications. Assume that a malicious user obtains access to the domain controller. The AD DS database and, by extension, all the systems and accounts managed by Active Directory can be modified, corrupted, or destroyed in such a scenario.

Because domain controllers can read from and write to anything in the AD DS database, if a domain controller is compromised, your Active Directory forest can be considered
