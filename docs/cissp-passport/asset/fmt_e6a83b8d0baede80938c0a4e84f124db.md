
The controls for securing and protecting information cannot just be randomly picked. Many factors go into control selection, some of which include the state the data is in, the type of data, and the governance requirements for the data. Data states influence which controls are used, and how controls are implemented to meet the specific needs of the data that requires protecting.

## Data States

Raw data and, when placed in context, information are categorized as always being in one of three states: at rest, in use (or in process), and in transit. Many of the security controls that are selected to protect data are focused on one or more of these three states, which we will discuss next.

### Data in Transit

Data in transit is simply data that is being actively sent across a transmission media such as cabling or wireless. Data in this state is vulnerable to eavesdropping and interception if it is not properly protected. Controls traditionally used to protect data while in transit include strong authentication and transmission encryption. Examples of protocols and other mechanisms used to protect data during transmission include Transport Layer Security (TLS), Secure Shell (SSH), hardware encryption devices, and so on.

### Data at Rest

Data at rest is data that is in permanent storage, such as data that resides on a system’s hard drive. It is data that is not being actively transmitted or received, nor is it actively being processed by the system. In this state, data is subject to unauthorized access, copying, deletion, or removal. Controls typically used to protect data while at rest include access controls such as permissions, strong encryption, and strong authentication.

### Data in Use

Data in use is data that is in a temporary or ephemeral state, characterized by data being actively processed by a device’s CPU and residing in volatile or temporary memory, such as RAM for example. During this state of being in use, data is transferred across the system bus to interact with various software and hardware components, including the CPU and memory, as well as the applications that use the data. Data in this state is destined to be read, transformed or modified, and returned back to storage.

This data state has been a traditional weakness in data and system security, in that data cannot always be fully protected by controls such as encryption. For example, different software and hardware components may not work with selected security controls because they need direct, unrestricted access to data. Only recently have efforts been made to protect data while it is being actively processed, and typically the controls that are used to protect it are now included in system hardware and software components. Advances in hardware and software have facilitated implementation of controls such as encrypting data between the storage device and the CPU on the system bus, memory protection, process isolation, and other security measures.

![Images](exam.jpg)

**EXAM TIP** Data exists in three recognized “states”: at rest (in storage), in transit (being transmitted), and in use (being actively accessed and processed in a device’s CPU and RAM).

## Control Standards Selection

Selecting controls to protect information and other assets is not an arbitrary decision. Organizations use control standards such as the ISO/IEC 27000 series, the Center for Internet Security (CIS) Critical Security Controls (CIS Controls), or the National Institute of Standards and Technology (NIST) security controls (NIST SP 800-53, Revision 5, Security and Privacy Controls for Information Systems and Organizations) based upon several factors, including the data type (e.g., financial data, healthcare data, personal data, etc.), the level of protection needed (based on the sensitivity and criticality of the data), and, most importantly, compliance with governance. Very often, governance is the deciding factor, since some sensitive data types, such as credit card information, must be protected according to a specific control set.

Beyond governance, an organization may choose control standards because of the industry they are involved in or, data protection needs, or its management culture. For example, defense contractors providing services to the U.S Department of Defense typically follow the NIST controls by default because the U.S. federal government requires contractors to comply with those controls.

## Scoping and Tailoring Data Security Controls

Regardless of the control standard that an organization chooses to protect its sensitive data, there are several factors that go into determining which controls the organization uses, and to what depth the organization implements the controls to protect its information. Controls are not simply implemented in a “one-size-fits-all” fashion; the controls selected, as well as their level of implementation, can be scoped and tailored appropriately to the organization’s information protection requirements.

Considerations in scoping and tailoring information security controls include factors we discussed in Objective 1.10 when we talked about risk management, including the criticality and sensitivity of the data. The more critical or sensitive the data, the more stringent the controls that must be put into place to protect it. Another issue is the overall value of the data or asset to the organization. The organization conducts a cost/benefit analysis to determine if the value of the asset to the organization is far less than the cost to implement and maintain a control to protect it.

Governance also figures into this scoping and tailoring effort. Some laws and regulations require a specific level of control implementation, in addition to the basic standard they impose. For example, financial regulations require that personal financial information be encrypted, using a specific encryption strength or algorithm.

In any event, selecting controls and tailoring them the right way to protect data in critical assets at the level the organization requires is an exercise in risk management, as we discussed in Objective 1.10.

## Data Protection Methods

This exam study guide covers a variety of data protection methods, but exam objective 2.6 identifies three specific methods that you should be familiar with for the exam, as described in this section. For this objective we will focus on digital rights management (DRM), data loss prevention (DLP), and cloud access security broker (CASB).

### Digital Rights Management

Digital rights management (DRM) refers to various technologies that help to restrict access to data so that it cannot be copied or modified by an unauthorized user. DRM most often is implemented to protect copyrighted material, such as music and movies, but it is also used to protect proprietary or sensitive information that an organization produces, such as trade secrets. DRM is regularly implemented in software, and there are some hardware-enabled DRM solutions, such as DVD and Blu-ray players, that won’t play copied or unencrypted discs. Software implementations include protections like watermarking, file or software encryption, licensing limitations, and so on. A popular form of DRM is steganography, which involves concealment of embedded information in computer files. Steganography can be used in a malicious way to hide malware in otherwise innocuous-looking files, but in the DRM arena, it is used to insert digital watermarking into files to protect intellectual property.

### Data Loss Prevention
