hash using the sender’s public key. If a subsequent hashing of the message reveals an identical value, two things are known: First, the message has not been altered. Second, the sender possessed the private key of the named sender, so is presumably the sender him- or herself.

A digital signature does not by itself protect the contents of the message from interception. The message is still sent in the clear, so if confidentiality of the message is a requirement, additional steps must be taken to secure the message from eavesdropping. This can be done by encrypting the message itself, or by encrypting the channel over which it is transmitted.

# Use of Proven Technologies

When setting up a cryptographic scheme, it is important to use proven technologies. Proven cryptographic libraries and proven cryptographically correct random number generators are the foundational elements associated with a solid program. Homegrown or custom elements in these areas can greatly increase risk associated with a broken system. Developing your own cryptographic algorithms is beyond the abilities of most groups. Algorithms are complex and difficult to create. Any algorithm that has not had public review can have weaknesses. Most good algorithms are approved for use only after a lengthy test and public review phase.

# Chapter Review

In this chapter, you became acquainted with the principles of cryptography. The chapter opened with the concepts of cryptography, including the description of vocabulary elements associated with general cryptography. An examination of the fundamental methods of cryptography, encryption, and hashing was presented in terms of the types of algorithms and the types of data. Data can be in either block form, where many bytes are present at a time for encryption, or in stream form, where bytes are spaced temporally. Encryption algorithms are either symmetric or asymmetric in nature. The issue of key exchange, a challenge in the case of symmetric encryption, was presented, including methods such as ephemeral Diffie-Hellman exchanges that offer perfect forward secrecy. Newer methods, including elliptic curve and quantum-based cryptography, were also covered.

The chapter presented the use of hash functions for verification of integrity. The combination of hash functions with asymmetric encryption enables things such as digital signatures and non-repudiation. The chapter concluded with such topics as key escrow and steganography.

# Questions

To help you prepare further for the CompTIA Security+ exam, and to test your level of preparedness, answer the following questions and then check your answers against the correct answers at the end of the chapter.