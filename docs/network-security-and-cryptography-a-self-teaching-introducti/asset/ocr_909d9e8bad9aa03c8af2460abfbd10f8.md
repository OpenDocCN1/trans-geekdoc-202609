# 12.5.7 IPSec Key Management

The automated Key Management Protocol for IPSec is known as the “ISAKMP/Oakley Key Management Protocol,” where ISAKMP stands for Internet Security Association Key Management Protocol. It compromises two components:

+   - Oakley Key Exchange Protocol: It is a key exchange protocol, a variant of the Diffie-Hellman Key-Exchange Protocol, with added security features for thwarting Man-in-the-Middle Attacks and Clogging Attacks.
- Internet Security Association Key Management Protocol (ISAKMP): It defines the procedures and formats to negotiate, modify, and delete Security Associations.

# 12.5.8 Features of Oakley Key-Exchange Protocol

The bare Diffie-Hellman Key-Exchange Protocol suffers from the following limitations:

+   - The key-exchange entities are not provided with each other’s identity.
- It is prone to Man-in-the-Middle Attacks.
- It is prone to Clogging Attacks, where an adversary (Say “E”) captures the authentication exchanges of some valid user (say “A”). Then “E” impersonates (masquerades) as user “A” and sends a large number of key-exchange requests to another user (Say “B”). This forces user “B” to perform many computations related to key determination, preventing it from doing other useful work. This is called a clogging attack on user “B.”

The Oakley Key-Exchange Protocol supports the following features to thwart attacks:

+   - Use of nonces to thwart replay attacks.
- Use of Data-Origin Authentication to thwart Man-in-the-Middle Attacks: Oakley key Determination supports the following techniques for Data-Origin Authentication:
- Digital Signatures of the sender.
- Encryption of some critical fields in the messages like User-Id and Nounces using the sender’s Private Key (Public-Key Cryptography).