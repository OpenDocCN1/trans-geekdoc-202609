
patching doesn’t directly prevent specific external applications from connecting.

**Option D is incorrect.** Encrypting data at rest helps protect stored data from unauthorized access but does not regulate which applications can connect to the server.

**Question 74.** Alice needs to provide proof of the authenticity of a digital document she’s sending to Bob. Which of the following cryptographic elements should Alice use to accomplish this task and ensure Bob knows the document came from her?

- (A) Encrypt the document with Bob's private key
- (B) Encrypt the document with her public key
- (C) Sign the document with her private key
- (D) Sign the document with Bob's public key

**Explanation 74. Correct Answer: C. Sign the document with her private key.** To prove authenticity, a digital signature is created using the sender’s private key. When Bob receives the document, he can verify the signature using Alice’s public key. This proves that the document was signed by Alice and has not been tampered with during transit.

**Option A is incorrect.** Bob’s private key is known only to Bob and should never be used by anyone else, including for encryption.

**Option B is incorrect.** Encrypting with Alice’s public key doesn’t prove authenticity. It would also mean only Alice’s private key could decrypt it, which isn’t the intent.

**Option D is incorrect.** One does not sign documents with the recipient’s public key. Signatures are created using the sender’s private key.

**Question 75.** Carla, a security analyst, receives an alert that one of the company’s server certificates may have been exposed in a recent data breach. What is the most immediate action Carla should take to ensure that the exposed certificate cannot be used maliciously?

- (A) Request a new certificate from the CA
- (B) Update the company firewall rules
- (C) Add the certificate to the Certificate revocation list (CRL)
- (D) Perform a vulnerability assessment on the server

**Explanation 75. Correct Answer: Add the certificate to the Certificate revocation list (CRL).** If a certificate is believed to be compromised, the most immediate action is to revoke it. This is done by adding the certificate to the Certificate revocation list (CRL). Systems and applications that check the CRL before establishing secure communications will then not trust the compromised certificate.

**Option A is incorrect.** While requesting a new certificate may be necessary after revoking the compromised one, the immediate action should be revoking the potentially compromised certificate.

**Option B is incorrect.** Updating firewall rules, while essential for many security scenarios, doesn’t directly address the misuse of a potentially exposed certificate.

**Option D is incorrect.** A vulnerability assessment is a broader action to identify weaknesses in the system. While valuable, it doesn’t directly address the issue of the compromised certificate.

**Question 76.** A database administrator is concerned about identical passwords. To mitigate this risk, what cryptographic technique should the administrator implement?

- (A) Digital signature
- (B) Salting
- (C) Key stretching
- (D) Symmetric encryption

**Explanation 76. Correct Answer: B. Salting.** Salting involves adding a unique string to each password before hashing, ensuring that identical passwords result in different hashes and protecting against rainbow table attacks.

**Option A is incorrect.** Digital signatures are used for authenticity and integrity, not for handling identical passwords.

**Option C is incorrect.** Key stretching is used to make password cracking more time-consuming, but is not the primary method for ensuring identical passwords have different hashes.

**Option D is incorrect.** Symmetric encryption is used for data confidentiality and doesn't address the issue of identical passwords in hashes.

**Question 77.** An online retailer is considering various methods to protect credit card information. Instead of storing actual numbers, they opt for substitutes. What is this called?

- (A) Symmetric encryption
- (B) Digital watermarking
- (C) Hashing
- (D) Tokenization

**Explanation 77. Correct Answer: D. Tokenization.** Tokenization replaces sensitive data with non-sensitive substitutes called tokens, reducing the risk of exposing actual credit card numbers.

**Option A is incorrect.** Symmetric encryption uses a key to encrypt data, whereas the scenario focuses on replacing numbers with substitutes.

**Option B is incorrect.** Digital watermarking is not a standard method for protecting credit card number storage.

**Option C is incorrect.** Hashing is a one-way function, whereas tokenization is reversible for authorized systems.

**Question 78.** During a scheduled maintenance window, a security administrator plans to apply a critical update to the company’s firewall. Which of the following actions is MOST crucial to ensure minimized downtime?

- (A) Notifying the firewall vendor about the update
- (B) Disabling all firewall rules
- (C) Creating a rollback plan in case of failure
- (D) Scheduling the update during peak hours

**Explanation 78. Correct Answer: C. Creating a rollback plan in case of failure.** In change management, having a rollback plan ensures that if there are issues with the applied update, the system can be reverted to its previous state, thereby minimizing downtime.

**Option A is incorrect.** While it might be useful to notify the vendor, it is not the most crucial step to minimize downtime.

**Option B is incorrect.** Disabling all firewall rules can introduce significant security risks.

**Option D is incorrect.** Scheduling updates during peak hours could result in maximum disruption.

**Question 79.** A security administrator is considering a cryptographic solution for protecting data in transit between servers located in the same data center. The primary goal is to ensure speed and efficiency in encryption and decryption processes. Which type of encryption would best meet this requirement?

- (A) Asymmetric encryption using RSA
- (B) Symmetric encryption using AES
- (C) Hybrid encryption using a combination of RSA and AES
- (D) Asymmetric encryption using ECC

**Explanation 79. Correct Answer: B. Symmetric encryption using AES.** Symmetric encryption, such as AES, is typically faster and requires less computational resources than asymmetric encryption. This makes it suitable for scenarios where high-speed encryption and decryption are essential, like data in transit between servers in a data center.

**Option A is incorrect.** Asymmetric encryption using RSA is more computationally intensive than symmetric encryption and may not be the most efficient for the given scenario.

**Option C is incorrect.** While hybrid encryption can provide a balance of security and speed, using only symmetric encryption (AES) is more efficient for the described case.

**Option D is incorrect.** ECC, like RSA, is an asymmetric encryption method, which means it will typically be slower than symmetric methods like AES.
