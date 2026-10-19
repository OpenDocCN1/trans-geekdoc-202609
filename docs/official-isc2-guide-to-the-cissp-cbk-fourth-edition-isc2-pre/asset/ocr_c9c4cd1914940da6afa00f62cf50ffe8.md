# Cryptography

Cryptographic techniques protect information by transforming the data through encryption schemes. They are used to protect the confidentiality and integrity of information. Most cryptographic techniques are used in telecommunications systems; however, because of the increase in distributed systems, they are becoming increasingly used in operating systems. Encryption algorithms can be used to encrypt specific files located within the operating system. For example, database files that contain user information, such as group rights, are encrypted using one-way hashing algorithms to ensure a higher protection of the data.

# Password Protection Techniques

Operating system and application software use passwords as a convenient mechanism to authenticate users. Typically, operating systems use passwords to authenticate the user and establish access controls for resources, including the system, files, or applications. Password protections offered by the operating system include controls on how the password is selected and how complex the password is, password time limits, and password length.

Password files stored within a computer system must be secured by the protection mechanisms of the operating system. Because password files are prone to unauthorized access, the most common solution is to encrypt password files using one-way encryption algorithms (hashing). These, however, are very susceptible to a dictionary attack if the passwords chosen appear in any dictionary. Another feature offered by an operating system for password security involves an overstrike or password-masking feature. This prevents others from reading the typed password through shoulder surfing.

# Inadequate Granularity of Controls

If there is not enough granularity of security, users may be able to gain more access permission than needed. If the user is unable to access object A, but the user has access to a program that can access object A, then the security mechanisms could be bypassed. If the security controls are granular enough to address both program and user, then the disclosure may be prevented. Inadequate granularity of controls can be addressed by properly implementing the concept of least privilege, setting reasonable limits on the user. Also, the separation of duties and functions should be covered. Programmers should never be system administrators or users of the application. Grant users only those permissions necessary to do their job.

Users should have no access to server rooms or legacy programs; programmers and