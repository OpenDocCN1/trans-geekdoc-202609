
# Crypto Shredding

**Crypto shredding** is intentionally deleting an encryption key. The consequence is effectively permanently encrypting the data. In practice, this can be useful when a client wants their data "erased" or inaccessible forever. This brings up the challenge of maintaining unique keys to enable every possible such request.

But the risk is, deleting the encryption key doesn't mean the encrypted data is not available. Encrypted data doesn't stay unencrypted when attacked with enough brute force.

# Cryptographic Obfuscation

Unlike encryption that renders something entirely unreadable, **obfuscation** is the method of masking the data's value by mixing it or modifying it with nonsensical data. This scrambles the input into something too challenging to understand or recover. This is **not** the same as the poor practice of "security by obscurity." Obfuscation works best when the data is already fairly complex or not easily recovered. For instance, source code is unrecoverable with minimal obfuscation.

# Key Rotation

Knowing when to rotate keys and certificates is based on their validity period. Interestingly enough, the maximum validity period has been contested and changed in recent years. In 2022, the maximum period is 825 days, but there is growing momentum to reduce it to 398 days.

In any case, key rotation must happen within those periods to maintain valid certificates and keys. And rotation can and should happen sooner if any compromise is detected.

# Compromised Keys

The real danger of compromised keys is a malicious actor can now impersonate the intended source of the compromised certificate. The consequences of a malicious actor acting as the legitimate source can range from certified malware, decrypted communication, setting up on-path (formerly known as man-in-the-middle) attacks, forged traffic, and sniffing encrypted traffic. It's a bad thing.

# Summary

This chapter focused on cryptography, a relatively deep component of the CASP+ content. While cryptography is on the CASP+ exam, it is also one of the most powerful tools of a security professional. It offers you the ability to protect sensitive information through the use of encryption. It can also offer you the ability to verify the integrity of patches, files, and important data. In addition, cryptography makes e-commerce possible. With cryptographic solutions such as `PKI`, you can trust that a third party is who they claim to be. These are but a few of the solutions cryptography offers.

As a security professional, you need to able to communicate with others about cryptographic solutions and services. You don't have to be able to write your own cryptographic algorithms. You do need to be able to offer solutions to real problems. There is not a week that goes by without a news report that lists stolen or lost media that contained personal information. As a security professional, you may be in a position to suggest that your company use full disk encryption (`FDE`) for all laptops. You may also have the opportunity to promote `PGP` as a standard to encrypt all email being used to discuss sensitive business matters. You may even be on a team preparing to roll out a new e-commerce site and be asked to offer your opinion on `PKI`. These are the types of solutions that security professionals offer every day.

# Exam Essentials

**Be able to describe which cryptographic solution is appropriate for a given situation.** Cryptographic solutions can be broadly divided into symmetric encryption, asymmetric encryption, hybrid encryption, and hashing. Each offers specific solutions such as privacy, authentication, integrity, and nonrepudiation.

**Be able to describe the basic operation of PKI and understand advanced PKI concepts.** `PKI` allows two parties that are previously unknown to each other to communicate over an insecure public network. Such communications can then be used to exchange data securely and privately or for e-commerce. `PKI` systems make use of public and private keys. Keys are shared through a trusted certificate authority.

**Know what terms such as `wildcard` mean when applied to PKI.** A `wildcard` certificate allows the purchaser to secure an unlimited number of subdomain certificates on a domain name. The advantage is that you buy and maintain only one certificate. The drawback, however, is that you are using just one certificate and private key on multiple websites and private servers.

**Be able to describe transport encryption.** Transport encryption is one of the two modes in which `IPsec` can operate. When `IPsec` transport encryption is used, only the data portion or payload of each `IP` packet is encrypted. This leaves the `IP` header untouched and sent in the clear.

**Be able to describe a digital signature.** A digital signature is a hash value that has been encrypted with the private key of the sender. It is used for authentication and integrity.

**Be able to describe hashing.** Hashing refers to a broad category of algorithms that are useful for their ability to provide integrity and authentication. Hashing algorithms operate by taking a variable amount of data and compressing it into a fixed-length value referred to as a hash value.

**Be able to describe code signing.** Code signing is the process of digitally signing executables and scripts to confirm the software author. Code signing also guarantees that the code has not been altered or corrupted since it was signed by use of a hash.

**Know how nonrepudiation works.** Nonrepudiation is the ability to verify proof of identity. It is used to ensure that a sender of data is provided with proof of delivery and that the recipient is assured of the sender's identity.

**Be able to define certificate authority hierarchy.** Understand the relationship between the root, subordinate, and intermediate `CAs`. Understand the importance of the chain of trust.

**Be able to explain perfect forward secrecy.** Perfect forward secrecy is based on the concept that the exposure of a single key will permit an attacker access only to data protected by a single key.

**Recognize and understand PKI implementation issues.** There are several configuration problems that can arise from poorly implemented `PKI`. Recognize the errors you might encounter and how to decipher them. Remember that troubleshooting begins with verifying the simple issues first.

# Review Questions

You can find the answers in [Appendix](#b01.xhtml).

1.  You have been asked by a member of senior management to explain the importance of encryption and define what symmetric encryption offers. Which of the following offers the best explanation?

    1.  Nonrepudiation
    2.  Confidentiality
    3.  Hashing
    4.  Privacy and authentication

2.  As the security administrator for your organization, you must be aware of all types of hashing algorithms. Which fast-block algorithm was developed by Ron Rivest and offers a 128-bit output?

    1.  `Salsa20`
    2.  `3DES`
    3.  `CHACHA`
    4.  `RC5`

3.  A co-worker is concerned about the veracity of a claim because the sender of an email denies sending it. The co-worker wants a way to prove the authenticity of an email. Which would you recommend?

    1.  Hashing
    2.  Digital signature
    3.  Symmetric encryption
    4.  Asymmetric encryption

4.  A junior administrator at a sister company called to report a possible exposed private key that is used for `PKI` transactions. The administrator would like to know the easiest way to check whether the lost key has been flagged by the system. What are you going to recommend to the administrator?

    1.  Hashing
    2.  Issuance to entities
    3.  Adding to `RA`
    4.  `Wildcard` verification

5.  You've discovered that an expired certificate is being used repeatedly to gain logon privileges. To what list should the certificate have been added?

    1.  `Wildcard` verification
    2.  Expired key revocation list
