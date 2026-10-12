
# High Resiliency Requirements

High resiliency requirements exist when it is extremely important that data be preserved and not accidentally destroyed during an encryption operation. In cases where resiliency is extremely important, the easiest way to address the issue is for the sender of data to retain a copy until the recipient confirms the successful receipt and decryption of the data.

## Homomorphic Encryption

Privacy concerns also introduce some specialized use cases for encryption. In particular, we sometimes have applications where we want to protect the privacy of individuals, but still want to perform calculations on their data. `Homomorphic encryption` technology allows this, encrypting data in a way that preserves the ability to perform computation on that data. When you encrypt data with a homomorphic algorithm and then perform computation on that data, you get a result that, when decrypted, matches the result you would have received if you had performed the computation on the plaintext data in the first place.

## Quantum Computing

`Quantum computing` is an emerging field that attempts to use quantum mechanics to perform computing and communication tasks. It's still mostly a theoretical field but, if it advances to the point where that theory becomes practical to implement, quantum cryptography may be able to defeat cryptographic algorithms that depend on factoring large prime numbers.

At the same time, quantum computing may be used to develop even stronger cryptographic algorithms that would be far more secure than modern approaches. We'll have to wait and see how those develop to provide us with strong quantum communications in the postquantum era.

# Summary

Cryptography is one of the most important security controls in use today and it touches almost every other area of security, ranging from networking to software development. The use of cryptography supports the goals of providing confidentiality, integrity, authentication, and nonrepudiation in a wide variety of applications.

Symmetric encryption technology uses shared secret keys to provide security for data at rest and data in motion. As long as users are able to overcome key exchange and maintenance issues, symmetric encryption is fast and efficient. Asymmetric cryptography and the public key infrastructure (`PKI`) provide a scalable way to securely communicate, particularly when the communicating parties do not have a prior relationship.

# Exam Essentials

**Understand the goals of cryptography.** The four goals of cryptography are confidentiality, integrity, authentication, and non-repudiation. Confidentiality is the use of encryption to protect sensitive information from prying eyes. Integrity is the use of cryptography to ensure that data is not maliciously or unintentionally altered. Authentication refers to uses of encryption to validate the identity of individuals. Nonrepudiation ensures that individuals can prove to a third party that a message came from its purported sender.

**Explain the differences between symmetric and asymmetric encryption.** Symmetric encryption uses the same shared secret key to encrypt and decrypt information. Users must have some mechanism to exchange these shared secret keys. The `Diffie–Hellman` algorithm provides one approach. Asymmetric encryption provides each user with a pair of keys: a public key, which is freely shared, and a private key, which is kept secret. Anything encrypted with one key from the pair may be decrypted with the other key from the same pair.

**Explain how digital signatures provide nonrepudiation.** Digital signatures provide nonrepudiation by allowing a third party to verify the authenticity of a message. Senders create digital signatures by using a hash function to generate a message digest and then encrypting that digest with their own private key. Others may verify the digital signature by decrypting it with the sender's public key and comparing this decrypted message digest to one that they compute themselves using the hash function on the message.

**Understand the purpose and use of digital certificates.** Digital certificates provide a trusted mechanism for sharing public keys with other individuals. Users and organizations obtain digital certificates from certificate authorities (`CAs`), who demonstrate their trust in the certificate by applying their digital signature. Recipients of the digital certificate can rely on the public key it contains if they trust the issuing `CA` and verify the `CA`'s digital signature.

**Demonstrate familiarity with emerging issues in cryptography.** `Tor` uses perfect forward secrecy to allow anonymous communication over the Internet. The `blockchain` is an immutable distributed public ledger made possible through the use of cryptography. `Homomorphic encryption` allows the protection of sensitive data while still facilitating computation on that data in a manner that preserves privacy. `Quantum computing` challenges modern approaches to cryptography and may be a disruptive force in the future.

# Review Questions

1. Mike is sending David an encrypted message using a symmetric encryption algorithm. What key should he use to encrypt the message?

    1. Mike's public key
    2. Mike's private key
    3. David's public key
    4. Shared secret key

2. Alan's team needs to perform computations on sensitive personal information but does not need access to the underlying data. What technology can the team use to perform these calculations without accessing the data?

    1. Quantum computing
    2. Blockchain
    3. Homomorphic encryption
    4. Certificate pinning

3. Norm is using full-disk encryption technology to protect the contents of laptops against theft. What goal of cryptography is he attempting to achieve?

    1. Integrity
    2. Nonrepudiation
    3. Authentication
    4. Confidentiality

4. Brian discovers that a user suspected of stealing sensitive information is posting many image files to a message board. What technique might the individual be using to hide sensitive information in those images?

    1. Steganography
    2. Homomorphic encryption
    3. Replay attack
    4. Birthday attack

5. Which one of the following statements about cryptographic keys is incorrect?

    1. All cryptographic keys should be kept secret.
    2. Longer keys are better than shorter keys when the same algorithm is used.
    3. Asymmetric algorithms generally use longer keys than symmetric algorithms.
    4. Digital certificates are designed to share public keys.

6. What type of cipher operates on one character of text at a time?

    1. Block cipher
    2. Bit cipher
    3. Stream cipher
    4. Balanced cipher

7. Vince is choosing a symmetric encryption algorithm for use in his organization. He would like to choose the strongest algorithm from the choices below. What algorithm should he choose?

    1. DES
    2. 3DES
    3. RSA
    4. AES

8. Kevin is configuring a web server to use digital certificates. What technology can he use to allow clients to quickly verify the status of that digital certificate without contacting a remote server?

    1. CRL
    2. OCSP
    3. Certificate stapling
    4. Certificate pinning

9. Acme Widgets has 10 employees and they all need the ability to communicate with one another using a symmetric encryption system. The system should allow any two employees to securely communicate without other employees eavesdropping. If an 11th employee is added to the organization, how many new keys must be added to the system?

    1. 1
    2. 2
    3. 10
    4. 11

10. Referring to the scenario in question 9, if Acme Widgets switched to an asymmetric encryption algorithm, how many keys would be required to add the 11th employee?

    1. 1
    2. 2
    3. 10
    4. 11
