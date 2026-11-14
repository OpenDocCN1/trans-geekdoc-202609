

| | | |
|:---|:---|:---|
| 2 | U1 chooses a random value A | U2 chooses a random value B |
| 3 | U1 calculates the value: a = g^A(mod p) | U2 calculates the value: b = g^B(mod p) |
| 4 | U1 and U2 exchange the values of a and b.<br>a ↔ b<br>Note: this exchange does not need to be secure. | |
| 5 | U1 calculates the value: K = b^A(mod p) | U2 calculates the value: K = a^B(mod p) |
| | Both users then share an identical secret key K without sharing the values A and B. | |

NOTE.

- A and B can take the values of the secret keys associated with U1 and U2.
- It is theoretically impossible to find the values A and B from the values p, g, a, b and K.
- In practice, the numbers used are numbers with 300 digits raised to the power of 100 digits, which is very strong.

## Example

| Step | U1 | U2 |
|:---|:---|:---|
| 1 | p = 23<br>g = 7 | |
| 2 | A=3 | B=6 |
| 3 | a = 7^3(mod 23) = 21 | b = 7^6(mod 23) = 4 |
| 4 | U1 and U2 exchange the values of a and b.<br>a ↔ b | |
| 5 | K = 4^3(mod 23) = 18 | K = 21^6(mod 23) = 18 |
| | The two users then share an identical secret key 18. | |

## 8.4. Hash functions

Hash functions are one-way functions used to ensure data integrity. A hash function processes a block of data which may be large or diversified in nature, to return a small hash value, called the “message digest” which is of fixed size. A hash function is characterized by the following properties:

- it is impossible to reconstruct a message from its hash value;
- modifying a message always results in another hash value.

It is impossible for two different messages to have the same hash value.

The list of most commonly used hash functions includes:

- MD5: enables the creation of 128-bit message digests;
- SHA-1: allows the creation of 160-bit message digests;
- SHA-2: enables the creation of 224-bit and 512-bit message digests.

## 8.5. HMAC codes

Hash-based Message Authentication Code (HMAC) allows you to calculate a message digest by using existing hash functions combined with a shared secret key. This makes it possible to ensure the authentication as well as integrity of the data.

Cisco uses two HMAC functions:

- HMAC-MD5 with a shared key, based on the MD hashing algorithm;
- HMAC-SHA-1 with shared key, based on the SHA-1 hashing algorithm.

## 8.6. Asymmetric cryptography

### 8.6.1. Introduction

Asymmetric cryptography is a procedure that is based on a pair of keys (public key and private key) for the encryption and decryption of data. Both keys can encrypt the data. However, the complementary key is necessary to decrypt the data.

Asymmetric cryptography is based on complex mathematical algorithms and, thus, takes longer to compute than symmetric algorithms.

Asymmetric cryptography is used to ensure confidentiality and authentication.

### 8.6.2. How it works

| Confidentiality | Confidentiality → public key (encryption) + private key (decryption) |
|:---|:---|
| | – The public key is used to encrypt; the corresponding private key is used to decipher. |
| | – Given that the private key is only present on a single system, this process guarantees confidentiality. |
| | – This scenario is often used for key exchange. |
| Authentication | Authentication → private key (encryption) + public key (decryption) |
| | – The private key is used to encrypt; the corresponding public key is used for decryption. |
| | – Given that the private key is present on only one system, authentication is guaranteed when its public key decrypts the message. |

Figure 8.4. gives an overview of the procedure that ensures **confidentiality**.

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_167_0.png)

**Figure 8.4.** Only A can read the message sent by B

Figure 8.5. presents the procedure that ensures **authentication**.

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_168_0.png)

Figure 8.5. Only A can have sent this message

### 8.6.3. Digital signatures

### 8.6.3.1. Introduction

A digital signature can ensure the integrity of an electronic document and authenticate the author of the document. It is characterized by the following properties:

- it cannot be falsified;
- it is part of the signed document and cannot be moved to another document;
- a signed document cannot be modified further.

A digital signature offers three security functions:

- the authenticity of the signatory: the identity of the signatory has been approved definitively;
- integrity of the data: digital signatures guarantee that the document has remained intact from the time of transmission;
- non-repudiation: the signatory cannot repudiate the signature on the document.

### 8.6.3.2. How it works

The process of validating a signed document, sent by User A to User B, can be summarized as follows:

### Step 1: signing the document

The first user, “A”, will:

- 1) generate a private key **Kpr** and a public key **Kpb**;
- 2) calculate the hashing value of the document using a hash function **H**;
- 3) encrypt the hash value using their private key **Kpr**;
- 4) send the following information to the recipient, “B”:
  - the public key **Kpb**;
  - the document;
  - the function H;
  - the encrypted hash value.

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_169_0.png)

**Figure 8.6.** The signature of the document

### Step 2: the verification of the signed document

The second user, “B” will then:

- 2) calculate the hash value of the document using the hash function H;
- 3) compare the message digest generated by the document and the message digest previously decrypted using the public key Kpb. If the two message digests are identical, the signature is valid.

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_170_0.png)

Figure 8.7. Verifying the signed document

### 8.6.4. Public key infrastructure

### 8.6.4.1. Introduction

A Public Key Infrastructure (PKI) is a set of services that can ensure the confidentiality, integrity and authentication of data in an organization, and is based on the fundamental principles of asymmetric encryption. PKI solutions are based on digital certificates and the guarantee of a reliable third party.

### 8.6.4.2. Terminology

| Concepts | Definitions and characteristics |
|:---|:---|
| **Certification Authority (CA)** | – A Certification Authority is a reliable organization that makes it possible to associate public keys with users, companies, devices etc.<br>– This authority is given the responsibility of digitally signing and publishing these public keys and guaranteeing their authenticity.<br>– A certification Authority may be a private organization (e.g. VeriSign, Cisco etc.) or a public organization. |
| **A certificate** | – An electronic document that associates a user name or organization name with a public key.<br>– Digital certificates are digitally signed by a certification authority.<br>– In addition to the public key of the concerned entity, a digital certificate contains information on the validity period of the certificate, the algorithm used to sign the certificate etc. |
| **The certificate revocation list (CRL)** | – A CRL is a list of certificates that are no longer valid.<br>– A certificate may become invalid for several reasons:<br>  - the expiry of its validity date;<br>  - the comprising of the private or public key associated with the certificate;<br>  - a change in at least one field included in the name of the certificate holder;<br>  - Others. |

### 8.6.4.3. PKI standards

The most widely used PKI norms include:

- X.509: this is a standard created by the organization ITU-T, which defines a basic standard format for public key certificates, the Certificate Revocation Lists (CRL) and other attributes of a certificate;
- **public key cryptographic standards (PKCS)**: these are a set of specifications designed by the “RSA” laboratories for putting in place public key cryptography techniques. The most commonly adopted PKCS in the IT world include:

