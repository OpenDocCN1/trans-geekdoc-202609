
# 63. D
Administrative access controls are procedures and the policies from which they derive. They are based on regulations, requirements, and the organization’s own policies. Corrective access controls return an environment to its original status after an issue, while logical controls are technical access controls that rely on hardware or software to protect systems and data. Compensating controls are used in addition to or as an alternative to other controls.

# 64. A
When clients perform a client service authorization, they send a TGT and the ID of the requested service to the TGS, and the TGS responds with a client-to-server ticket and session key back to the client if the request is validated. An AS is an authentication server, and the SS is a service server, neither of which can be sent.

# 65. C
In a mandatory access control system, all subjects and objects have a label. Compartments may or may not be used, but there is not a specific requirement for either subjects or objects to be compartmentalized. The specific labels of Confidential, Secret, and Top Secret are not required by MAC.

# 66. D
Passwords are never stored for web applications in a well-designed environment. Instead, salted hashes are stored and compared to passwords after they are salted and hashed. If the hashes match, the user is authenticated.

# 67. C
When a third-party site integrates via OAuth 2.0, authentication is handled by the service provider’s servers. In this case, Google is acting as the service provider for user authentication. Authentication for local users who create their own accounts would occur in the e-commerce application (or a related server), but that is not the question that is asked here.

# 68. B
The anti-forgery state token exchanged during OAuth sessions is intended to prevent cross-site request forgery. This makes sure that the unique session token with the authentication response from Google’s OAuth service is available to verify that the user, not an attacker, is making a request. XSS attacks focus on scripting and would have script tags involved, SQL injection would have SQL code included, and XACML is the eXtensible Access Control Markup Language, not a type of attack.

# 69. A
Knowledge-based authentication relies on preset questions such as “What is your pet’s name?” and the answers. It can be susceptible to attacks because of the availability of the answers on social media or other sites. Dynamic knowledge-based authentication relies on facts or data that the user already knows that can be used to create questions they can answer on an as-needed basis (for example, a previous address, or a school they attended).

Out-of-band identity proofing relies on an alternate channel like a phone call or text message. Finally, Type 3 authentication factors are biometric, or “something you are,” rather than knowledge based.

# 70. C
An access control matrix is a table that lists objects, subjects, and their privileges. Access control lists focus on objects and which subjects can access them. Capability tables list subjects and what objects they can access. Subject/object rights management systems are not based on an access control model.

# 71. C
Self-service password reset tools typically have a significant impact on the number of password reset contacts that a help desk has. Two-factor and biometric authentication both add additional complexity and may actually increase the number of contacts. Passphrases can be easier to remember than traditional complex passwords and may decrease calls, but they don’t have the same impact that a self-service system does.

# 72. C
RADIUS supports TLS over TCP. RADIUS does not have a supported TLS mode over UDP. AES pre-shared symmetric ciphers are not a supported solution and would be very difficult to both implement and maintain in a large environment, and the built-in encryption in RADIUS only protects passwords.

# 73. B
OAuth provides the ability to access resources from another service and would meet Jim’s needs. OpenID would allow him to use an account from another service with his application, and Kerberos and LDAP are used more frequently for in-house services.

# 74. B
Since physical access to the workstations is part of the problem, setting application time-outs and password-protected screensavers with relatively short inactivity time-outs can help prevent unauthorized access. Using session IDs for all applications and verifying system IP addresses would be helpful for online attacks against applications.

# 75. The security controls match with the categories as follows:
1. Password: B. Technical.
2. Account reviews: A. Administrative.
3. Badge readers: C. Physical.
4. MFA: B. Technical.
5. IDP: B. Technical.

* Passwords, multifactor authentication (MFA) techniques, and intrusion prevention systems (IPS) are all examples of technical controls. Account reviews are an administrative control, while using badges to control access is a physical control.

# 76. A
Verifying information that an individual should know about themselves using third-party factual information (a Type 1 authentication factor) is sometimes known as dynamic knowledge-based authentication and is a type of identity proofing. Out-of-band identity proofing would use another means of contacting the user, like a text message or phone call, and password verification requires a password.

# 77. C
The US government’s Common Access Card is a smart card. The US government also issues PIV cards, or personal identity verification cards.

# 78. C
OpenID Connect is a RESTful, JSON-based authentication protocol that, when paired with OAuth, can provide identity verification and basic profile information. SAML is the Security Assertion Markup Language, Shibboleth is a federated identity solution designed to allow web-based SSO, and Higgins is an open-source project designed to provide users with control over the release of their identity information.

# 79. C
In a mandatory access control system, classifications do not have to include rights to lower levels. This means that the only label we can be sure Jim has rights to is Secret. Despite that it is unclassified, Unclassified data remains a different label, and Jim may not be authorized to access it.

# 80. B
Time-based controls are an example of context-dependent controls. A constrained interface would limit what Susan was able to do in an application or system interface, while content-dependent control would limit her access to content based on her role or rights. Least privilege is used to ensure that subjects only receive the rights they need to perform their role.

# 81. The security controls match with the categories as follows:
1. Password: B. Something you know.
2. ID card: A. Something you have.
3. Retinal scan: C. Something you are.
4. Smartphone token: A. Something you have.
5. Fingerprint analysis: C. Something you are.

# 82. B
Policy is a subset of the administrative layer of access controls. Administrative, technical, and physical access controls all play an important role in security.

# 83. C
Synchronous soft tokens, such as Google Authenticator, use a time-based algorithm that generates a constantly changing series of codes. Asynchronous tokens typically require a challenge to be entered on the token to allow it to calculate a response, which the server compares to the response it expects. Smartcards typically present a certificate but may have other token capabilities built in. Static tokens are physical devices that can contain credentials and include smart cards and memory cards.
