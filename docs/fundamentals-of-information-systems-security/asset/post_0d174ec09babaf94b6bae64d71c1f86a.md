
key pair to encrypt and decrypt. The originator is the only one who knows one of the keys. It has an irrefutable timestamp. The argument in court would go something like this:

> > Encryption does more than just keep messages secret. It can validate the identity of the sender. This encrypted message decrypts with this public key. Only the holder of the associated private key could have created this message. The message contains a time-based hash produced by a trusted third-party timestamping device. Neither party could have tampered with it. Thus, we know with effective certainty that this message as decrypted is genuine and originated with this known party. This is nonrepudiation.

## Business and Security Requirements for Cryptography

In this section, you will learn about information security principles and how cryptography can address them.

### Internal Security

A number of security objectives add value to a business. These include the following:

- **Confidentiality**—Confidentiality keeps information readable only by authorized people. It keeps that data away from people who are unauthorized. For example, most companies keep salary information confidential.

- **Privacy**—Privacy is often confused with confidentiality. Privacy differs in that it protects the release of information that could identify an individual. For example, information that discloses that a person who lives in a certain postal code was treated for a broken arm and a facial laceration on a specific day at a certain hospital may reveal a person's identity. Privacy assures that an attacker cannot assemble available information to identify an individual.

- **Integrity**—Integrity ensures that no one has changed or deleted data. For example, payroll data need integrity to make sure no one changes a payment after sending it to the check printer.

- **Authorization**—Authorization means approving someone to do a specific task or access certain data. For example, changing salary plans requires proper authorization from management.

- **Access control**—Access control involves restricting information to the right people. For example, you can store salary plans in a locked file cabinet to which only HR employees have the key.

### Security in Business Relationships

A number of security objectives add value to relationships between businesses or between businesses and their customers. In addition to those listed before, they include the following:

- **Message authentication**—Message authentication confirms the identity of the person who started a correspondence. For example, a broker would like to know that a message to “Buy 1,000 shares of XYZ for account ABC” came from ABC.

> > **NOTE**
> As privacy issues become more and more important, an interesting source of tension in security circles becomes more obvious. Nonrepudiation means that an action can be positively associated with an individual. Privacy means being able to carry out actions without disclosing personal information. Which one is more important? We don’t know yet. These two concepts are fundamentally at odds, and the debate continues.

- **Signature**—A digital signature binds a message or data to a specific entity. Note that this is not a digitized signature, which is an image of an electronically reproduced signature.
- **Receipt and confirmation**—Email messages often use receipt and confirmation. Receipt verifies that an entity acknowledges information has arrived. Confirmation acknowledges that the provider has provided a service.
- **Nonrepudiation**—Nonrepudiation means that the person who sends a message cannot later deny it. For example, if the person who made the buy order were to dispute it after XYZ dropped 50 percent, nonrepudiation would prove the original message was valid.

### Security Measures That Benefit Everyone

Beyond business and customer relationships, certain security objectives add value to information systems. In addition to those items already listed, these objectives include the following:

- **Anonymity**—This disguises a user's identity. For example, a dissident in a repressive country might want to post information to a web discussion site without the authorities knowing who he or she is. Unfortunately, criminals and terrorists can use anonymity as well to avoid detection.
- **Timestamping**—This provides an exact time when a producer creates or sends information. For example, people submitting tax returns at the last minute may want to prove they met the deadline.
- **Revocation**—This stops authorization for access to data. For example, a person who loses a credit card calls the issuer to stop use of the card.
- **Ownership**—This associates a person with information to claim legal rights. For example, most documents have copyright notices that tell who wrote them.

### Cryptographic Principles, Concepts, and Terminology

There are many different information security objectives. It is important to understand them, how they work together, and how they sometimes oppose one another. They represent most of the goals of security initiatives, including cryptography. One of the best summaries of security objectives is in the Handbook of Applied Cryptography. TABLE 9-1 contains the security objectives summary. When you try to solve a business security problem, you need to understand these terms. Then you can tell if you could use a cryptographic solution.

### Cryptographic Functions and Ciphers

A basic understanding of cryptographic ciphers can tell you how cryptography can satisfy your business needs. Each cipher has specific characteristics that may make it desirable or undesirable for any situation. The first issue to consider when evaluating a cipher is its intended use. Are you trying to secure data in transit or data at rest? Different ciphers solve different problems better than others. Once you select a cipher, you still have to make additional decisions about things such as key size and operational mode. Many symmetric ciphers operate as either a stream cipher or a block cipher, depending on the mode you

### TABLE 9-1 Information security objectives.

| OBJECTIVE | STEPS TO TAKE |
|---|---|
| Privacy or confidentiality | Keep information secret from all unauthorized users. |
| Integrity | Ensure that unauthorized users or unknown processes have not altered information. |
| Entity authentication or identification | Corroborate the identity of an entity (that is, a person, a computer terminal, a credit card, etc.). |
| Message authentication | Corroborate the source of information; authenticate the data's origin. |
| Signature | Bind information to an entity. |
| Authorization | Convey an official sanction to do or be something to another entity. |
| Validation | Provide timely authorization to use or manipulate information or resources. |
| Access control | Restrict access to resources to privileged entities. |
| Certification | Endorse information by a trusted entity. |
| Timestamping | Record the time a user created or accessed information. |
| Witnessing | Verify the action to create an object or verify an object's existence by an entity other than the creator. |
| Receipt | Acknowledge that the recipient received information. |
| Confirmation | Acknowledge that the provider has provided services. |
| Ownership | Grant an entity the legal right to use or transfer a resource to others. |
| Anonymity | Conceal the identity of an entity involved in some process. |
| Nonrepudiation | Prevent an entity from denying previous commitments or actions. |
| Revocation | Retract certification or authorization. |

choose. A stream cipher encrypts one byte (or bit) at a time, whereas a block cipher encrypts an entire block of data at a time. Deciding on the “best” type of cipher is a complex task.
There are many subtleties and very few standard answers. As ciphers become more complex, they rely on new techniques to generate keys and transform plaintext into ciphertext.

Two fertile areas of research are elliptic curve cryptography (ECC) and quantum cryptography. ECC ciphers depend on the algebraic structures of elliptic curves over finite fields. These ciphers can result in very secure ciphertext using smaller keys than more traditional ciphers. However, ECC imposes a high computational overhead cost. Quantum cryptography bases its algorithms on the properties of quantum mechanics. The basic difference between classic cryptography and quantum cryptography is in the difficulty in breaking the cipher. Breaking classic ciphers is extremely difficult; breaking quantum cryptography ciphers is theoretically impossible. Of course, quantum cryptography implementations are computationally expensive and more difficult to get “right.” For those reasons, classic cryptography still dominates in today’s implementations.
