
## 19. B
Alice creates the digital signature using her own private key. Then Bob, or any other user, can verify the digital signature using Alice’s public key.

## 20. B
The salt is a random value added to a password before it is hashed by the operating system. The salt is then stored in a password file with the hashed password. This increases the complexity of cryptanalytic attacks by negating the usefulness of attacks that use precomputed hash values, such as rainbow tables.

## 21. A
Hash functions do not include any element of secrecy and, therefore, do not require a cryptographic key.

## 22. D
A preaction fire suppression system activates in two steps. The pipes fill with water once the early signs of a fire are detected. The system does not dispense water until heat sensors on the sprinkler heads trigger the second phase.

## 23. B
The Encapsulating Security Payload (ESP) protocol provides confidentiality and integrity for packet contents. It encrypts packet payloads and provides limited authentication and protection against replay attacks.

## 24. D
The greatest risk when a device is lost or stolen is that sensitive data contained on the device will fall into the wrong hands. Confidentiality protects against this risk.

## 25. C
The exclusive or (XOR) operation is true when one and only one of the input values is true.

## 26. A
DES uses a 64-bit encryption key, but only 56 of those bits are actually used as keying material in the encryption operation. The remaining 8 bits are used to detect tampering or corruption of the key.

## 27. C
The `*-Security Property` states that an individual may not write to a file at a lower classification level than that of the individual. This is also known as the confinement property.

## 28. B
The Diffie-Hellman algorithm allows for the secure exchange of symmetric encryption keys over a public network.

## 29. C
Protection Profiles (PPs) specify the security requirements and protections that must be in place for a product to be accepted under the Common Criteria.

## 30. A
Hash functions must be able to work on any variable-length input and produce a fixed-length output from that input, regardless of the length of the input.

## 31. C
Binary keyspaces contain a number of keys equal to two raised to the power of the number of bits. Two to the fifth power is 32, so a 5-bit keyspace contains 32 possible keys.

## 32. B
Kerckhoff’s principle says that a cryptographic system should be secure even if everything about the system, except the key, is public knowledge.

## 33. A
Mantraps use a double set of doors to prevent piggybacking by allowing only a single individual to enter a facility at a time.

## 34. A
While it would be ideal to have wiring closets in a location where they are monitored by security staff, this is not feasible in most environments. Wiring closets must be distributed geographically in multiple locations across each building used by an organization.

## 35. D
The `*-Integrity Property` states that a subject cannot modify an object at a higher integrity level than that possessed by the subject.

## 36.
The architecture security concepts match with the descriptions as follows:

1.  **Time of check**: C. The time at which the subject checks whether an object is available.
2.  **Covert channel**: A. A method used to pass information over a path not normally used for communication.
3.  **Time of use**: D. The time at which a subject can access an object.
4.  **Maintenance hooks**: E. An access method known only to the developer of the system.
5.  **Parameter checking**: F. A method that can help prevent buffer overflow attacks.
6.  **Race condition**: B. The exploitation of difference between time of check and time of use.

## 37. B
In the Fair Cryptosystem approach to key escrow, the secret keys used in communications are divided into two or more pieces, each of which is given to an independent third party.

## 38. A
The Ready state is used when a process is prepared to execute but the CPU is not available. The Running state is used when a process is executing on the CPU. The Waiting state is used when a process is blocked waiting for an external event. The Stopped state is used when a process terminates.

## 39. A
EAL1 assurance applies when the system in question has been functionally tested. It is the lowest level of assurance under the Common Criteria.

## 40. A
Administrators and processes may attach security labels to objects that provide information on an object’s attributes. Labels are commonly used to apply classifications in a mandatory access control system.

## 41. B
Open-source software exposes the source code to public inspection and modification. The open-source community includes major software packages such as the Linux operating system.

## 42. A
Adam created a list of individual users that may access the file. This is an access control list, which consists of multiple access control entries. It includes the names of users, so it is not role-based, and Adam was able to modify the list, so it is not mandatory access control.

## 43. C
Parameter checking, or input validation, is used to ensure that input provided by users to an application matches the expected parameters for the application. Developers may use parameter checking to ensure that input does not exceed the expected length, preventing a buffer overflow attack.

## 44. A
`Kernel mode`, `supervisory mode`, and `system mode` are all terms used to describe privileged modes of system operation. User mode is an unprivileged mode.

## 45. D
Multistate systems are certified to handle data from different security classifications simultaneously by implementing protection mechanisms that segregate data appropriately.

## 46. C
For systems running in System High mode, the user must have a valid security clearance for all information processed by the system, access approval for all information processed by the system, and a valid need to know for some, but not necessarily all, information processed by the system.

## 47. B
Steganography is the art of using cryptographic techniques to embed secret messages within other content. Some steganographic algorithms work by making alterations to the least significant bits of the many bits that make up image files.

## 48. C
The Caesar cipher is a shift cipher that works on a stream of text and is also a substitution cipher. It is not a block cipher or a transposition cipher. It is extremely weak as a cryptographic algorithm.

## 49. A
The kernel lies within the central ring, Ring 0. Conceptually, Ring 1 contains other operating system components. Ring 2 is used for drivers and protocols. User-level programs and applications run at Ring 3. Rings 0 through 2 run in privileged mode while Ring 3 runs in user mode. It is important to note that many modern operating systems do not fully implement this model.

## 50. D
In an infrastructure as a service environment, security duties follow a shared responsibility model. Since the vendor is responsible for managing the storage hardware, the vendor would retain responsibility for destroying or wiping drives as they are taken out of service. However, it is still the customer’s responsibility to validate that the vendor’s sanitization procedures meet their requirements prior to utilizing the vendor’s storage services.

## 51. B
The major difference between a code and a cipher is that ciphers alter messages at the character or bit level, not at the word level. DES, shift ciphers, and word scrambles all work at the character or bit level and are ciphers. “One if by land; two if by sea” is a message with hidden meaning in the words and is an example of a code.
