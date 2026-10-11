
# 3. Online Certificate Status Department

# 4. Certificate revocation list (CRL)

# 6. A junior administrator comes to you in a panic after seeing the cost for certificates. She would like to know if there is a way to get one certificate to cover all domains and subdomains for the organization. What solution can you offer?

1.  Wildcards
2.  Blanket certificates
3.  Distributed certificates
4.  No such solution exists

# 7. Which of the following is not an advantage of symmetric encryption?

1.  It's powerful.
2.  A small key works well for bulk encryption.
3.  It offers confidentiality.
4.  Key exchange is easy.

# 8. Most authentication systems make use of a one-way encryption process. Which of the following offers the best example of one-way encryption?

1.  Asymmetric encryption
2.  Symmetric encryption
3.  Hashing
4.  PKI

# 9. Which of the following algorithms would serve to prove the integrity of a file?

1.  RSA
2.  Diffie–Hellman
3.  SHA-256
4.  ECC

# 10. Which type of encryption offers the easiest key exchange and key management?

1.  Symmetric
2.  Asymmetric
3.  Hashing
4.  Digital signatures

# 11. SSL and TLS can best be categorized as which of the following?

1.  Symmetric encryption systems
2.  Asymmetric encryption systems
3.  Hashing systems
4.  Hybrid encryption systems

# 12. Which is the type of certificate to use for securing these example domains: `snakes.pets.com`, `budgies.pets.com`, and `chinchillas.pets.com`?

1.  Wildcard
2.  Multidomain
3.  Validation
4.  CRL

# 13. Which of the following is not a hashing algorithm?

1.  SHA-512
2.  ECDH
3.  Skipjack
4.  IDEA

# 14. A mobile user calls you from the road and informs you that he has been asked to travel to China on business. He wants suggestions for securing his hard drive. What do you recommend he use?

1.  S/MIME
2.  BitLocker
3.  Secure SMTP
4.  PKI

# 15. You were given a disk full of applications by a friend but are unsure about installing a couple of the applications on your company laptop. Is there an easy way to verify if the programs are original or if they have been tampered with?

1.  Verify with a hashing algorithm.
2.  Submit to a certificate authority.
3.  Scan with symmetric encryption.
4.  Check the programs against the CRL.

# 16. What is the correct term for when two different files are hashed and produce the same hashed output?

1.  Session key
2.  Digital signature
3.  Message digest
4.  Collision

# 17. You have been asked to suggest a simple trust system for distribution of encryption keys. Your client is a three-person company and wants a low-cost or free solution. Which of the following would you suggest?

1.  Single authority trust
2.  Hierarchical trust
3.  Spoke/hub trust
4.  Web of trust

# 18. Which of the following would properly describe a system that uses a symmetric key distributed by an asymmetric process?

1.  Digital signature
2.  Hybrid encryption
3.  HMAC
4.  Message digest

# 19. A CASP+ must understand the importance of encryption and cryptography. It is one of the key concepts used for the protection of data in transit, while being processed, or while at rest. With that in mind, 3DES ECB is an example of which of the following?

1.  Disk encryption
2.  Block encryption
3.  Port encryption
4.  Record encryption

# 20. Which of the following can be used to describe a physical security component that is used for cryptoprocessing and can be used to store digital keys securely?

1.  HSM
2.  TPM
3.  HMAC
4.  OCSP

# Chapter 7: Incident Response and Forensics

In 2021, FireEye/Mandiant CEO Kevin Mandia testified before the United States Senate Intelligence Committee as the country was in the middle of responding to the SolarWinds supply chain attack. He said, “Speed is critical to the effective disruption or mitigation of an attack by an advanced threat actor.” Many risk management solutions help with low-level security events, but having an experienced incident response and forensics team with expertise to quickly respond to an attack will increase success when dealing with a breach. This chapter discusses what a CASP+ should know about incident response and forensics.

## The Incident Response Framework

The security maturity level of an organization directly influences the type of incident response they will have. A startup might have an untested incident response plan. It takes a high level of maturity to have a seasoned 24-hour security operations center (SOC) staffed with incident responders threat hunting for attackers in their network. Unless it's ransomware openly locking down assets, many organizations are told by third parties that they are compromised, and that is not a fast enough response in today's cyber realm. Things can and will go wrong quickly, and companies have to be prepared and looking. Unfortunately, not all networks or assets are 100 percent secure. Attackers’ dwell time in a network is always changing, putting stress on analysts to detect and respond in real time. A CASP+ must be able to conduct incident response quickly and efficiently and implement documented recovery procedures as soon as an event becomes an incident.

### Event Classifications

Incident response is both an art and a science. With education and experience, the art of incident response comes with understanding and intuition. The science of incident response comes with testing data. A huge mistake that incident responders can make is making assumptions and concluding that something is true when it is actually false, as well as concluding that something is false when it is really true. A `false positive` is when personnel determine something is true when it isn't. It is often called a false alarm. A `false negative` is saying something is false when it's accurate. In [Figure 7.1](#c07.xhtml#c07-fig-0001), you see the relationship between reality and hypothetical decisions.

![FIGURE 7.1 Relationship in hypothetical decision-making](images/c07f001.png)

**FIGURE 7.1** Relationship in hypothetical decision-making

In a criminal court, it is ideal to have a `true positive` or `true negative` decision, meaning the innocent are found innocent and the guilty are found guilty. It is not ideal but preferable to have a false negative, where a criminal is found innocent, rather than a false positive convicting someone who is innocent. However, entering the courthouse, it is preferable that a metal detector indicate metal is found (false positive) than fail to find a gun when it is actually present (false negative). In this situation, a false negative is a huge security risk.

### Triage Events

In incident response, an event is something that is observed. It is unknown if it is malicious or not. Events happen hourly in most large organizations; however, many never progress into an actual incident. Events are changes that are captured in the environment. With tools configured properly, alerts can be generated to let the SOC team know that something happened. For example, an alert can be generated by a security information and event management (SIEM) tool providing real-time notification that an administrator changed their password. Administrators have a lot of control in an enterprise environment, so this is noteworthy, but not necessarily nefarious.
