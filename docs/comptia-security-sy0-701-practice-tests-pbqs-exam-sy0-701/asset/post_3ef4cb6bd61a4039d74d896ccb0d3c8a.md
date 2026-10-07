
Option A is incorrect. RSA is an asymmetric encryption method, not a key exchange protocol.

Option B is incorrect. HMAC is a specific type of message authentication code that involves hashing and is not used for key exchange.

Option D is incorrect. AES is a symmetric encryption algorithm and does not offer a key exchange mechanism.

Question 60. A company is developing a new video conferencing tool. They want to make sure that all video and audio data transmitted between participants are encrypted and protected from eavesdropping. Which type of encryption should the developers implement to achieve this?

- (A) Endpoint Encryption
- (B) Transport-layer Encryption
- (C) Volume-level Encryption
- (D) Database-level Encryption

Explanation 60. Correct Answer: B. Transport-layer Encryption. Transport-layer Encryption is tailored for securing data while it is in transit. By implementing this encryption, the company ensures that all video and audio data during the video conference are confidential, maintaining the privacy of the participants.

Option A is incorrect. Endpoint Encryption is designed for data on specific devices like laptops or mobile phones, not for data being transmitted over networks.

Option C is incorrect. Volume-level Encryption pertains to encrypting specific logical drives or volumes, not data in transit.

Option D is incorrect. Database-level Encryption secures data within a database and is not specific to data transmission over networks.

Question 61. After a significant cybersecurity incident, ABC Tech revamped its incident response procedures. However, the documentation was not updated to reflect these changes. During a subsequent minor incident, there was confusion regarding the steps to be followed. Which of the following is the MOST direct implication of not updating the incident response documentation?

- (A) The company may have to invest in new cybersecurity tools
- (B) Stakeholders might lose trust in the company’s ability to handle incidents
- (C) Incident response might be inconsistent and less effective
- (D) ABC Tech may have to hire external consultants for incident response

Explanation 61. Correct Answer: C. Incident response might be inconsistent and less effective. Without up-to-date documentation reflecting the most recent incident response procedures, there’s a risk that the response will be inconsistent, leading to inefficiencies and potential oversights.

Option A is incorrect. While new tools might be beneficial, the direct concern with outdated documentation is the effectiveness of the response.

Option B is incorrect. While stakeholder trust is important, the immediate implication of outdated documentation is the quality of the incident response.

Option D is incorrect. Hiring external consultants might be an option, but the direct consequence of outdated documentation is the potential ineffectiveness of the internal response process.

Question 62. A financial organization is considering implementing a system that allows all users to view all transactions, but once a transaction is recorded, it cannot be altered or deleted. They want this transparency to foster trust among their users. Which of the following would best meet this requirement?

- (A) Digital certificate
- (B) Open public ledger
- (C) Symmetric encryption
- (D) Secure file transfer protocol

Explanation 62. Correct Answer: B. Open public ledger. An open public ledger provides transparency by allowing all users to view all transactions. Moreover, once a transaction is added to the ledger, it becomes immutable, meaning it cannot be altered or deleted, ensuring data integrity and fostering trust among participants.

Option A is incorrect. A digital certificate is used to verify the identity of an entity and bind a public key to it, but it doesn’t offer the transparency of transactions or their immutability.

Option C is incorrect. Symmetric encryption is used to encrypt and decrypt data using a single secret key, but it doesn’t provide transaction transparency or immutability.

Option D is incorrect. Secure file transfer protocol (SFTP) is a method to securely transfer files over a network, but it doesn’t maintain a public ledger of transactions.

Question 63. A company is implementing a system to ensure that code released to production is unaltered and approved by a specific team member. Which of the following cryptographic techniques should they implement?

- (A) Symmetric encryption of the code
- (B) Hashing the code with SHA-256
- (C) Encrypting the code with the team member's public key
- (D) Digital signature by the team member

Explanation 63. Correct Answer: D. Digital signature by the team member. Digital signatures provide both integrity and non-repudiation. By having the specific team member digitally sign the code, the company can ensure the code has not been altered (integrity) and that it was approved by the designated individual (non-repudiation).

Option A is incorrect. Symmetric encryption provides confidentiality, but it doesn’t provide the needed integrity and non-repudiation in this scenario.

Option B is incorrect. Hashing the code provides a mechanism to check for alterations (integrity), but it does not provide non-repudiation or evidence of the specific team member’s approval.

Option C is incorrect. Encrypting with the team member’s public key doesn’t provide non-repudiation. Moreover, only the team member with the corresponding private key would be able to decrypt it, which might not be desirable for production releases.

Question 64. Your company has recently deployed an update to its CRM application. Post-update, users are experiencing connectivity issues. As a security administrator, which of the following steps should you take FIRST to address the connectivity problem without causing data loss?

- (A) Restart the application immediately
- (B) Disconnect all users and then restart the application
- (C) Validate the update's integrity and then restart the application
- (D) Reinstall the previous version of the CRM application

Explanation 64. Correct Answer: C. Validate the update's integrity and then restart the application. Before making any changes, it’s essential to validate the update’s integrity to ensure it was correctly applied.

Option A is incorrect. Restarting the application immediately might cause further complications if the update was not correctly applied.

Option B is incorrect. Disconnecting users might be necessary at some point, doing so without validating the update’s integrity can result in further disruptions.

Option D is incorrect. Reinstalling the previous version is a drastic step and might not be necessary if the update’s integrity can be validated and issues resolved with a restart.
