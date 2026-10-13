
# 核心安全目标

[Confidentiality](#30_glossary.xhtml#gloss96) is the protection against unauthorized access, while providing authorized users access to resources without obstruction. Confidentiality ensures that data is not intentionally or unintentionally disclosed to anyone without a valid need to know. A job description defines the person’s need to know. If a task does not require access to a specific resource, then that person does not have a need to access that resource.

[Integrity](#30_glossary.xhtml#gloss243) is the protection against unauthorized changes, while allowing for authorized changes performed by authorized users. Integrity ensures that data remains consistent, both internally and externally. Consistent data does not change over time and remains in sync with the real world. Integrity also protects against accidents and hacker modification by [malicious code](#30_glossary.xhtml#gloss289), or software written with malicious intent.

[Availability](#30_glossary.xhtml#gloss40) is the protection against [downtime](#30_glossary.xhtml#gloss148), loss of data, and blocked access, while providing consistent uptime, protecting data, and supporting authorized access to resources. Availability ensures that users can get their work done in a timely manner with access to the proper resources. Availability, for example, ensures that web resources are accessible, so sales are not lost.

[Authentication](#30_glossary.xhtml#gloss35) is the proof or verification of a user’s identity before granting access to a secured area. This can occur on a network or in the physical, real world. While the most common form of authentication is a password, passwords can be accidentally shared or stolen, especially if written down. Multifactor authentication is the method most network administrators prefer for secure logon, as it requires multiple proofs of one’s identity.

[Authorization](#30_glossary.xhtml#gloss39) is controlling what users are allowed and not allowed to do. Authorization is dictated by the organization’s security structure, which may focus on discretionary access control (DAC), mandatory access control (MAC), or role-based access control (RBAC). Authorization restricts access based on need to know and users’ job descriptions. Authorization is also known as [access control](#30_glossary.xhtml#gloss2).

[Nonrepudiation](#30_glossary.xhtml#gloss322) is the security principle that prevents a user from being able to deny having performed an action. For example, nonrepudiation prevents a sender from denying having sent a message. Public-key cryptography commonly provides nonrepudiation services.

[Privacy](#30_glossary.xhtml#gloss362) protects the confidentiality, integrity, and availability of personally identifiable or sensitive data. Private data can include financial records or medical information. Privacy prevents the unauthorized watching and monitoring of users and employees.

Maintaining and protecting these security objectives can be a challenge. As with most difficult tasks, breaking security down into simpler or smaller components will help you to understand and ultimately accomplish this objective. To support security objectives, you need to know exactly what you are trying to protect.

## What Are You Trying to Protect?

In terms of security, the things you want to protect are known as assets. An [asset](#30_glossary.xhtml#gloss28) is anything used to conduct business. Any object, computer, program, piece of data, or other logical or physical component that employees need to accomplish a task is an asset.

Assets do not have to be expensive, complicated, or large. In fact, many assets are relatively inexpensive, commonplace, and variable in size. But no matter the characteristics, an asset needs protection. When assets are unavailable for whatever reason, employees cannot complete their work.

For most organizations, whether small or large, the assets of highest concern include business and personal data. If this information is lost, damaged, or stolen, serious complications result. Businesses can fail. Individuals can lose money. Identities can be stolen. Lives can be ruined.

What causes these problems? What violates network security? The answer includes accidents, ignorance, and hackers. Accidents happen, including hardware failures and natural disasters. Poor training equals ignorance. Workers with the best of intentions can damage systems if they do not know proper procedures or if they lack necessary skills. Overworked and rushed personnel overlook issues that can result in asset compromise or loss. Malicious hackers can launch attacks and [exploits](#30_glossary.xhtml#gloss166) against the network, seeking to gain access or simply to cause damage.

### Seven Domains of a Typical IT Infrastructure

No aspect of an IT infrastructure is without risk, nor is it immune to the scrutiny of a hacker. [Risk](#30_glossary.xhtml#gloss410) is the likelihood that a threat will take advantage of a [vulnerability](#30_glossary.xhtml#gloss539). When designing and implementing network security, you need to analyze every one of the seven [domains](#30_glossary.xhtml#gloss145) of a typical IT infrastructure ([**FIGURE 1-2**](#10_chapter01_02.xhtml#fig1-2)) for potential vulnerabilities and weaknesses. Security measures must be detailed, focused, and exhaustive. You must consider every possible avenue of attack; assess risk; and if the risk is sufficient, apply a [countermeasure](#30_glossary.xhtml#gloss104). Failing to do so will leave an open pathway for a hacker. A hacker needs only one crack in your defenses to begin chipping away at the security of the entire network.

![FIGURE 1-2 The seven domains of a typical IT infrastructure.](Images/9781284183658_CH01_FIGF02.png)

**FIGURE 1-2** The seven domains of a typical IT infrastructure.

Each of the seven domains of a typical IT infrastructure has unique aspects that need security improvements. The following sections describe important foundational network security issues related to the seven domains.

#### User Domain

This domain refers to actual users, whether they are employees, consultants, contractors, or other third-party users. Any user who accesses and uses the organization’s IT infrastructure must review and sign an acceptable use policy (AUP) prior to being granted access to the organization’s IT resources and infrastructure. This domain should also focus on training, strong authentication, granular authorization, and detailed accounting. Additionally, many of the protections added to other domains provide additional protections for and against the User Domain.

Social engineering is a hacker attack against people. This type of attack attempts to fool people through clever wording, lying, misdirection, relationship manipulation, fear, psychological tricks, and confidence games. The results of social engineering attacks can include users giving away private information or performing actions on a computer that cause a reduction in network security.

#### Workstation Domain

This domain refers to the end user’s desktop devices, such as a desktop computer, laptop, Voice over Internet Protocol (VoIP) telephone, or other endpoint device. Workstation devices typically require security countermeasures such as antivirus, anti-spyware, and vulnerability software patch management to maintain the integrity of the device.

The workstation, client, or standalone home system can be a target. These types of hosts are often less secure than local area network servers. This is not on purpose, because most security focuses on core components of the infrastructure, rather than those seemingly on the periphery. Many times, the security measures on a workstation are old, out-of-date, or improperly installed and configured. System hardening, communication protection, and positioning of work stations are critical to security.

#### LAN Domain
