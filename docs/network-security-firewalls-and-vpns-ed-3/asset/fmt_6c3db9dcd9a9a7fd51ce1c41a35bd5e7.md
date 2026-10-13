
# Controlling Access to Your Network

Controlling access to your network, and the types of actions users may perform, greatly reduces the risk of a successful breach. Encryption helps to protect sensitive data whether it is in storage or transit. Keep the following best practices in mind when securing your network:

*   **Limit and filter Internet connectivity**—An unrestricted or unfiltered Internet connection is a pathway for malicious code, social engineering attacks, and intrusion attempts. If an Internet service, protocol, domain, or Internet Protocol (IP) address is not essential to a necessary business task, block it. Computer access to the organization’s network and assets is for work tasks, not personal activities.

*   **Implement multifactor authentication**—[Single-factor authentication](#30_glossary.xhtml#gloss458), especially password-based authentication, is no longer a truly secure or sufficient method of protecting the logon process. Adding at least one additional factor significantly increases the authentication security of the environment. Once multifactor authentication begins, allow no exceptions that fall back on single-factor solutions. Otherwise, intrusion efforts will focus on the single-factor pathway as it is the weakest link in the network’s defenses.

*   **Do not rely on authentication at session initiation alone**—Session hijacking is a serious threat on most commonly used protocols. Use solutions that support periodic midstream reauthentication, as well as communications encryption.

*   **Eliminate or severely limit remote access**—When possible, avoid remote access. Limit access to local direct connections only. When remote access is necessary, require a virtual private network (VPN). Once you allow remote connectivity, you allow the possibility of remote hacking. Remote hacking attempts to breach security without the need to be physically at or within the target’s facilities. Requiring VPNs for all remote connections reduces this threat by preventing open connections or communications vulnerable to eavesdropping.

*   **Restrict access**—Focus on establishing a philosophy of default deny rather than default allow. By blocking everything as a starting point, only those features, services, protocols, ports, applications, and users that management deems safe and appropriate can be enabled by exception. A default-permit stance means you must create a never-ending stream of explicit denials as you detect new compromises or malicious events. *Deny by default/allow by exception* is always the preferred security stance.

*   **Employ device and file encryption**—Any device that is portable or easily accessible by a nonemployee should use [whole hard drive encryption](#30_glossary.xhtml#gloss549) or at least [file encryption](#30_glossary.xhtml#gloss179). Although it is not absolutely foolproof, encrypting an entire hard drive makes accessing the data on a portable device much more complex. If a system is stolen when powered off, the hard drive’s encryption typically presents an insurmountable barrier. If the equipment is running when stolen, a hacker might bypass the hard drive encryption by hacking the encryption key out of active memory. However, this is an unlikely attack.

*   **Encrypt network traffic**—Require encryption of all internal network communications. Use IPSec to secure all intranet communications. This is often an easy and cost-effective means to quickly reduce the risk of eavesdropping, man-in-the-middle, replay, and many other forms of network attacks. Well-encrypted data is much less likely to fall into the hands of hackers, thieves, and unauthorized personnel.

*   **Implement whitelist application control**—A whitelist is a list of allowed exceptions against a background of default deny. By configuring a system with a whitelist, you block all executables unless each is on the list of allowed exceptions. A whitelist consists of the application name, its file name, and the file’s hash value. This prevents spoofing by malicious or unapproved applications that simply rename the executable.

## Technical TIP

Don’t overlook the importance of authentication, authorization, and accounting. These services are essential to a secure infrastructure. You must control who is allowed onto the network (authentication); place limitations on what users can do (authorization); and hold all entities—even upper-level management—accountable for their actions, activities, and results (accounting).

Remember, the strongest security comes in layers, making it difficult for an attacker to break through each line of defense to gain access.

## Physical Security

There is no security without physical security. Logical protections can protect only against logical attacks. Physical protections protect against physical attacks. With just a few moments of physical contact, a hacker can overcome or bypass most logical security.

Physical security is the prevention of direct physical contact, access, or influence of an unauthorized person to a sensitive component of an IT infrastructure. Any well-designed network security solution will include physical security components. If you fail to address physical security adequately, you fail to understand the threats facing your organization.

Physical security includes a facility that resists forcible entry. Select, improve, or build facilities that prevent and deter unauthorized physical intrusion. If physical breaking and entering is possible and potentially profitable for a thief, it is more likely to take place.

Physical security should include the monitoring of all personnel activity. Solid physical access control includes keeping track of when an employee enters and exits every secured or sensitive area. Good physical access control blocks outsider access and enforces escorts for visitors, consultants, and other authorized nonemployees. This is an often-violated area of a security policy. Locks on the doors serve a purpose but may be bypassed if there is no monitoring or alarm. Consider the employees who prop open the back door to a facility when they leave to take a smoke break. If the doorway is out of their view, anyone could sneak inside. Even if they can watch from where they are, how many would confront a stranger and attempt to deter their entry? Unfortunately, we live in a world with active shooters and those who would harm us because of where we work, our religious or political beliefs, or simply because they can. Bypassing physical security essentially renders all other security components ineffective.

All servers and important devices should be kept in locked and secured areas to prevent tampering and accidents. When labeling a device, it is helpful to identify an internal strategy for easy access that would not be recognizable to an outsider. Instead of affixing a label noting “web server” and the corresponding IP and Media Access Control (MAC) addresses, it would be more secure to simply denote the information in a code known to IT administration staff, but not to others.

Physical security should include card key entry, burglar alarms, motion detectors, and security cameras. Use the best available technology to both deter and detect physical security violations. Education in physical security is also essential. For example, our natural tendency is to hold a door for someone entering a facility, but that would defeat the key card required for entry and fail to provide an accurate accounting of who entered the building and at what time. This could be disastrous if there was an emergency or evacuation and an accurate head count was necessary.

## Techniques for Preventing and Deterring Incidents
