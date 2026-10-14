
## 23
**A.** Logging systems can provide accountability for identity systems by tracking the actions, changes, and other activities a user or account performs.

## 24
**B.** As an employee’s role changes, they often experience privilege creep, which is the accumulation of old rights and roles. Account review is the process of reviewing accounts and ensuring that their rights match their owners’ role and job requirements. Account revocation removes accounts, while re-provisioning might occur if an employee was terminated and returned or took a leave of absence and returned.

## 25
**A.** Biba uses a lattice to control access and is a form of the mandatory access control (MAC) model. It does not use rules, roles, or attributes, nor does it allow user discretion. Users can create content at their level or lower but cannot decide who gets access, levels are not roles, and attributes are not used to make decisions on access control.

## 26
**C.** RADIUS is an AAA protocol used to provide authentication and authorization; it’s often used for modems, wireless networks, and network devices. It uses network access servers to send access requests to central RADIUS servers. Kerberos is a ticket-based authentication protocol; OAuth is an open standard for authentication allowing the use of credentials from one site on third-party sites; and EAP is the Extensible Authentication Protocol, an authentication framework often used for wireless networks.

## 27
**A.** Resource-based access controls match permissions to resources like a storage volume. Resource-based access controls are becoming increasingly common in cloud-based infrastructure as a service environments. The lack of roles, rules, or a classification system indicate that role-based, rule-based, and mandatory access controls are not in use here.

## 28
**C.** By default, RADIUS uses UDP and only encrypts passwords. RADIUS supports TCP and TLS, but this is not a default setting.

## 29
**D.** A key distribution center (KDC) provides authentication services, and ticket-granting tickets (TGTs) provide proof that a subject has authenticated and can request tickets to access objects. Authentication services (ASs) are part of the KDC. There is no TS in a Kerberos infrastructure.

## 30
**D.** Authorization provides a user with capabilities or rights. Roles and group management are both methods that could be used to match users with rights. Logins are used to validate a user.

## 31
**C.** Privilege creep occurs when users retain from roles they held previously rights they do not need to accomplish their current job. Unauthorized access occurs when an unauthorized user accesses files. `Excessive provisioning` is not a term used to describe permissions issues, and account review would help find issues like this.

## 32
**B.** Phishing is not an attack against an access control mechanism. While phishing can result in stolen credentials, the attack itself is not against the control system and is instead against the person being phished. Dictionary attacks and man-in-the-middle attacks both target access control systems.

## 33
**B.** Race conditions occur when two or more processes need to access the same resource in the right order. If an attacker can disrupt this order, they may be able to affect the normal operations of the system and gain unauthorized access or improper rights. Collisions occur when two different files produce the same result from a hashing operation, out-of-order execution is a CPU architecture feature that allows the use of otherwise unused cycles, and `determinism` is a philosophical term rather than something you should see on the CISSP exam!

## 34
**C.** Mandatory access controls use a lattice to describe how classification labels relate to each other. In this image, classification levels are set for each of the labels shown. A discretionary access control (DAC) system would show how the owner of the objects allows access. RBAC could be either rule- or role-based access control and would use either system-wide rules or roles. Task-based access control (TBAC) would list tasks for users.

## 35
**C.** LDAP distinguished names are made up of zero or more comma-separated components known as relative distinguished names. `cn=ben,ou=example;` ends with a semicolon and is not a valid DN. It is possible to have additional values in the same RDN by using a plus sign between then.

## 36
**B.** The process of a subject claiming or professing an identity is known as identification. Authorization verifies the identity of a subject by checking a factor like a password. Logins typically include both identification and authorization, and token presentation is a type of authentication.

## 37
**D.** Dogs, guards, and fences are all examples of physical controls. While dogs and guards might detect a problem, fences cannot, so they are not all examples of detective controls. None of these controls would help repair or restore functionality after an issue, and thus they are not recovery controls, nor are they administrative controls that involve policy or procedures, although the guards might refer to them when performing their duties.

## 38
**B.** Password complexity is driven by length, and a longer password will be more effective against brute-force attacks than a shorter password. Each character of additional length increases the difficulty by the size of the potential character set (for example, a single lowercase character makes the passwords 26 times more difficult to crack). While each of the other settings is useful for a strong password policy, they won’t have the same impact on brute-force attacks.

## 39
**A.** The stored sample of a biometric factor is called a reference profile or a reference template. None of the other answers is a common term used for biometric systems.

## 40
**A.** Organizations that have very strict security requirements that don’t have a tolerance for false acceptance want to lower the false acceptance rate, or FAR, to be as near to zero as possible. That often means that the false rejection rate, or FRR, increases. Different biometric technologies or a better registration method can help improve biometric performance, but false rejections due to data quality are not typically a concern with modern biometric systems. In this case, knowing the crossover error rate, or CER, or having a very high CER doesn’t help the decision.

## 41
**B.** The complexity of brute-forcing a password increases based on both the number of potential characters and the number of letters added. In this case, there are 26 lowercase letters, 26 uppercase letters, and 10 possible digits. That creates 62 possibilities. Since we added only a single letter of length, we get 62^1, or 62 possibilities, and thus, the new passwords would be 62 times harder to brute-force on average.

## 42
**B.** Biometric systems can face major usability challenges if the time to enroll is long (over a couple of minutes) and if the speed at which the biometric system is able to scan and accept or reject the user is too slow. FAR and FRR may be important in the design decisions made by administrators or designers, but they aren’t typically visible to users. CER and ERR are the same and are the point where FAR and FRR meet. Reference profile requirements are a system requirement, not a user requirement.

## 43
**C.** TLS provides message confidentiality and integrity, which can prevent eavesdropping. When paired with digital signatures, which provide integrity and authentication, forged assertions can also be defeated. SAML does not have a security mode and relies on TLS and digital signatures to ensure security if needed. Message hashing without a signature would help prevent modification of the message but won’t necessarily provide authentication.
