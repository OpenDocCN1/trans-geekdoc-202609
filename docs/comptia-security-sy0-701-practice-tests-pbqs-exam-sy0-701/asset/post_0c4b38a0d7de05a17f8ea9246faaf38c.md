
[content]
employees can use their existing credentials to access services on SoftTech’s system without the need to create new accounts.

**Option A is incorrect.** Creating new accounts for every user in a collaborating organization isn’t scalable and negates the advantages of federation.

**Option B is incorrect.** Allowing anonymous access would compromise security and wouldn’t guarantee identity verification.

**Option D is incorrect.** Resetting all passwords and providing them anew is not a practical or secure approach to collaboration between two organizations.

**Question 451.** GlobalTech is implementing a disaster recovery plan and wants to ensure continuous availability with no data loss. They have decided to use replication as a backup strategy. Which of the following replication techniques should GlobalTech implement to achieve their objective?

- (A) Periodic replication scheduled daily
- (B) Asynchronous replication with hourly synchronization
- (C) Synchronous replication
- (D) Snapshot replication every 30 minutes

**Explanation 451.** **Correct Answer: C. Synchronous replication.** Synchronous replication ensures that data is written to the primary and secondary locations simultaneously, ensuring no data loss and continuous availability. This method is suitable for GlobalTech’s requirement of no data loss.

**Option A is incorrect.** Periodic replication scheduled daily could result in up to a day’s worth of data loss in the event of a disaster.

**Option B is incorrect.** Asynchronous replication with hourly synchronization could lead to an hour’s worth of data loss if an incident occurs just before synchronization.

**Option D is incorrect.** Snapshot replication every 30 minutes could result in 30 minutes of data loss in the event of an incident.

**Question 452.** An e-commerce website suddenly experiences a sharp increase in traffic, causing the website to become slow and occasionally inaccessible. The IT team observes that a large number of requests are originating from multiple IP addresses spread across various countries. What type of network attack is the e-commerce website likely experiencing?

- (A) Man-in-the-middle attack
- (B) DNS spoofing
- (C) Distributed denial-of-service (DDoS) attack
- (D) ARP poisoning

**Explanation 452.** Correct Answer: C. Distributed denial-of-service (DDoS) attack. In a DDoS attack, the attacker uses multiple systems, often compromised from different locations, to flood a target system with requests, making the target slow or inaccessible.

**Option A is incorrect.** A man-in-the-middle attack involves an attacker secretly intercepting and possibly altering the communication between two parties. It doesn’t lead to website inaccessibility due to high traffic.

**Option B is incorrect.** DNS spoofing is when an attacker introduces corrupt DNS cache information to redirect traffic to a different IP address, usually under the attacker’s control. It doesn’t cause increased traffic from various countries.

**Option D is incorrect.** ARP poisoning is a technique by which an attacker sends fake ARP messages to a local area network. This is usually used to link an attacker’s MAC address with the IP address of another host, causing any traffic meant for that IP address to be sent to the attacker instead.

**Question 453.** A software development company is working on a mobile banking application. They want to ensure that sensitive operations like cryptographic processes and biometric data validation are isolated from the main operating system to prevent potential tampering. Which tool should they consider implementing to achieve this objective?

- (A) Hardware Security Module (HSM)
- (B) Key Management System (KMS)
- (C) Secure enclave
- (D) Trusted Platform Module (TPM)

**Explanation 453.** **Correct Answer: C. Secure enclave.** A secure enclave is a hardware-based isolated environment often found in modern CPUs, especially in mobile devices. It’s designed to run specific operations such as cryptographic processes and biometric data validation, ensuring that this data is kept isolated from the main operating system, making it resilient to tampering.

**Option A is incorrect.** While a HSM is a dedicated hardware device that manages cryptographic keys, it doesn’t provide the isolated environment within a CPU for operations like the secure enclave does.

**Option B is incorrect.** KMS is primarily focused on the management of cryptographic keys, not on creating isolated environments for operations.

**Option D is incorrect.** TPM provides hardware-level security for individual devices, but it doesn’t create a segregated environment within the CPU for operations like the secure enclave.

**Question 454.** A popular social media platform allows third-party applications to access user data and post on behalf of users. To avoid sharing user passwords with third-party applications and provide limited, scoped access, which authentication method should the platform use?

- (A) Embed user passwords in the application’s code
- (B) Use basic authentication with username and password for every request
- (C) Implement Single Sign-On (SSO) using OAuth to provide token-based access
- (D) Rely solely on CAPTCHA for third-party app authentication

**Explanation 454.** Correct Answer: C. Implement Single Sign-On (SSO) using OAuth to provide token-based access. OAuth provides token-based access and lets third-party applications operate on behalf of users without exposing user passwords. OAuth tokens can also be scoped to limit the range of actions a third-party application can perform.

**Option A is incorrect.** Embedding passwords in application code is insecure and goes against best practices.

**Option B is incorrect.** Basic authentication exposes user credentials and doesn’t offer the scoped access OAuth provides.

**Option D is incorrect.** CAPTCHA is designed to differentiate between human and automated access but doesn’t handle authentication or authorization.

**Question 455.** A company has noticed an increase in malware infections over the past month. After investigating, it was determined that the infections were caused by employees visiting websites that newly registered but had malicious intent. Which of the following would be the BEST approach to mitigate this threat?

- (A) Implement a block rule to deny access to all websites
- (B) Use a web filter that incorporates domain checks and blocks newly registered
- (C) Set the web filter to block websites categorized as "Business"
- (D) Enforce multi-factor authentication for all internet-based applications

Explanation 455. **Correct Answer: B. Use a web filter that incorporates domain checks and blocks newly registered.** Reputation-based web filters can evaluate the trustworthiness of domains, as cybercriminals often use these for phishing or malware distribution.

**Option A is incorrect.** Blocking access to all websites is an extreme measure that would hinder business operations and productivity.

**Option C is incorrect.** Simply blocking websites categorized “Business” does not specifically target the threat of newly registered domains. Additionally, some business-relevant websites might not be categorized properly.

**Question 456.** MetroTech recently experienced an incident where an employee mistakenly deleted a portion of their database. The IT team was able to restore the data using a backup snapshot taken 24 hours prior. However, some data loss still occurred. Which of the following recommendations would minimize data loss in a similar situation in the future?

- (A) Configure backup snapshots to be taken on a weekly basis
- (B) Employ a differential backup solution in addition to snapshots
- (C) Increase the storage capacity for backups
- (D) Use an hourly snapshot backup schedule

**Explanation 456.** **Correct Answer: D. Use an hourly snapshot backup schedule.** Increasing the frequency of snapshot backups, such as taking them hourly, will ensure that the maximum amount of data that can be lost is limited to that hour’s worth. This minimizes the potential for data loss compared to a 24-hour window.

**Option A is incorrect.** Taking weekly snapshots would actually increase the potential data loss window, not decrease it.

**Option B is incorrect.** While differential backups capture data changes since the last full backup, they don’t necessarily reduce the time window for data loss like increasing snapshot frequency would.

**Option C is incorrect.** Increasing storage capacity allows for more backups or longer retention but does not in itself reduce the time window for data loss.

**Question 457.** Alice receives an email from Bob with an attached document. She wants to verify both the authenticity of the sender and the integrity of the attached document. Which of the following should Bob have used before sending the email?

- (A) Encrypt the document with his private key
- (B) Hash the document
- (C) Encrypt the document with Alice's public key
- (D) Sign the document with his private key
[/content]
