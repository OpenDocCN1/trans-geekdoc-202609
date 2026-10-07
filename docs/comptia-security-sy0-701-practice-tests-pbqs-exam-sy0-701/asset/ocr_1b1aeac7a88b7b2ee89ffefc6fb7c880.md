**Option A is incorrect.** A digital certificate is used to verify the identity of an entity and bind a public key to it, but it doesn’t offer the transparency of transactions or their immutability.

**Option C is incorrect.** Symmetric encryption is used to encrypt and decrypt data using a single secret key, but it doesn’t provide transaction transparency or immutability.

**Option D is incorrect.** Secure file transfer protocol (SFTP) is a method to securely transfer files over a network, but it doesn’t maintain an public ledger of transactions.

**Question 63.** A company is implementing a system to ensure that code released to production is unaltered and approved by a specific team member. Which of the following cryptographic techniques should they implement?

+   (A) Symmetric encryption of the code
(B) Hashing the code with SHA-256
(C) Encrypting the code with the team member's public key
(D) Digital signature by the team member

**Explanation 63.** **Correct Answer: D. Digital signature by the team member.** Digital signatures provide both integrity and non-repudiation. By having the specific team member digitally sign the code, the company can ensure that the code has not been altered (integrity) and that it was approved by the designated individual (non-repudiation).

**Option A is incorrect.** Symmetric encryption provides confidentiality, but it doesn’t provide the needed integrity and non-repudiation in this scenario.