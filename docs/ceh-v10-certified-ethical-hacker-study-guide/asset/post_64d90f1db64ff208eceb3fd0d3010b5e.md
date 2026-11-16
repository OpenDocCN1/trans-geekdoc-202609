
This is sometimes referred to as public key cryptography. A common approach is to use a hybrid cryptosystem where public key cryptography is used to share a session key, which is a symmetric key used to encrypt messages within the session.

Certificates, defined by X.509, a subset of the X.500 digital directory standard, are used to store public key information. This includes information about the identity of the certificate holder so verification of the certificate can happen. Certificates may be managed using a CA, which is a trusted third party that verifies the identity of the certificate holder. A CA is not the only way to verify identity, though. PGP uses a web of trust model, where individual users validate identity by signing the public keys of people they know.

A MAC is used to ensure that messages haven't been altered. This is generally a cryptographic hash, which is an algorithm that generates a fixed-length digest value from variable-length data. This can be used not only for message authentication but also for verifying that files have not been tampered with or corrupted.

## Review Questions

You can find the answers in the Appendix.

- 1. With a rotation of 4, what does erwaiv decrypt to?
  - A. waive
  - B. wave
  - C. answer
  - D. decrypt

- 2. What do you call a message before it is encrypted?
  - A. Text
  - B. Plain text
  - C. Bare words
  - D. Bare text

- 3. What does PGP use to verify identity?
  - A. Central authority
  - B. Web of users
  - C. Web of trust
  - D. Central trust authority

- 4. What principle is used to demonstrate that a signed message came from the owner of the key that signed it?
  - A. Non-repudiation
  - B. Non-verifiability
  - C. Integrity
  - D. Authority

- 5. What is Diffie-Hellman used for?
  - A. Key management
  - B. Key isolation
  - C. Key exchange
  - D. Key revocation

- 6. How did 3DES improve on DES?
  - A. Made the key longer
  - B. Used two keys
  - C. Changed algorithms
  - D. Used three keys

- 7. What improvement does elliptic curve cryptography make?
  - A. Smaller keys improve speed
  - B. Algorithm is more complex
  - C. Doesn't use factoring, which is better
  - D. Longer keys

- 8. What is it called when two different data sets yield the same cryptographic hash?
  - A. Paradox
  - B. Collision
  - C. Crash
  - D. Unrealistic

- 9. Which of the following terms can be used in a description of asymmetric key encryption?
  - A. Private key
  - B. Multifactor
  - C. Public key
  - D. Single factor

- 10. If Alice were to send an email to Bob, what key would she use to encrypt the message?
  - A. PGP key
  - B. Private key
  - C. Public key
  - D. Symmetric key

- 11. What property allows you to trust someone trusted by a certificate authority you trust?
  - A. Commutative property
  - B. Associative property
  - C. Communicative property
  - D. Transitive property

- 12. Why is symmetric key encryption typically used over asymmetric key encryption?
  - A. It's faster.
  - B. It's more secure.
  - C. It's easier to implement.
  - D. It isn't encumbered with patents.

- 13. What is it called when both symmetric and asymmetric keys are used?
  - A. Fast cryptosystem
  - B. Hybrid cryptosystem
  - C. Super-symmetric cryptosystem
  - D. Dual key cryptosystem

- 14. What is MD5 or SHA-1 commonly used for in cryptography?
  - A. Media access control (MAC)
  - B. Machine authentication code (MAC)
  - C. Message access code (MAC)
  - D. Message authentication code (MAC)

- 15. What type of encryption does PGP use?
  - A. Symmetric key
  - B. Asymmetric key
  - C. Trusted key
  - D. Web key

![](img/421171b17a0c0dfae0aacde15d9831c1_507_0.png)

## Chapter 14

## Security Architecture and Design

THE FOLLOWING CEH TOPICS ARE COVERED IN THIS CHAPTER:

- Security architecture
- Service-oriented architecture
- N-tier application design
- Database structures
- Security models

![](img/421171b17a0c0dfae0aacde15d9831c1_508_0.png)

Developing strategies for an enterprise, including how to develop applications, takes a lot of consideration. There are many elements to think about, and you don't have to start from scratch. No matter what you are developing or implementing, it's important to consider users and, perhaps more important, data classifications and their necessary security requirements. Not all data is created equal, after all. Just as not all data is created equal, not all users are created equal. Because of that, when developing a security program, it's useful to have a security model. This means defining how you are going to allow users to interact with data and with each other. There are several ways of approaching the design of security models, and some of them relate to how data is classified.

Security models are a way to ensure that security policies are adhered to. Developing a security model is one way of defining behaviors to be implemented. This can help to guide application development and deployment as well. This may be especially true when it comes to defining architecture. There are different ways to implement applications today, especially as we move further away from a straight native application deployed on a single client system.

Additionally, there are security architectures to consider when it comes to application development and deployment. Developing a security architecture means using a top-down approach to ensuring that security policies, standards, and controls are all consistent and coherent. Security policy starts at the top of the organization, setting the direction based on business needs and requirements. It's important to keep in mind that security should be a business enabler.

## Data Classification

Not all data is created equal. Data classification is an important step when organizing security systems and controls. Data classification is used to identify and organize information that has similar security control needs. This allows appropriate access controls to be created. When you start thinking about security models, it is important to consider your data classifications, because security models are used to help identify who gets to look at what data. You can't do this without first classifying and organizing your data resources.

Different organizations will use different types of classification schemes, depending on the data resources in place. This is also something you will hear a lot when it comes to the government and perhaps especially the military. Table 14.1 lists common classifications in use within the government.

## TABLE 14.1 Governmental data classifications

| Classification | Description |
|---|---|
| Top secret | The highest level of data classification. Only a very limited number of people will be able to look at data classified as top secret. |
| Secret | The exposure of secret information would cause serious damage to national security. |
| Confidential | The exposure of confidential information would cause damage to national security. |
| Restricted | Exposure of restricted data would have undesirable effects. |
| Official | This is information that relates to government business and may not be an indicator of the potential for harm if the information were lost or exposed. |
| Unclassified | Unclassified information can be viewed by everyone. This may include declassified information that was once considered a higher classification but the threat posed by its exposure has subsided. |

Within each of these classification levels there may be additional compartments. Top secret information is not necessarily available to everyone who has been cleared at a top secret level. Just as not all data is created equal, not all people are created equal. Information sometimes needs to be compartmentalized even beyond these data classification levels. This is not the only way of categorizing data, of course. Organizations may have different ways of thinking about their information. Table 14.2 shows another way of classifying data.

## TABLE 14.2 Simple data classification

| Classification | Description |
|---|---|
| Restricted | Data that is internal or sensitive. Loss or disclosure of this data could cause significant damage to an organization. |
| Private | Data that may also be internal or sensitive, but the loss or disclosure of this data would cause only moderate damage to an organization. |
| Public | Data that is classified public would incur no damage to an organization if it were disclosed or lost. |

You can see this is a much simpler way of categorizing data. Even simpler than this would be two classifications: restricted and public. Again, it depends entirely on the type
