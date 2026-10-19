
![](img/3be1e4f35d99b14a974b22ecf8355b5e_892_0.png)

Figure 5.7 — Hand Geometry reader

## Voice Recognition

Voice recognition identifies the voice characteristics of a given phrase to that of one held in a template. Voice recognition is generally not performed as one function, and it is typically part of a system where a valid PIN must be entered before the voice analyzer is activated. An advantage of voice recognition is that the technology is less expensive than other biometric technologies. Additionally, it can be operated hands-free. A disadvantage is that the voice synthesizer must be placed in an area where the voice is not disturbed by background sounds. Often a booth or a security portal has to be installed to house the sensor in order to provide the system with an acceptable quiet background.

## Iris Patterns

Iris recognition technology scans the surface of the eye and compares the iris pattern with stored iris templates. Iris scanning is the most accurate biometric technology. A benefit of iris recognition is that it is not susceptible to theft, loss, or compromise, and irises are less susceptible to wear and injury than many other parts of the body. Newer iris scanners allow scanning to occur from up to ten inches away. A disadvantage of iris scanning is that some people are timid about having their eye scanned. Throughput time for this technology should also be considered. Typical throughput time is two seconds. If a number of people need to be processed through an entrance in a short period of time, this can be problematic.

The EOFFI retinal scanner reads from the outer iris in towards the pupil edge. The retinal scanner then plots distinct patterns of blood vessels using infrared light

![](img/3be1e4f35d99b14a974b22ecf8355b5e_894_0.png)

After scanning the information is then sent to a central server where the results are compressed

Upon entering the facility, the client's retinal map will be compared to their stored compressed information

Figure 5.9 – How Retinal Scanners record identity
(http://www.eofti.com/about/retinal-scan/)

## Signature Dynamics

First, the signer writes out a handwritten signature on a special electronic pad, such as the ePad by Interlink or a Palm Pilot. The shape of the signature is then electronically read and recorded, along with such unique features as the pressure on the pen and the speed at which the signature was written in order to identify the signer's unique writing; for example, did the "t" get crossed from right to left and did the "i" get dotted at the very end?

The advantage of signature dynamics is that it works like a traditional signature. Signers do not need special knowledge of computers nor any unusual tools to make a signature. At the same time, the system allows the notary to record unique identifying features to help prevent and detect forged signatures. For example, if a forger attempted to copy the signature of another person and wrote slowly to try and create a visually identical style of writing, an analyst could compare it with the data to detect the slower writing speed and recognize it as a different signer.

![](img/3be1e4f35d99b14a974b22ecf8355b5e_897_0.png)

Figure 5.12 – Sample Keystroke Dynamics measurements
(http://bit.ly/typeprint_technology)

## Accountability

Ultimately, one of the drivers behind strong identification, authentication, auditing, and session management is accountability. Accountability is fundamentally about being able to determine who or what is responsible for an action and can be held responsible. A closely related information assurance topic is non-repudiation. Repudiation is the ability to deny an action, event, impact, or result. Non-repudiation is the process of ensuring a user may not deny an action. Accountability relies heavily on non-repudiation to ensure users, processes, and actions may be held responsible for impacts. The following contribute to ensuring accountability of actions:

- Strong identification
- Strong authentication
- User training and awareness
- Comprehensive, timely, and thorough monitoring
- Accurate and consistent audit logs
- Independent audits
- Policies enforcing accountability
- Organizational behavior supporting accountability

### Strong Identification

For accountability to be successful, an action must be attributable to a single individual, process, device, or object. Without the ability to directly associate an action with an individual, repudiation of the action can arise. One of the most prevalent examples of this is the use of shared accounts. When several people have access to a single account, the ability to directly associate an action performed through the account with an individual diminishes rapidly as users are able to blame others with plausible deniability.

### Strong Authentication

Weak authentication not only makes it easier for an attacker to take control of an account with no accountability, but it also allows users to blame weak authentication on account abuses. Strong authentication such as biometrics helps ensure non-repudiation by strongly associating something only one individual has to an account. While not perfect, strong authentication with strong identification greatly increases accountability.

### User Training and Awareness

Users need to be trained and have a basic awareness of the penalties for misuse of accounts, information, and systems. Informed users are less likely to intentionally or unintentionally abuse accounts, access, or information if they are aware of the consequences. A well-structured and repeated security awareness program is generally accepted as a baseline for ensuring users understand consequences and acceptable behaviors. The security professional may want to use login banners as one of many tools to reinforce the messages and behaviors that user training and awareness programs are designed to instill in users.

### Monitoring

Monitoring must be sufficient to detect problems and violations with accounts, access, information egress, and system operation. If an organization does not have visibility into an information system, it is unlikely the organization will know when accountability issues surface. Monitoring technologies such as data loss prevention (DLP), intrusion detection systems (IDS), intrusion prevention systems (IPS), and firewalls can be implemented to increase visibility and therefore greatly strengthen accountability. It is up to the security architect and the security practitioner both to ensure that systems are designed and deployed that address the issues of monitoring from a bi-directional perspective across the enterprise. If the traditional bias and focus of these systems is maintained, and they only address perimeter-based external oriented monitoring, then they will be of limited use to the enterprise. The need to ensure that visibility is created with regards to internal activities and information flows is of equal importance.

### Audit Logs

Audit logs are necessary in the event an action must be traced back to a user. Audit logs from DLP, IDS, servers, firewalls, and other network devices should be collected and consolidated as much as possible. Often these logs are collected into a Security Information and Event Management (SIEM) system. SIEMs are used in conjunction with analytical tools to correlate information and help "tell the story" of what happened. They are highly useful in helping ensure accountability.

### Independent Audits

Independent audits help ensure accountability by bringing in an unbiased third party to review accounts, actions, and impacts. Independent audits, investigations, or reviews are required to establish accountability when collusion may have occurred between several parties. Routine independent audits can also set a tone throughout the organization that corrupt practices are not tolerated.

### Policy

An organization’s policy must recognize the need for accountability and provide expectations of behavior and define sanctions and rewards for accountability related behaviors. Some organizations have an "integrity" award for outstanding acts of accountability in difficult situations. Without a policy, accountability cannot be enforced consistently and fairly throughout an organization.

### Organizational Behavior

Arguably the most significant aspect of ensuring accountability is the culture of the organization. An organization that does not set the "tone at the top" for accountability expectations is unlikely to receive the support necessary to implement accountability controls throughout the organization. Additionally, if violations of accountability are not met with timely and consistent treatment, further instances of accountability violations can be expected.

### Session Management

With the increase in Web-based applications and cloud computing, access controls must be viewed in light of session management. "Session management" is a term used to describe how a single instance of identification and authentication is applied to resources. For example a "desktop" session manager may allow a user to maintain a particular set of open applications, files, and functions while simultaneously starting another desktop session with a different set of applications, files, and functions. Many Unix and Linux operating systems offer this capability. Web browsers also rely on sessions to manage access to Web applications and resources often through the use of cookies or other session monitoring and tracking technologies. While session management provides ease of use and flexibility for the end-user, it also provides an avenue of attack.
