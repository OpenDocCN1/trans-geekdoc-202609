
# Authentication

Authentication is another key goal of cryptography. First, `authentication` is associated with digital signatures. Authentication provides a way to ensure that any message is from who we believe it's from. In its basic form, authentication is used to determine identity. It is also part of the identification and authentication process.

# Integrity

Integrity is another cryptographic goal. Integrity is important while data is in transmission and in storage. `Integrity` means that information remains unaltered. Imagine the situation of needing to download a patch. Although the patch is available on the developer's site, you also have a copy on DVD that was given to you by a colleague. Is the version on the DVD the same as the one on the developer's website? Integrity verification programs that perform hashing such as `MD5` or `SHA` can help you determine this.

# Non-repudiation

`Non-repudiation` is assurance that an entity in a communication cannot deny authenticity. It is proof of the veracity of a claim. Non-repudiation means that a sender of data receives proof of delivery and the recipient is assured of the sender's identity. Neither party should be able to deny having sent or received the data at a later date. This can be achieved with digital signatures. A digital signature provides authenticity, integrity, and non-repudiation. In the days of face-to-face transactions, non-repudiation was not as hard to prove. Today, the Internet makes many transactions faceless. We may never see the people we deal with; therefore, non-repudiation becomes all the more critical. Non-repudiation is achieved through digital signatures, digital certificates, and message authentication codes (`MACs`).

# Cryptographic System Design Considerations

When implementing a cryptographic system there has to be consideration of strength versus performance versus feasibility to implement versus interoperability. Stronger systems typically require more process power and longer encryption/decryption times. Basically, you must consider how strong an encryption process should be. The strength of a cryptosystem relies on the strength of an algorithm and the complexity of the key generation process. The strength of the encryption mechanism also rests on the size and complexity of the key. If the cryptosystem uses a weak key generation process, then the entire process is weak. The key size goes a long way in determining the strength of the cryptosystem.

The designer of a cryptographic system must also understand the implications of cryptographic methods and design. As an example, Caesar might have thought his system of encryption was quite strong, but it would be seen as relatively insecure today. You need a sufficiently sized key to deter brute-force and other attacks. In the world of cryptography, key lengths are defined by the number of binary bits. So a 64-bit key has a keyspace of 2 to the power of 64, or 18,446,744,073,709,551,616.

# Cryptographic Terms

As a security professional, you need to understand basic cryptographic terms. You will encounter these terms when examining a vendor's security solution, discussing security controls with colleagues, and implementing a security solution. Here are some basic cryptographic terms:

1.  **Plain Text** Clear text that is readable.
2.  **Cipher Text** Encrypted text that is unreadable.
3.  **Encryption** Transforming data into an unreadable format. For example, using Caesar's cipher to encrypt the word `cat` would result in `fdw`. Encryption here has moved each character forward by three letters.
4.  **Cryptanalysis** The act of obtaining plain text from cipher text without a cryptographic key. It is used by governments, the military, enterprises, ethical hackers, and malicious hackers to find weaknesses and crack cryptographic systems.
5.  **Digital Signature** A hash value that has been encrypted with the private key of the sender. It is used for authentication and integrity.
6.  **Chain of Trust** The relationship between subordinate certificate authorities. The concept of chain of trust is critical in the world of public key infrastructure as it provides a means to pass trust from one entity to another. It allows the delegation of certificate duties to a subordinate certificate authority.
7.  **Root of Trust** Root of trust can be described as the concept of trust in a system, software, or data. It is the most common form of attestation and provides a basic set of functions that are always trusted by the operating system. `Attestation` means that you are validating something as true. A root of trust can be designed as hardware based, software based, or hybrid. The Trusted Platform Module (`TPM`) is one of the most common.

Think of root of trust as something that has been deemed trustworthy. As an example, if you are asked to serve on the jury of a court case, the lawyers should be seen as trustworthy. That's because the court trusts that the lawyers are licensed to practice law in the state and that a client-to-lawyer relationship has been established by the legal system, and because the court uses a well-defined procedural process for evidence to be admitted. Although computer systems don't need lawyers, let's hope, they do need trust, and that is the role that `TPM` plays. `TPM` has a root of trust that is defined by the endorsement key (`EK`) pair. It is a unique `RSA` key found within all `TPM` devices.

# Cryptographic System Classifications

Cryptographic systems can be broadly classified into symmetric, asymmetric, and hashing:

1.  **Symmetric Cryptography** This type uses a single private key.
2.  **Asymmetric Cryptography** This type uses two keys: a public key known to everyone and a private key that only the recipient of messages uses.

    Although both concepts are discussed in more detail later in the chapter, at this point it's important to understand that both symmetric and asymmetric cryptography make use of a key. The key is input into the encryption algorithm as data on which to perform mathematical operations such as permutation, substitution, or binary math.
3.  **Hash** A hash is a defined mathematical procedure or function that converts a large amount of data into a fixed small string of data or integer. The output of a hash is known as a hash value, hash code, hash sum, checksum, fingerprint, or message digest.

# Additional Cryptographic Terms

Here are some other terms that you will need to know:

1.  **Algorithm** An `algorithm` is a set of rules or ordered steps used to encrypt and decrypt data. The algorithm is a set of instructions used with the cryptographic key to encrypt plain text data. Plain text data encrypted with different keys or dissimilar algorithms will produce different cipher text.
2.  **Cipher Text** `Cipher text` is data that is scrambled and unreadable. When plain text is converted into cipher text, the transformation can be accomplished in basically two ways:
    1.  **Block Ciphers** Function by dividing the message into blocks for processing.
    2.  **Stream Ciphers** Function by dividing the message into bits for processing.
3.  **Cryptographic Key** How strong the encryption process is relies in part on the cryptographic key. The `cryptographic key`, or simply `key`, is a piece of information that controls how the cryptographic algorithm functions. It can be used to control the transformation of plain text to cipher text or cipher text to plain text. For attackers to brute-force the cryptographic system, they would need to guess the key. That is why the more values or combinations for the key, the longer it will take for an attacker to gain access to your encrypted data. The security of the system rests in the key. If the key generation process is weak, the entire system that is designed around it will also be weak. A good example of this can be seen with Wired Equivalency Privacy (`WEP`), whose use of `RC4` and weak key generation led to many of the attacks against this wireless protection system.
