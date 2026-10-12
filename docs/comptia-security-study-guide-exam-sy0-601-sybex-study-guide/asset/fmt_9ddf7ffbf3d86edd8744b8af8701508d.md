
## Chapter 8: Identity and Access Management

### Questions 10-20

**10. B.** In an asymmetric encryption algorithm, each employee needs only two keys: a public key and a private key. Adding a new user to the system requires the addition of these two keys for that user, regardless of how many other users exist.

**11. D.** Extended validation (EV) certificates provide the highest available level of assurance. The CA issuing an EV certificate certifies that they have verified the identity and authenticity of the certificate subject.

**12. C.** Wildcard certificates protect the listed domain as well as all first-level subdomains. `dev.www.mydomain.com` is a second-level subdomain of `mydomain.com` and would not be covered by this certificate.

**13. A.** Root CAs are highly protected and not normally used for certificate issuance. A root CA is usually run as an offline CA that delegates authority to intermediate CAs that run as online CAs.

**14. C.** The PFX format is most closely associated with Windows systems that store certificates in binary format, whereas the P7B format is used for Windows systems storing files in text format.

**15. A.** Hardware security modules (HSMs) provide an effective way to manage encryption keys. These hardware devices store and manage encryption keys in a secure manner that prevents humans from ever needing to work directly with the keys.

**16. C.** A downgrade attack is sometimes used against secure communications such as TLS in an attempt to get the user or system to inadvertently shift to less secure cryptographic modes. The idea is to trick the user into shifting to a less secure version of the protocol, one that might be easier to break.

**17. C.** When encrypting a message using an asymmetric encryption algorithm, the person performing the encryption does so using the recipient's public key.

**18. D.** In an asymmetric encryption algorithm, the recipient of a message uses their own private key to decrypt messages that they receive.

**19. B.** The sender of a message may digitally sign the message by encrypting a message digest with the sender's own private key.

**20. A.** The recipient of a digitally signed message may verify the digital signature by decrypting it with the public key of the individual who signed the message.

### Questions 1-18

**1. D.** Angela's organization is acting as an identity provider (IdP). Other members of the federation may act as a service provider or relying party when they allow her users to access their services. Authentication provider is not a named role in typical federation activities.

**2. A.** Password complexity requirements do not prevent sharing of complex passwords, making it the least effective option from the list. Biometric authentication measures will require the enrolled user to be there, although in some cases such as fingerprint systems, multiple users could each enroll a valid fingerprint for a single account. Both types of one-time passwords could be shared but make it harder and less convenient to share accounts.

**3. B.** Most cloud services provide identity and authorization tools for their services. Most, although not all, allow customers to set some or even many of the account policies they will use, and most major vendors support some form of multifactor capability.

**4. A.** Of all the listed options, only RADIUS is an authentication, authorization, and accounting service.

**5. B.** SMS messages are not secure and could be accessed by cloning a SIM card or redirecting VoIP traffic, among other possible threat models. Both HOTP and TOTP tokens and applications as well as biometric factors are generally considered more secure than an SMS-based factor.

**6. B.** Geofencing sets a geographic boundary that can be used as part of a ruleset. In this case, Samantha should set the ruleset to prevent devices from allowing users to use them when they are outside of the geofenced area. Time-of-day limitations and time-based logins are both related account policies that are used to ensure that users cannot log in when they shouldn't be at work. This can prevent compromised credential reuse and insider threat abuses during off-hours. Finally, impossible travel time is a type of geographic login data usage that maps when logins occur and compares them to the distance between them. If the time is impossible, with a login in China 5 minutes after one in the United States, for example, the login may be reported and stopped.

**7. B.** Picture password asks users to click on specific, self-defined parts of a picture. This means that clicking on those points is something you can do. Somewhere you are involves a location, something you exhibit is typical of personality traits, and someone you know would involve a third party, which can be useful for verification when someone can't otherwise prove their identity!

**8. B.** Hardware security modules (HSMs) are used to create, securely store, and manage digital signatures, cryptographic key pairs, and other cryptographic functions. They are not used for biometric enrollment data, to enable federation, or to generate one-time passwords.

**9. C.** Role-based access control (RBAC) sets permissions based on an individual's role, which is typically associated with their job. Attribute-based access control (ABAC) is typically matched to attributes other than the job role. Discretionary access control (DAC) and mandatory access control (MAC) are commonly implemented at the operating system level.

**10. D.** Fingerprint scanners are found on many mobile devices and laptops, making it one of the most broadly deployed biometric technologies. Facial recognition is also broadly deployed, but it is not offered as an option.

**11. B.** LDAP, the Lightweight Directory Access Protocol, is an open industry standard for directory services. LDAP is not itself a federation or an attestation service, nor does it provide biometric authentication services.

**12. A.** PINs and passwords are both examples of something you know. Something you set is not a type of factor. Biometric factors are an example of something you are, and a physical USB token would be a common example of something you have.

**13. C.** A low crossover error rate will ensure that there's a low false rejection rate and a low false acceptance rate. The other options each have a high element, which isn't desirable.

**14. D.** Account lockout policies lock out an account after a specific number of failed login attempts. This type of response helps to prevent brute-force attacks by stopping them from using repeated attempts until they can successfully log in.

**15. B.** Account policies include password complexity requirements; password history to prevent password reuse; and the time of day, geolocation, and similar settings that control elements of an account. Account audits check settings and account status. Access policies determine who can use systems or devices and other related items. Credential attributes is a made-up phrase for this question and the phrase does not appear in the Security+ exam outline.

**16. D.** OAuth is a protocol designed to allow users to grant third-party sites access to their information without providing that site with their password. It is typically used by OpenID identity providers to provide both authentication and authorization. Neither Kerberos nor RADIUS fits these requirements.

**17. C.** Google Authenticator implements time-based one-time passwords, with continuously generated codes provided to the user that expire and are refreshed on an ongoing basis.

**18. D.** Inadvertent exposure of private keys via upload to a service like GitHub; poor handling of the private key in user directories; use of weak or reused passwords and passphrases; and key sprawl, in which keys are used broadly across an organization, are all common concerns. Weak encryption is not a typical concern with the use of SSH, since it implements modern strong encryption.
