
hash using the sender’s public key. If a subsequent hashing of the message reveals an identical value, two things are known: First, the message has not been altered. Second, the sender possessed the private key of the named sender, so is presumably the sender him- or herself.

A digital signature does not by itself protect the contents of the message from interception. The message is still sent in the clear, so if confidentiality of the message is a requirement, additional steps must be taken to secure the message from eavesdropping. This can be done by encrypting the message itself, or by encrypting the channel over which it is transmitted.

## Use of Proven Technologies

When setting up a cryptographic scheme, it is important to use proven technologies. Proven cryptographic libraries and proven cryptographically correct random number generators are the foundational elements associated with a solid program. Homegrown or custom elements in these areas can greatly increase risk associated with a broken system. Developing your own cryptographic algorithms is beyond the abilities of most groups. Algorithms are complex and difficult to create. Any algorithm that has not had public review can have weaknesses. Most good algorithms are approved for use only after a lengthy test and public review phase.

## Chapter Review

In this chapter, you became acquainted with the principles of cryptography. The chapter opened with the concepts of cryptography, including the description of vocabulary elements associated with general cryptography. An examination of the fundamental methods of cryptography, encryption, and hashing was presented in terms of the types of algorithms and the types of data. Data can be in either block form, where many bytes are present at a time for encryption, or in stream form, where bytes are spaced temporally. Encryption algorithms are either symmetric or asymmetric in nature. The issue of key exchange, a challenge in the case of symmetric encryption, was presented, including methods such as ephemeral Diffie-Hellman exchanges that offer perfect forward secrecy. Newer methods, including elliptic curve and quantum-based cryptography, were also covered.

The chapter presented the use of hash functions for verification of integrity. The combination of hash functions with asymmetric encryption enables things such as digital signatures and non-repudiation. The chapter concluded with such topics as key escrow and steganography.

## Questions

To help you prepare further for the CompTIA Security+ exam, and to test your level of preparedness, answer the following questions and then check your answers against the correct answers at the end of the chapter.

- 1. Why are session keys utilized?
   - A. To protect each session individually.
   - B. To get the benefits of both types of encryption ciphers.
   - C. Session keys provide a higher bit strength.
   - D. Session keys can be safely shared, similar to public keys.

- 2. Why is hashing a unique form of cryptography?
   - A. Hashing uses ten times the bit strength of regular encryption.
   - B. Hashing is a hidden encryption cipher that allows you to have encrypted text that appears the same as unencrypted text.
   - C. Hashing is a one-way function, with no way to extract the plaintext from the ciphertext.
   - D. Hashing allows you to share all details of the algorithm publicly, without a loss to security.

- 3. What factors are important to a digital signature? (Choose all that apply.)
   - A. Confidentiality
   - B. Integrity
   - C. Availability
   - D. Non-repudiation

- 4. What is a popular use of ECC?
   - A. Cryptography on low-power mobile devices
   - B. More efficient SSL key exchange for servers
   - C. The enforcement of a larger keyspace
   - D. Steganography

- 5. When would out-of-band key exchange be used?
   - A. When using a stream cipher.
   - B. When using varying length keys, such as a one-time pad.
   - C. It is a key component of Diffie-Hellman.
   - D. It is required as part of using the AES algorithm.

- 6. How does a block cipher handle plaintext input?
   - A. It generates a key of the same length as the input and encrypts the text.
   - B. It uses a hash algorithm to reduce the input to match the current key.
   - C. It divides the input into predefined lengths, and pads the remainder to maintain a set length.
   - D. It encrypts it only to the private key.

- 7. When you get an SSL certificate from a web page, what kind of cipher is used?
   - A. One-time pad
   - B. Symmetric
   - C. Asymmetric
   - D. All of the above

- 8. Which of the following is a popular use of key escrow?
   - A. Key sharing for groups
   - B. Having keys prepared for future use
   - C. Home use
   - D. Enterprise environment

- 9. Which of the following describes a pitfall of new or proprietary algorithms?
   - A. They could have an unknown weakness.
   - B. They could have too low a key strength.
   - C. They have deliberate weaknesses placed in them by the government.
   - D. All of the above.

- 10. What makes steganography so hard to detect?
   - A. There are many images on the Internet.
   - B. It involves changes in the image that are too subtle to detect.
   - C. The data can be encrypted and encoded in a proprietary manner.
   - D. All of the above.

For questions 11–15, assume the following scenario: You have been asked to develop software specs for a new cloud-based file-sharing application that will primarily be used to store and share password information.

- 11. What are the advantages to using an asymmetric cipher as part of the design? (Choose all that apply.)
   - A. Integrity
   - B. Non-repudiation
   - C. Authentication of users
   - D. Secure key exchange
   - E. Fast encryption
   - F. Ability to add multiple users to the encryption

- 12. Where would you use a symmetric cipher as part of the design?
   - A. For passphrase storage
   - B. For authenticating users
   - C. Multiuser collaboration
   - D. File transfers to and from the cloud

- 13. In what situation would this application benefit from key escrow?
   - A. User forgets their private key passphrase
   - B. Government legal action
   - C. Security audits
   - D. Both A and B
   - E. Both A and C

- 14. What key exchange method would be optimal for an online solution?
   - A. In-band
   - B. Out-of-band
   - C. Both A and B
   - D. Neither A nor B

- 15. When would non-repudiation be important to your application?
   - A. An attacker breaks the encryption algorithm.
   - B. One user adds a new user to the system.
   - C. A collaborative user makes changes to a document that need to be securely tracked.
   - D. Non-repudiation would not be important.

## Answers

- 1. B. Session keys allow a communication to get the benefits of both types of encryption ciphers. Asymmetric is used for key exchange, and symmetric, the faster protocol, is used for data encryption.
- 2. C. Hashing is a one-way function that creates a digest of the message and cannot be reversed to extract the source plaintext.
- 3. B and D. Integrity and non-repudiation are the important factors of digital signatures. A document can be hashed to a value, and that value can be signed by the sender’s key. If any change is made to the document, the hash will change, and because the hash is signed, the attacker cannot re-encrypt the changed hash with a key they don’t possess. If the hash is correct, the sender signed it.
- 4. A. ECC requires less power for a given key strength, making ECC a good candidate for mobile devices.
- 5. **B.** Out-of-band key exchange can best be used if the length of the key must match the length of the message, as in a one-time pad cipher. Alternatively, it can be useful when a key exchange protocol cannot be used securely.
- 6. **C.** A block cipher divides the input into predefined lengths called blocks, and then pads any remainder to make a complete block.
- 7. **C.** SSL certificates are part of a public key infrastructure, using asymmetric keys.
- 8. **D.** Key escrow, or key recovery, is popular in an enterprise environment where systems exist that would lose large volumes of data if the primary passphrase were lost.
- 9. **A.** Any algorithm that has not had public review can have weaknesses in the algorithm. Most good algorithms are only approved for use after a lengthy public review phase.
- 10. **D.** All three answers are correct. There are so many images, sound files, and video files on the Internet that scanning all of them for hidden messages would be an unachievable task. Also, the changes are so minimal as to be very difficult to detect. The data can also be encrypted to make pattern analysis much more difficult, and the encoding can be proprietary to avoid leaving a known pattern in image pixels.
- 11. **C, D, and F.** The best answers are authentication of users, secure key exchange, and ability to add multiple users to the encryption. Asymmetric keys will allow each user to be authenticated, as they should be the only ones with access to the private keys. Asymmetric keys also allow secure exchange of any necessary session keys, and as asymmetric keys are user based, the removal of a single user can be accomplished without compromising the security of the data.
- 12. **D.** Symmetric ciphers are good at performing encryption quickly, allowing for good file transfer speeds.
- 13. **D.** Both a forgotten key passphrase and a court-ordered government action could be possible uses of key escrow.
- 14. **A.** In-band key exchange would be an optimal design for an online solution. The delays caused by out-of-band key exchange would greatly limit usability and slow adoption of the application.
- 15. **C.** Non-repudiation is important in a collaborative environment so that changes to documents can be securely tracked and the person who made the changes cannot deny having made the changes.
