
![](img/922567202a944c5e8d3ba0168d2ad3a5_237_0.png)

> **EXAM TIP** Confidentiality can be achieved through encryption, access control lists, or data hiding. Encryption is the strongest form, access control scales well, and data hiding is the least secure.

A last method of providing confidentiality is through a process such as steganography, a form of data hiding. This is not the preferred method, as it has been known for a long time that security via obscurity is not a strong method of protection.

## Integrity

Integrity is better known as *message integrity*, and it is a crucial component of message security. When a message is sent, both the sender and recipient need to know that the message was not altered in transmission. This is especially important for legal contracts—recipients need to know that the contracts have not been altered. Signers also need a way to validate that a contract they sign will not be altered in the future.

Integrity is provided with one-way hash functions and digital signatures. The hash functions compute the message digests, and this guarantees the integrity of the message by allowing easy testing to determine whether any part of the message has been changed. The message now has a computed function (the hash value) to tell the users to resend the message if it was intercepted and interfered with.

This hash value is combined with asymmetric cryptography by taking the message’s hash value and encrypting it with the user’s private key. This enables anyone with the user’s public key to decrypt the hash and compare it to the locally computed hash, which not only ensures the integrity of the message, but also positively identifies the sender.

![](img/922567202a944c5e8d3ba0168d2ad3a5_237_1.png)

> **EXAM TIP** Integrity can be verified through hashing. The employment of hash functions in operations such as digital signatures enables verification of integrity and non-repudiation.

Using hash values to verify integrity is commonly done behind the scenes. When a user needs to use an asymmetric key, they use a certificate that holds the key and supporting information. Using hash values on the certificate, the validity of the information can be verified. Using the signing keys on the certificate, the veracity of the key can be determined, acting as a form of non-repudiation.

## Availability

Availability is the third leg of the CIA triad, and refers to the property of system access being available to authorized users when they are authorized to have access. For some systems, availability can be a significant operational concern. This has led to the development of fault-tolerant and redundant systems to ensure the continuous availability of critical systems. A key operational process to ensure availability of systems is the change configuration board. A properly functioning change configuration board can ensure that systems have maximum availability, even when they need to be taken down for patching. In a system of multiple identical servers, only a portion is changed at any given time, allowing the efficacy of the change to be fully tested in production before committing all machines. Provided that the changes are permitted only during slack user periods, there should be sufficient slack space to allow rolling changes while maintaining availability.

![](img/922567202a944c5e8d3ba0168d2ad3a5_238_0.png)

> EXAM TIP Availability can be achieved through fault-tolerant and redundant systems.

The use of standby systems can also improve availability in the event of disasters and the implementation of business continuity plans. Having a hot site as a standby system is the best solution, as warm and cold sites will add a period of downtime to continuous operations. In the case of extreme failover needs, as in no lost time or data, then an active-active architecture is needed. When the data centers are active-active and applications are also active-active, the result is continuous availability. An active-active system will process data on both the primary and backup systems, allowing instant failover, but with the drawback of needing bidirectional replication-capable software.

Data availability can also become an issue, especially when a significant amount of data is stored on individual machines and mobile devices. Daily data, viewed as critical by many workers, may not be backed up at the same frequency as enterprise data. If workers’ daily work has value, then the data should also receive appropriate attention in the form of backup protections.

## Safety

Safety and security are related in several ways. A secure system performs the tasks it is supposed to do and only those tasks, and these qualities are needed for safety. Safety systems come in a wide range and in various forms, but many are related to physical security issues.

### Fencing

Fencing can be used for physical isolation and protection. Fencing can be used to separate security zones, provide safe areas, and maintain traffic separation. From simple chain-link fencing to high-security fencing, each can provide a level of protection. Chain-link fences can provide for simple crowd control, but offer little in terms of blocking a determined adversary. High-security fencing, such as palisade fencing, offers significant levels of anti-climb protection, and delay factors for intrusions.

### Lighting

Lighting is essential for several reasons. It can provide illumination necessary for surveillance systems, such as CCTV systems. It can also provide needed guidance for people during evacuation drills. Appropriate levels of lighting in work areas is common, but it is equally important to provide adequate lighting in other areas such as egress venues and stairwells.

### Locks

Locks provide a means of controlling access, acting as physical manifestations of an access control list. Because locks are physical devices that can be vulnerable to tampering, for high-security locks, measures need to be taken to prevent bypassing them. Many high-security lock manufacturers will patent and tightly control key blanks. This will make blanks unavailable to unauthorized persons and eliminate bump keys. Physical keyways can also be of more complex designs than ordinary key locks, making physical manipulation (lock picking) extremely difficult.

### CCTV

Closed-circuit TV systems can provide surveillance and monitoring over large areas and allow monitoring from a central or remote location. These systems can provide the ability to coordinate many efforts in emergency conditions. CCTV can be combined with facial recognition technology with the potential to track individuals as they pass cameras connected to the system.

### Escape Routes

Escape routes are methods of egress planned into buildings. Typically required by building codes, escape routes can be used to navigate egress to a safe place in the event of a hazardous condition. Egress may require transiting secured doors, and in the event of emergencies, a fail-safe condition can be employed to open doors for people evacuating.

### Escape Plans

Escape plans can be devised to enable employees to safely evacuate buildings, structures, and complex systems such as industrial plants. Preparation for emergencies that includes the development, posting, and training of escape plans can result in saving lives if the plans are ever needed in a real emergency. Escape routes, plans, and drills can work together to achieve a prepared workforce for the task of emergency egress.

### Drills

Drills are used to practice specific behaviors so that when an emergency occurs, people will know how to act without additional training or instruction. In the case of a situation where increased physical security measures are needed, doors and windows, with their locks, can be employed. A lockdown drill can engage numerous people to achieve this behavior.

### Testing Controls

Controls are not foolproof. The proper employment of them is generally a complex event and one that requires extensive planning. Once they are deployed, security controls
