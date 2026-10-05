# 2 CHAPTER 1 Foundations

Plaintext is denoted by M, for message, or P for plaintext. It can be a stream of bits, a text file, a bitmap, a stream of digitized voice, a digital image . . . as a computer is concerned, M is simply binary data. [After this chapter, this book concerns itself with binary data and computer cryptography.] The plaintexttext can be intended for either transmission or storage. In any case, M is the message to be encrypted.

Ciphertext is denoted by C. It is also binary data: sometimes the same size as M, sometimes larger. [By combining encryption with compression, C may be smaller than M. However, encryption does not accomplish this.] The encryption function E operates on M to produce C. Or, in mathematical notation:

```
E(M) = C
```

In the reverse process, the decryption function D operates on C to produce M:

```
D(C) = M
```

Since the whole point of encrypting and decrypting a message is to recover the original plaintext, the following identity must hold true:

```
D(E(M)) = M
```

# Authentication, Integrity, and Nonrepudiation

In addition to providing confidentiality, cryptography is often asked to do other jobs:

+   - **Authentication.** It should be possible for the receiver of a message to ascertain its origin; an intruder should not be able to masquerade as someone.
- **Integrity.** It should be possible for the receiver of a message to verify that it has not been modified in transit; an intruder should not be able to substitute a false message for a legitimate one.
- **Nonrepudiation.** A sender should not be able to falsely deny that he sent a message.

These are vital requirements for social interaction on computers, and are analogous to face-to-face interactions. Someone who is he says he is . . . that some credentials—whether a driver's license, a medical degree, or a passport—are valid . . . that document purporting to come from a person actually came from that person. provide. These are the things that authentication, integrity, and nonrepudiation

# Algorithms and Keys

A **cryptographic algorithm**, also called a **cipher**, is the mathematical function used for encryption and decryption. (Generally, there are two related functions: one for encryption and the other for decryption.)