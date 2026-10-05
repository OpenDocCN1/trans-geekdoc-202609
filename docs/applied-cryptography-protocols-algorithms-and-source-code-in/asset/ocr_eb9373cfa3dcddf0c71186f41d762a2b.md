# CHAPTER 24 Example Implementations

+   - User authentication (called single sign-on)
- Two-party authentication
- Key distribution
- Authentication of data origin and content

From a user's perspective, KryptoKnight is similar to Kerberos. Some differences are:

+   - KryptoKnight uses a hash function for authentication and encrypting tickets.
- KryptoKnight does not rely on synchronized clocks; it uses nonces for challenges
- If Alice wishes to communicate with Bob, KryptoKnight has the option of allowing Alice to send a message to Bob and for Bob to initiate the exchange protocol.

KryptoKnight has tickets and authenticators, just like Kerberos. It has TGSs, KryptoKnight calls them authentication servers. KryptoKnight's designers spent considerable effort minimizing the number of messages, lengths of messages, and amount of encryption. For further information on KryptoKnight, read [1110,173,174,175].

# 24.7 SESAME

SESAME stands for Secure European System for Applications in a Multivendor Environment. It is an European community security project, 50 percent funded by RACE [see Section 25.7], whose primary objective is producing technology for user authentication with distributed access control. This kind of a European version of Kerberos. It is a two-part project: Stage one is a basic prototype of the architecture, and stage two is a set of commercial projects. The three companies with the greatest hand in development are ICL in the United Kingdom, Germany, and Bull in France.

SESAME is an authentication and key-exchange system [361,1248,797,1043]. It uses the Needham-Schroeder protocol, with public-key cryptography to communicate between different security domains. The system is severely flawed in several respects. Instead of using a real encryption algorithm, it uses XOR with a 64-bit key size. Even worse, they use XOR in CBC mode, which leaves the plaintext unencrypted. In their defense, they planned using DES until the French government complained, they validated the code with DES but then removed it, and expect people to add it. It is unpremissible.

Authentication in SESAME is a function on the first of a message, not on the end of a letter. Key generation consists of two calls to the UNIX rand function, which isn't very random. SESAME uses crc32 and MD5 as one-way hash functions. And of course, SESAME is vulnerable to Kerberos-like password-guessing.