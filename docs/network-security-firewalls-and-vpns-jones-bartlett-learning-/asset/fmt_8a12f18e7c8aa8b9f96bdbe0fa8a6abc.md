
# Trust and Security Objectives

## Third-Party Trust

Trust can also come from using a third-party method. If a trustworthy third party knows you and me, and that third party states that you and I are both trustworthy people, then you and I can assume that we can conditionally trust each other. Over time, someone’s behavior shows whether the initial conditional trust was merited or not.

A common example of a third-party trust system is the use of digital certificates that a public certificate authority issues. As shown in [Figure 1-1](#07_chapter01.xhtml#fig1-1), a user communicates with a Web e-commerce `server`. The user does not initially know whether a Web server is what it claims to be or if someone is “spoofing” its identity. Once the user examines the digital certificate issued to the Web server from the same certificate authority that issued the user’s digital certificate, the user can then trust that the identity of the Web site is valid. This occurs because both the user and the Web site have a common, trustworthy third party that they both know.

Ultimately, network security is based on trust. Companies assume that their employees are trustworthy and that all of the computers and network devices are trustworthy. But not all trust is necessarily the same. You can (and probably should) operate with different levels or layers of trust. Those with a higher level of trust can be assigned greater `permissions` and `privileges`. If someone or something violates your trust, then you remove the violator’s access to the secure environment. For example, companies terminate an untrustworthy employee or replace a defective operating system.

![Image](images/pg5.jpg)

**FIGURE 1-1**

An example of a third-party trust system.

## Who—or What—Is Trustworthy?

Determining who or what is trustworthy is an ongoing activity of every organization, both global corporations and a family’s home network. In both cases, you offer trust to others on a conditional basis. This conditional trust changes over time based on adherence to or violation of desired and prescribed behaviors.

If a program causes problems, it loses your trust and you remove it from the system. If a user violates security, that person loses your trust and might have access privileges revoked. If a worker abides by the rules, your trust grows and privileges increase. If an Internet site does not cause harm, you deem it trustworthy and allow access to that site.

To review, trust is subjective, tentative, and changes over time. You can offer trust based on the reputation of a third party. You withhold trust when others violate the rules. Trust stems from actions in the past and can grow based on future behaviors.

In network security, trust is complex. Extending trust to others without proper background investigation can be devastating. A network is only as secure as its weakest link. You need to vet every aspect of a network, including software, hardware, configuration, communication patterns, content, and users, to maintain network security. Otherwise, you will not be able to accomplish the security objectives of your organization’s network.

## What Are Security Objectives?

**Security objectives** are goals an organization strives to achieve through its security efforts. Typically, organizations recognize three primary security objectives:

![Image](images/bull1.jpg) Confidentiality/privacy

![Image](images/bull1.jpg) Integrity/nonrepudiation

![Image](images/bull1.jpg) Availability/uptime

**Confidentiality** is the protection against unauthorized access, while providing authorized users access to resources without obstruction. Confidentiality ensures that data is not intentionally or unintentionally disclosed to anyone without a valid need to know. A **job description** defines the person’s need to know. If a task does not require access to a specific resource, then that person does not have a need to know that resource.

**Integrity** is the protection against unauthorized changes, while allowing for authorized changes performed by authorized users. Integrity ensures that data remain consistent, both internally and externally. Consistent data do not change over time and remain in sync with the real world. Integrity also protects against accidents and hacker modification by `malicious code`, or software written with malicious intent.

**Availability** is the protection against `downtime`, loss of data, and blocked access, while providing consistent uptime, protecting data, and supporting authorized access to resources. Availability ensures that users can get their work done in a timely manner with access to the proper resources.

**Authentication** is the proof or verification of a user’s identity before granting access to a secured area. This can occur both on a network as well as in the physical, real world. While the most common form of authentication is a password, password access is also the least secure method of authentication. Multifactor authentication is the method most network administrators prefer for secure logon.

**Authorization** is controlling what users are allowed and not allowed to do. Authorization is dictated by the organization’s security structure, which may focus on discretionary access control (DAC), mandatory access control (MAC), or role-based access control (RBAC). Authorization restricts access based on need to know and users’ job descriptions. Authorization is also known as access control.

Nonrepudiation is the security service that prevents a user from being able to deny having performed an action. For example, nonrepudiation prevents a sender from denying having sent a message. **Auditing** and public-key cryptography commonly provide nonrepudiation services.

**Privacy** protects the confidentiality, integrity, and availability of personally identifiable or sensitive data. Private data often includes financial records and medical information. Privacy prevents the unauthorized watching and monitoring of users and employees.

Maintaining and protecting these security objectives can be a challenge. As with most difficult tasks, breaking security down into simpler or smaller components will help you to understand and ultimately accomplish this objective. To support security objectives, you need to know clearly what you are trying to protect.

## What Are You Trying to Protect?

In terms of security, the things you want to protect are known as assets. An **asset** is anything used to conduct business. Any object, computer, program, piece of data, or other logical or physical component employees need to accomplish a task is an asset.

Assets do not have to be expensive, complicated, or large. In fact, many assets are relatively inexpensive, commonplace, and variable in size. But no matter the characteristics, an asset needs protection. When assets are unavailable for whatever reason, people can’t get their work done.

For most organizations, including `SOHO (small office, home office)` environments, the assets of most concern include business and personal data. If this information is lost, damaged, or stolen, serious complications result. Businesses can fail. Individuals can lose money. Identities can be stolen. Even lives can be ruined.

What causes these problems? What violates network security? The answer includes accidents, ignorance, oversight, and hackers. Accidents happen, including hardware failures and natural disasters. Poor training equals ignorance. Workers with the best of intentions damage systems if they don’t know proper procedures or lack necessary skills. Overworked and rushed personnel overlook issues that can result in asset compromise or loss. Malicious `hackers` can launch attacks and `exploits` against the network, seeking to gain access or just to cause damage.
