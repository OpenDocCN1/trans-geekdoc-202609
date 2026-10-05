
transfers funds to a different account. So, there is the need to ensure the security of databases and also to secure the communication of critical messages through the Internet. This is where cryptography plays its role to make the communications more and more secure and trusted. There is a never-ending fight between the designers of secure systems and the hackers. The hackers attempt to find loopholes in the cryptographic systems and the designers of such systems attempt to plug such loopholes. For designers to detect the loopholes, they have to employ hacker's techniques (called ethical hacking).

## 3.2 BASIC TERMS RELATED TO CRYPTOGRAPHY

**Cryptology**: Cryptology in Greek means “A Hidden Secret.” Though sometimes the terms Cryptography and Cryptology are used interchangeably, strictly speaking Cryptology encompasses two areas: Cryptography and Cryptanalysis.

- 1. **Cryptography** deals with design techniques for ensuring data confidentiality and/or data origin authentication. In a nutshell, cryptography deals with the design of Ciphers.
- 2. **Cryptanalysis** deals with techniques for the breaking of ciphers. A cryptanalyst attempts to defeat cryptographic means. It attempts to obtain unauthorized access to information and/or attempts to forge the authentication sequence of others. Cryptanalysis is also known as hacking, which is divided into two categories:
    - **Ethical hacking**, which is used by the cipher designers to determine weaknesses existing in cipher schemes and to eliminate these to make the cipher schemes more robust against attacks.
    - **Unethical hacking**, which is performed by antisocial elements with the aim of having unauthorized access to protected information.

**Plaintext**: It refers to a message in plain form that is readily intelligible. If transmitted in this form, it is highly prone to unauthorized disclosure, since a message in transit can be easily captured by adversaries.

Cipher-text: It refers to the encrypted form of a message. Prior to transmission, a plaintext M is encrypted so that it does not remain readily legible. The message travels from the sender to the intended recipients in cipher-text form. The cipher-text should be such that adversaries should find it extremely difficult to decipher it. The intended recipients will have the necessary keys to decipher it easily.

Encryption Algorithm: The Algorithm used for transforming plaintext to cipher-text is called an "Encryption (or Enciphering) Algorithm." It performs complex substitutions andor permutations over the plaintext using an encryption key to produce the resulting cipher-text.

```
$C = f(M, K_i) = E_{K_i}[M]$
```

where C is Cipher-text, M is Plaintext, $K_i$ is the Encryption Key, and E is the Encryption algorithm.

The encryption process must be reversible so as to enable deciphering of the cipher-text by the intended recipients.

- *Decryption Algorithm*: It transforms cipher-text C back to the original plaintext M. The decryption process is the reverse of the Encryption process. The intended recipients of cipher-text C will perform the decryption process using Decryption Key $K_d$ and recover plaintext M from the received cipher-text C.

```
$M = f(C, K_d) = D_{K_d}[C]$
```

where D is the Decryption algorithm.

The Key Distribution mechanism should be so secure that only the intended recipients get the decryption key and no adversary is able to lay hands on it. The authorized recipients of the key must keep it highly secure.

Since Decryption is reverse of Encryption, the following holds true:

```
$D_{K_d}[C] = D_{K_d}[E_{K_i}[M]] = (E_{K_i})^{-1}[E_{K_i}[M]] = M$
```

In the case of Symmetric Cryptography, the Decryption Key is the same as the Encryption Key. However, in the case of Asymmetric or Public Cryptography, the Decryption Key is different from the Encryption Key; the Decryption Key is related to the Encryption Key, but knowing the Encryption Key is it still extremely difficult (or computationally infeasible) to determine the Decryption Key.

## 3.1.1 Cryptographic Primitives

Encryption and Decryption Algorithms, Cryptographic Hash Functions, and Pseudo-Random Number Generators are basic building blocks of Crypto Systems. These are called *Cryptographic Primitives*.

## 3.1.2 Cryptographic Protocols

A single building block (or *Cryptographic Primitive*) may not be sufficient to provide a complete solution to achieve secrecy, validation, and integrity of data. It may require a series of building blocks to accomplish the task. Such a well-defined series of steps is called a *Cryptographic Protocol*. Figure 3.1 shows a generic model of secure communication.

![](img/d3b56042c756fbcc011ff06f1b9f53f0_141_0.png)

FIGURE 3.1 Generic model of secure communication (M: Plaintext Message, C: Cipher-text, K: Encryption Key, K': Decryption Key).

## 3.1.3 Encryption (at the Sender's End)

$C = E_{K_k} [M]$

## 3.1.4 Decryption (at the Recipient's End)

$D_{K_{k'}} [C] = D_{K_k} [E_{K_k} [C]] = (E_{K_k})^{-1} [E_{K_k} [M]] = M$

## 3.2 REQUIREMENTS OF SECURE COMMUNICATION

Cryptography meets the following requirements of secure communication:

- The sender of a confidential message should be able to encrypt the message easily. What travels from the sender to the intended recipient is the cipher-text.

- It is presumed that adversaries can easily capture the cipher-text from the transmission media. The encryption should be such that an adversary should not be able to easily extract the plaintext from the cipher-text.

- The intended recipient should be able to decipher the received cipher-text and recover the plaintext using the decryption keys available with the recipient. For this to be feasible, the sender and the intended recipient first exchange keys that are needed for encryption and decryption. The Decryption Key may be the same as the Encryption Key (as the case of Symmetric Cryptography) or the two keys may be different (as in the case of Public Key Cryptography).

- The exchange of keys is done prior to the exchange of messages. In the case of Symmetric Cryptography, the exchange of a secret key (shared between the two parties) has to be done by the most secure means. The sender of a message will encrypt the message using the secret key and the intended recipient will use the same key for decryption. Since the key is known only to the sender and the intended recipient, no eavesdropper should be able to recover the plaintext easily. However, in the case of Public Key Cryptography, each party will generate a pair of keys that relate to each other. One of the keys, the Private Key, is kept by the party, and the other key, known as the Public Key, is made public; that is, made known to all users. Any message to be transmitted is encrypted using the Public Key of the intended recipient. The intended recipient will be able to decrypt the cipher-text using the Private Key. Since the Private Key is kept secret by each party, only the intended recipient will be able to recover the plaintext; an attacker will find it extremely hard to decrypt the cipher-text.

- If a cipher-text gets modified in transit (either intentionally or unintentionally due to system error), the intended recipient should be able to detect that the cipher-text has been modified, and the recipient should be able to take appropriate action.

- If some entity (say “A”) impersonates some other entity (say “B”) and sends a message to entity “C” with the intention of making “C” feel as if the message was sent by “B,” it is called a “masquerade.” In this case; “C” should be able to detect the impersonation and take appropriate corrective action. For this to be feasible, “C” should have the means to authenticate the source of the received message to ascertain that the message has been sent by the alleged sender (“B” in this case) or one else.

- The sender of a message should not be able to later denying sent the message. In case the sender denies having a message, the recipient should be able to prove that the message has been sent by the alleged sender and no one else. It is not feasible to prove in Symmetric Cryptography, but it is easy to prove in Public Key Cryptography. This function is known as “Source Non-Repudiation.”

- The recipient of a message should not be able to later denying having received a message. In case the recipient denies this, the sender of the message should be able to prove that the message has been received by the alleged recipient. Recipient acknowledgement would be needed to prove the Recipient Non-Repudiation.

## 3.3 OSI SECURITY ARCHITECTURE X.800

Open Systems Interconnection (OSI) Architecture X.800 is a set of standards relating to Security of Information. These standards have been developed by the International Telecom Union (ITU-T), UN-sponsored body that is responsible for the development of standards relating to telecommunications. The standards pertain to Security Attacks, Security Mechanisms, and Security Services.

**Security Attacks** – Security Attacks refer to the actions intending to compromise the security of information belonging to an organization.

**Security Mechanisms** – Security Mechanisms refer to the processes (or devices incorporating the processes) that are designed to prevent, detect, or recover from Security Attacks.

**Security Services** – Security Services refer to the services that make use of Security Mechanisms to counter Security Attacks.
