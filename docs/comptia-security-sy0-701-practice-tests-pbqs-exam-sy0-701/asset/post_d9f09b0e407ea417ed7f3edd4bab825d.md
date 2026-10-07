
observes that once logged in, if he presents the same token again, he is granted access without any restrictions. What type of vulnerability does this situation depict?

- (A) Cross-Site Request Forgery (CSRF)
- (B) Replay Attack
- (C) Man-in-the-Middle (MitM) Attack
- (D) Cross-Site Scripting (XSS)

**Explanation 481. Correct Answer: B. Replay Attack.** A replay attack, also known as playback attack, occurs when an attacker intercepts data and then retransmits it. In this scenario, Alex was able to reuse the authentication token to gain access, indicating that the system does not have mechanisms in place to prevent replayed tokens from being accepted multiple times.

**Option A is incorrect.** Cross-Site Request Forgery (CSRF) is an attack where an attacker tricks the victim into performing unwanted actions on a web application where they’re authenticated. It doesn’t involve reusing authentication tokens.

**Option C is incorrect.** While a Man-in-the-Middle (MitM) Attack can involve intercepting data between two parties, the described scenario doesn’t involve an attacker modifying or relaying the information in real-time.

**Option D is incorrect.** Cross-Site Scripting (XSS) vulnerabilities allow attackers to inject malicious scripts into web pages. The scenario doesn’t indicate any script injection.

**Question 482.** A large law firm has a centralized document repository where lawyers store client information, legal drafts, and other sensitive data. A new paralegal, Jenna, joins the firm and needs to be able to view client documents but should not be able to modify or delete them. Which type of permission should be granted to Jenna?

- (A) Read-Only
- (B) Full Control
- (C) Modify
- (D) Execute

**Explanation 482. Correct Answer: A. Read-Only.** The Read-Only permission allows users to view and open files or resources but does not allow them to modify, delete, or execute them. In this scenario, granting Jenna Read-Only access ensures she can view client documents without making any alterations or deletions.

**Option B is incorrect.** Full Control would give Jenna the ability to modify, delete, and even change the permissions of the documents, which exceeds the necessary permissions for her role.

**Option C is incorrect.** The Modify permission allows a user to make changes to documents, which is not appropriate for Jenna based on the scenario’s requirements.

**Option D is incorrect.** Execute permission is typically related to running programs or scripts and is not relevant to Jenna’s need to view documents.

**Question 483.** The IT department of a software development company wants to ensure that only company-approved development tools can be executed in their development environment, preventing any unauthorized or potentially harmful software from running. What should the IT department employ to achieve this?

- (A) Implement network segmentation
- (B) Conduct regular vulnerability assessments
- (C) Install a stable firewall
- (D) Establish an application allow list

**Explanation 483. Correct Answer: D. Establish an application allow list.** Establishing an application allow list would ensure that only specific, pre-approved applications can run in the development environment. This would prevent any unauthorized or potentially malicious software from being executed, aligning directly with the company’s goal.

**Option A is incorrect.** While network segmentation can isolate different parts of the network and limit the spread of potential threats, it does not prevent unauthorized applications from running within a segment.

**Option B is incorrect.** Regular vulnerability assessments identify weaknesses in systems, but they don’t proactively prevent specific applications from running.

**Option C is incorrect.** A stateful firewall monitors the state of active connections and can block or allow traffic based on stateful parameters, but it doesn’t regulate which applications can be executed on a workstation.

# **Question 484.** A company is implementing a system to ensure that code released to production is both unaltered and approved by a specific team member. Which of the following cryptographic techniques should they implement?

- (A) Symmetric encryption of the code
- (B) Hashing the code with SHA-256
- (C) Encrypting the code with the team member's public key
- (D) Digital signature by the team member

**Explanation 484. Correct Answer: D. Digital signature by the team member.** Digital signatures provide both integrity and non-repudiation. By having the specific team digitally sign the code, the company can ensure that the code has not been altered (integrity) and that it was approved by the designated individual (non-repudiation).

**Option A is incorrect.** Symmetric encryption provides confidentiality, but it doesn’t provide the needed integrity and non-repudiation in this scenario.

**Option B is incorrect.** Hashing the code provides a mechanism to check for alterations (integrity), but it does not provide non-repudiation or evidence of the specific team member’s approval.

**Option C is incorrect.** Encrypting with the team member’s public key doesn’t provide non-repudiation. Moreover, only the team member with the corresponding private key would be able to decrypt it, which might not be desirable for production releases.

**Question 485.** During an organization’s security review, the cybersecurity analyst noticed that there were multiple failed login attempts for different user accounts, each with a few commonly used passwords. What type of password attack does this scenario BEST describe?

- (A) Brute Force Attack
- (B) Dictionary Attack
- (C) Credential Stuffing
- (D) Password Spraying

**Explanation 485. Correct Answer: D. Password Spraying.** Password Spraying is an attack method where the attacker tries a few commonly used passwords against multiple accounts, rather than trying many passwords against a single account. The scenario described multiple accounts, aligning with this method.

**Option A is incorrect.** A Brute Force Attack involves trying all possible password combinations for a particular account. The scenario describes common passwords on multiple.

**Option B is incorrect.** A Dictionary Attack involves trying a list of probable passwords, often extracted from dictionaries or common password lists, against a single account. The emphasis is multiple accounts.

**Option C is incorrect.** Credential Stuffing involves previously leaked username and password pairs to gain unauthorized access. The emphasis is on known credentials, not common passwords.

**Question 486.** A project manager is working on a new product launch and has documents with sensitive projections on her local computer. She occasionally shares these documents with select board members via email. While she wants to keep the financial documents secure, she doesn't want to encrypt all the data on her computer. Which encryption approach should she utilize?

- (A) Full-disk Encryption
- (B) Transport-layer Encryption
- (C) File-level Encryption
- (D) Partition Encryption

**Explanation 486. Correct Answer: C. File-level Encryption.** File-level Encryption allows individual files or folders to be encrypted. In this scenario, the project manager can encrypt only the sensitive financial documents, allowing her to securely share them while keeping the rest of her data unencrypted.

**Option A is incorrect.** Full-disk Encryption would encrypt the entire drive, which is more than what's required.

**Option B is incorrect.** Transport-layer Encryption protects data in transit, but does not specifically address encrypting individual files for storage and sharing.

**Option D is incorrect.** Partition Encryption encrypts entire partitions or volumes, which isn't necessary in this scenario.

**Question 487.** A financial institution is looking to adopt an encryption algorithm for its transactions that is considered to be very secure due to its longer key length, compared to older
