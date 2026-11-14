
For access control to be effective, an authentication process must support the controls. To properly identify personnel and grant them appropriate access levels, it’s useful to understand two types of authentication: Multifactor authentication is present when at least two conditions are satisfied independently by the same individual who wants to access a network, system, or application. In many contexts, multifactor authentication and two-factor authentication are synonymous based on how many conditions must be satisfied. When an organization implements proper multifactor authentication, the process is recognized as strong authentication.

To gain access, an end user must provide something a person knows (password/PIN), something they have (a physical token/badge), something they are (biometrics), or some combination of those three factors. To be clear, this means the person can verify at least two of the following things^([8](#ch8.html#ch8en8)):

- What I know (authentication by knowledge)
- What I have (authentication by ownership)
- Who I am (authentication by characteristic)

## Access Control Models

Several access control models are used to enforce authentication and authorization guidelines, and the controls used are automated. (Imagine how difficult it would be to manually check the credentials of each end user every time they desired access to data or to a system!) The common models for access control are mandatory, discretionary, and role-based. There are some hybrid models that combine features of each, but these three are fundamental ones.

---

> ![image](note.jpg) **NOTE** Although these models are enforced by computer policies and configurations, some information security guidelines have provisions for overriding these policies and configurations, or for emergency access. The best example is the provision in HIPAA to provide “break glass” access in emergency situations. In other words, the system has a method for providing access to someone who may not have authorization or access under normal circumstances.

### Mandatory Access Control

The first type of access control model is mandatory access control, in which a central authority such as the organization’s CIO makes the access control policy, which is implemented by the IT department. The actual access control is enforced at the hardware or operating system level as a technical control. Most often, mandatory access control is used in organizations that handle classified information—for example, a military organization. It is valid to include mandatory access control in this context because it is relative to a healthcare organization where rigid, centralized controls are used in some applications and networked resources. In this model, individual system or data owners do not have the ability to change the level of access allowed. A mandatory access control model depends on proper security categorization of information because the access policy in this case most likely will be determined by the sensitivity of the information. In some organizations, there may be confidential information, in which case the central authority can determine who is allowed access to this type of information. Improperly categorized information can lock out individuals who may need access, or it may allow access to those who have no need to know the information. Neither case is desired. On the positive side, having a central authority enforce the access control makes standard, equitable policies possible.

### Discretionary Access Control

A discretionary access control model is used if access control is more decentralized or delegated to the owner of the individual system or to the owner of the data itself. Privileges are granted by the system owner or data owner to whomever he or she considers authorized to access the information. Discretionary access control is more flexible than mandatory access control, but it introduces greater risk. For instance, once someone has access to view a file, the system owner has no control over whether that person decides to copy it and allow others to view the file.

### Role-Based Access Control

Probably the most prevalent type of nondiscretionary access control model is role-based access control, in which system owners determine the level of access based on a user’s or group’s job function or organizational role. For instance, there may be one type of access control for physicians in pediatrics and another for nurses in the same department. One component of a role-based access model is an access control list (ACL), a list that indicates which personnel have access rights to certain objects or delineates which personnel have specific types of access rights, such as read, write, or delete access. An ACL is the most common way of implementing role-based access controls.

---

> ![image](note.jpg) **NOTE** Another use of the term ACL relates to firewall or router rules, and the concept is very similar. A firewall ACL is a list of ports and Internet Protocol (IP) addresses that are allowed to access the organization IT resources under predetermined circumstances (using certain protocols). This type of ACL could be thought of as role-based access control for IT systems instead of personnel.

## Data Encryption

Data encryption is a technical control or solution to protect information confidentiality. Strictly speaking, encryption does not focus on protecting or providing data integrity or availability; however, cryptographic algorithms, called hashing algorithms, do provide for data integrity. Sensitive data, such as PHI and PII, must be encrypted under the prevailing information security standards, such as HIPAA and ISO 27001, to name just two. There are two states in which data can (and should) be encrypted: when it is “at rest” and when it is “in transit.” The first state, at rest, refers to data that is stored on any media and is not currently being processed or transmitted. If data at rest has been encrypted, media that is lost or stolen and recovered by someone unauthorized to view the data will be unusable or unreadable to the person who finds it. In this case, the only people who can access the data are those who possess the cryptographic key to decrypt the information. There are two common ways of applying this type of encryption using encryption applications. One is to encrypt the entire volume of information on the disk with the same encryption key, and the other is to encrypt at the file level. Encrypting the entire volume of the disk has benefits in that human error is minimized because users may forget or neglect to encrypt data if any part of the process is manual or discretionary, as file-level encryption can be.
