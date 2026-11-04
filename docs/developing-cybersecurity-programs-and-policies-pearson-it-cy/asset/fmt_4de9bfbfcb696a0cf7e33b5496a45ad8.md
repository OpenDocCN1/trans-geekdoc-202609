
Another example is the General Data Protection Regulation (GDPR) by the European Commission. One of the GDPR’s main goals is to strengthen and unify data protection for individuals within the European Union (EU), while addressing the export of personal data outside the EU. In short, the primary objective of the GDPR is to give citizens back control of their personal data.

## What Is a “Key”?

A `key` is a secret code that is used by a cryptographic algorithm. It provides the instructions that result in the functional output. Cryptographic algorithms themselves are generally known. It is the secrecy of the key that provides for security. The number of possible keys that can be used with an algorithm is known as the `keyspace`, which is a large set of random values that the algorithm chooses from when it needs to make a key. The larger the keyspace, the more possibilities for different keys. For example, if an algorithm uses a key that is a string of 10 bits, then its key space is the set of all binary strings of length 10, which results in a keyspace size of `2^(10)` (or 1,024); a 40-bit key results in `2^(40)` possible values; and a 256-bit key results in `2^(256)` possible values. Longer keys are harder to break, but require more computation and processing power. Two factors must be taken into consideration when deciding upon the key length: the desired level of protection and the amount of resources available.

### Symmetric Keys

A `symmetric key` algorithm uses a single secret key, which must be shared in advance and be kept private by both the sender and the receiver. Symmetric keys are often referred to as `shared keys`. Because the keys are shared, symmetric algorithms cannot be used to provide nonrepudiation or authenticity. One of the most popular symmetric algorithms of recent years is `AES`. The strength of symmetric keys is that they are computationally efficient. The weakness is that key management is inherently insecure and that it is not scalable, because a unique key set must be used to protect the secrecy of the key.

### Asymmetric Keys

`Asymmetric key` cryptography, also as known as `public key` cryptography, uses two different but mathematically related keys known as `public` and `private` keys. Think of public and private keys as two keys to the same lock—one used to lock and the other to unlock. The private key never leaves the owner’s possession. The public key is given out freely. The public key is used to encrypt plain text or to verify a digital signature, whereas the private key is used to decrypt cipher text or to create a digital signature. Asymmetric key technologies allow for efficient, scalable, and secure key distribution; however, they are computationally resource-intensive.

## What Is PKI?

`Public key infrastructure (PKI)` is the framework and services used to create, distribute, manage, and revoke public keys. PKI is made up of multiple components, including a certification authority (CA), a registration authority (RA), client nodes, and the digital certificate itself:
* The `certification authority (CA)` issues and maintains digital certificates.
* The `registration authority (RA)` performs the administrative functions, including verifying the identity of users and organizations requesting a digital certificate, renewing certificates, and revoking certificates.
* `Client nodes` are interfaces for users, devices, and applications to access PKI functions, including the requesting of certificates and other keying material. They may include cryptographic modules, software, and procedures necessary to provide user access to the PKI.
* A `digital certificate` is used to associate a public key with an identity. Certificates include the certificate holder’s public key, serial number of the certificate, certificate holder’s distinguished name, certificate validity period, unique name of the certificate issuer, digital signature of the issuer, and signature algorithm identifier.

### FYI: Viewing a Digital Certificate

If you are using an Apple Mac operating system, the certificates are stored in the Keychain Access utility. If you are using a Microsoft Windows operating system, digital certificates are stored in the Internet Browser application. [Figure 10-3](#ch10.xhtml#ch10fig03) shows the digital certificate for [twitter.com](http://twitter.com), as an example.

![](graphics/10fig03.jpg)

## Why Protect Cryptographic Keys?

As mentioned earlier in the chapter, the usefulness of a cryptographic system is entirely dependent on the secrecy and management of the key. This is so important that NIST has published a three-part document devoted to cryptographic key management guidance. SP 800-67: Recommendations for Key Management, Part 1: General (Revision 3) provides general guidance and best practices for the management of cryptographic keying material. Part 2: Best Practices for Key Management Organization provides guidance on policy and security planning requirements for U.S. government agencies. Part 3: Application Specific Key Management Guidance provides guidance when using the cryptographic features of current systems. In the Overview of Part 1, NIST describes the importance of key management as follows: “The proper management of cryptographic keys is essential to the effective use of cryptography for security. Keys are analogous to the combination of a safe. If a safe combination is known to an adversary, the strongest safe provides no security against penetration. Similarly, poor key management may easily compromise strong algorithms. Ultimately, the security of information protected by cryptography directly depends on the strength of the keys, the effectiveness of mechanisms and protocols associated with keys, and the protection afforded to the keys. All keys need to be protected against modification, and secret and private keys need to be protected against unauthorized disclosure. Key management provides the foundation for the secure generation, storage, distribution, use, and destruction of keys.”

Best practices for key management include the following:
* The key length should be long enough to provide the necessary level of protection.
* Keys should be transmitted and stored by secure means.
* Key values should be random, and the full spectrum of the keyspace should be used.
* The key’s lifetime should correspond with the sensitivity of the data it is protecting.
* Keys should be backed up in case of emergency. However, multiple copies of keys increase the chance of disclosure and compromise.
* Keys should be properly destroyed when their lifetime ends.
* Keys should never be presented in clear text.

Key management policy and standards should include assigned responsibility for key management, the nature of information to be protected, the classes of threats, the cryptographic protection mechanisms to be used, and the protection requirements for the key and associated processes.

## Digital Certificate Compromise

Certification Authorities (CAs) have increasingly become targets for sophisticated cyber attacks. An attacker who breaches a CA to generate and obtain fraudulent certificates can then use the fraudulent certificates to impersonate an individual or organization. In July of 2012, NIST issued an ITL bulletin titled “Preparing for and Responding to Certification Compromise and Fraudulent Certificate Issue.” The bulletin primarily focuses on guidance for Certification and Registration Authorities. The bulletin does, however, include the guidance for any organization impacted by the fraud.

The built-in defense against a fraudulently issued certificate is certificate revocation. When a rogue or fraudulent certificate is identified, the CA will issue and distribute a certificate revocation list. Alternatively, a browser may be configured to use the Online Certificate Status Protocol (OCSP) to obtain revocation status.
