
## Chapter 10 Subject Hijack Attacks 239

of privilege where one admin had the ability to do something another admin did not (for example, be an Exchange Administrator).

This is not to say that this type of maliciousness cannot be noticed and stopped. The changing of the UPN usually creates an event in the Windows log file that shows the UPN is changed and what it changed to. Unless someone was looking for that and alerted on it, it would probably go unnoticed. And there are some log events, such as Event ID 4768, registered at the involved domain controllers which would include such smartcard's fingerprint, which would be reviewed as evidence to reveal that the Help Desk user's smartcard was somehow associated with the Super Admin account. But forensics investigators would have to be aware of and to validate this particular hack scenario. We would have to know that a particular certificate was printed to the Help Desk user and not Super Admin. It would be something most people looked for unless they knew it was even a possibility and what to look for. Even then, it's such a rare case (i.e., it's never been done in the kind of), that it's probably not going to be the first thing most incident responders check for. It's not going to be what most incident responders ever check, first or last. Beyond the people reading this chapter, perhaps a few dozen in the world would know about this link between smartcard and AD, and how it can be abused. Welcome to a very small group.

There are other related hacks. For anyone who is able to generate a trusted smartcard that anyone else can log in as that user. In the first example, we modified the Super Admin's UPN to helpdesk@victim.com. But we could simply generate a brand-new smartcard that contains the UPN of superadmin@victim.com and be able to log as Super Admin. I've done this technique using a "foreign" CA (i.e., a CA belonging to another organization) that was simply installed as a CA in the victim organization. The foreign CA can generate smartcards with the victim's UPN. Again, the only evidence a forensic examiner might find is a certificate fingerprint in the logs that doesn't match the Super Admin's certificate thumbprint.

To be clear, this is not a real hack or bug. Microsoft is not going to fix this. This is an "as-designed" outcome in which the Active Directory-integrated smartcards work. Smartcards are tied to a user's UPN and the Help Desk user changed UPNs. So, in Active Directory's defense, it did map the "user account to the authenticated smartcard as was defined in Active Directory. Active Directory has no way of knowing which UPN is the correct UPN over.

The defense to the smartcard hijack attack is not able to make sure unauthorized UPNs and to prevent smartcard administrators from simply creating any smartcard with any UPN they like. More realistically, log UPN changes (there are legitimate reasons why they occur as due to changes from marriage and divorce) and make sure the change was authorized. And make sure you trust your admins. Administrators are very powerful accounts that can do a lot of malicious things, well beyond just hijack attacks. You need to make sure your admins are trustworthy as rule #1.

## The Broader Issue

As covered in Chapter 2, “Authentication Basics,” the act of validating an authentication credential can, and often is, separate from the resulting authorization and access control processes. In this particular scenario, the smartcard authentication process (i.e., that the user is presenting a valid, trusted smartcard with a valid UPN and the associated PIN) and the access control and authorization process (where the “validated” user is handed their group memberships and privileges in an access control token), to Active Directory, almost completely separate. Once a valid, trusted smartcard and the correct PIN is typed in, there is no way (in the most common smartcard scenarios) for Active Directory know the valid UPN supplied should be mapped to the user account that contains it. It’s that Active Directory and smartcards were made to work with each other.

The general protection against these MFA abuses is to realize that any time you use an attribute, such as subject UPN, as an authentication solution, the involved attribute needs to be protected and monitored as if it were an authentication secret. Most administrators are taught to secure other authentication secrets, such as password hashes, as if they were the keys to the kingdom—and they are. But most admins are not taught to protect and monitor the other involved authentication attributes, though their malicious modification can have similar security impacts.

## Dynamic Access Control Example

Let me give another example attack to clarify further. Since Windows Server 2012/2016, Microsoft Windows and Active Directory allow Dynamic Access Control (DAC) and Central Access Policy (CAP) to control a subject’s authentication (see docs.microsoft.com/en-us/windows/security/identity-protection/access-control/dynamic-access-control for more details) in nearly a more feature-rich, granular way.

With Traditional Windows security, a subject (e.g., user, computer, service) can access is determined by their membership in groups and what individual and privileges they were given on various objects. With DAC/CAP, dozens of other elements, such as attributes and location, can be used to determine whether or not a subject can access a particular object. For example, the user is in a U.S. location and in the Accounting department? As Figure 10.16 shows, that question can now be asked to determine whether or not someone in a group is given access to a file. With traditional Windows security, the question would have much simpler: is the user a member of the Authenticated Users group? But with DAC/CAP, the question can be more granular: is the user a member of the Authenticated Users group, in the Accounting department, and located in the United States?

![Figure 10.16](link_to_image)

## Chapter 10 Subject Hijack Attacks 242

**Figure 10.16 Example of using DAC/CAP:** (link_to_image)

The problem is that any attribute used becomes a critical point. Most administrators are taught to secure other authentication secrets, such as password hashes, as if they were the keys to the kingdom—and they are. But most admins are not taught to protect and monitor the other involved authentication attributes, though their malicious modification can have similar security impacts.

## ADFS MFA Bypass

In 2018, MFA vendor, Okta, found out (www.darkreading.com/threat-intelligence/adfs-vulnerability-lets-attackers-bypass-mfa/d-id/1332553) that the MFA credential didn't have to belong to the same user. Possession of a valid MFA solution allowed that to pose as any user, bypassing the requirement that actual MFA be used part of account. This was definitely an error and Microsoft patched.

## Defenses to Component Attacks

The following sections highlight some defenses to component attacks.

## Threat Model Dependency Abuse Scenarios

All authentication solutions should be threat modeled and include all the various dependencies that the solution relies on to be accurate. Use Figure 5.1 in Chapter 5 as a starting point to begin discussions. I cannot recommend any higher Adam Shostack's Threat Modeling: Designing for Security (Wiley, 2014) for those who want to improve your threat modeling skills. All threat modelers should identify all critical dependencies and see whether dependency risks can be mitigated or minimized. All inputs should be considered untrusted by default.

## Secure Critical Dependencies

All critical dependencies for MFA solutions should be as secure as possible. This means that user and group hygiene has been performed to minimize which users and groups can access and modify various components, and those remaining who are allowed should be given least privilege permissions. Better yet, make all modifications require a checkout of a time-bound elevated credential access and is tracked. Critical dependencies need to be treated like passwords and password hashes, and protected accordingly.
