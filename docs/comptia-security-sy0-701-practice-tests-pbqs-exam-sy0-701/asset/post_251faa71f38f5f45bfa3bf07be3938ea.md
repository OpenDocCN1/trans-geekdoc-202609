
Question 494. An organization is choosing a hash function for digital signatures. They want to ensure that it is resistant to scenarios where an attacker might produce two different messages having the same hash. Which type of attack are they trying to defend against?

- (A) Side-channel Attack
- (B) Replay Attack
- (C) Birthday Attack
- (D) Ciphertext-only Attack

Explanation 494. Correct Answer: C. Birthday Attack. In a Birthday Attack, attackers exploit the mathematics behind the birthday problem in probability theory, aiming to find two different inputs that produce the same output, or hash. When selecting a hash function for digital signatures, it’s crucial to pick one that is resistant to Birthday Attacks to maintain the integrity of the signatures.

Option A is incorrect. A Side-channel Attack involves obtaining information from the physical implementation of a cryptographic system rather than exploiting a theoretical weakness in algorithms or protocols. It’s unrelated to producing two messages with the same hash.

Option B is incorrect. A Replay Attack involves intercepting data (like a login session) and then resending or replaying it to gain unauthorized access. It does not focus on matching hash values.

Option D is incorrect. In a Ciphertext-only Attack, the attacker has the ciphertext and tries to derive the plaintext without knowing the key. The scenario does not describe this type of attack.

**Question 495.** At ExamsDigest, employees can access the company’s cloud-based storage system. However, access to certain files within the storage is determined by the employee’s department, job title, and years of service. For instance, senior managers in the finance department with more than five years of service can view the company’s financial forecasts. Which access control model is ExamsDigest using?

- (A) Rule-Based Access Control (RAC)
- (B) Role-Based Access Control (RBAC)
- (C) Attribute-Based Access Control (ABAC)
- (D) Discretionary Access Control (DAC)

**Explanation 495. Correct Answer: C. Attribute-Based Access Control (ABAC).** Attribute-Based Access Control (ABAC) determines access based on attributes of the user, resource, and environment. In the scenario, the employee’s department, job title, and years of service are the attributes that determine their access to specific files.

**Option A is incorrect.** RAC works based on predefined rules, typically without involving multiple user attributes like department or job title.

**Option B is incorrect.** While RBAC is close in functionality, it assigns permissions based on roles (like “manager” or “clerk”), not on a combination of attributes.

**Option D is incorrect.** DAC allows resource owners to specify who can access their resources based on their discretion. It doesn’t involve a combination of attributes to determine access.

Question 496. After a recent system upgrade, CloudTech Corp. decided to validate the efficiency and reliability of its new data processing system. To do this, they run the new system alongside the old one and compare the outcomes. This way, they aim to ensure that the new system is both robust and capable of handling the current workload. What kind of testing is CloudTech Corp. utilizing?

- (A) Load Testing
- (B) Failover Testing
- (C) Parallel Processing Testing
- (D) Simulation Testing

**Explanation 496. Correct Answer: C. Parallel Processing Testing.** Parallel Processing Testing involves running two systems simultaneously (typically the new one and the old one) to compare the outcomes. This kind of testing ensures that a new system is as effective and reliable as the previous one.

**Option A is incorrect.** Load Testing checks the system’s ability to handle the expected volume of transactions and to see if it can maintain acceptable response times.

**Option B is incorrect.** Failover Testing is done to ensure that a system can switch to a backup or secondary system in the case of a failure, rather than comparing two systems for consistency.

**Option D is incorrect.** Simulation Testing involves creating a model of the system under test and stimulating it with virtual users or devices to understand its behavior under various conditions.

**Question 497.** SecureNet Inc. recently upgraded their security infrastructure. To validate how the new system would respond in real-world scenarios without exposing it to actual risks, they decide to imitate certain cyber threats in a controlled environment. Which type of test is SecureNet Inc. planning to conduct?

- (A) Penetration Testing
- (B) Simulation Testing
- (C) Vulnerability Assessment
- (D) Failover Testing.

**Explanation 497. Correct Answer: B. Simulation Testing.** Simulation testing involves creating a model of the system under test and then stimulating it with virtual users or devices to understand its behavior under various conditions. In the context of cybersecurity, this means imitating cyber threats in a controlled environment to assess how security infrastructure responds.

**Option A is incorrect.** Penetration Testing involves ethical hackers attempting to breach an organization’s defenses, which involves actual risks, rather than just a simulation.

**Option C is incorrect.** A Vulnerability Assessment identifies, quantifies, and prioritizes vulnerabilities in a system but doesn’t necessarily imitate threats in a controlled environment.

**Option D is incorrect.** Failover Testing ensures that a system can switch to a backup or secondary system in case of a failure, and does not focus on simulating threats.

Question 498. A marketing team is collaborating on a new campaign and requires access to a shared folder. However, they shouldn’t be able to modify files created by others. How should permissions be set on this shared folder?

- (A) Assign the marketing team full control
- (B) Allow the marketing team read-only access
- (C) Assign the marketing team write-only access
- (D) Assign the marketing team modify permission but deny the permission

Explanation 498. Correct Answer: D. Assign the marketing team modify permission but deny the permission. By providing modify permissions but denying delete permissions, team members can create and edit their own files, but they won’t be able to delete or modify files by others.

Option A is incorrect. Full control would allow team members to modify or delete any file, which is not desired.

Option B is incorrect. Read-only access would prevent team members from creating or editing any files.

Option C is incorrect. Write-only access would prevent team members from viewing existing files.

Question 499. An organization’s e-commerce platform experienced a data breach where attackers exploited a known vulnerability. Post-incident analysis revealed that a patch was available for this vulnerability two months before the breach not applied. Which of the following would have been the MOST effective measure to prevent this breach?

- (A) Implementing stronger user authentication methods
- (B) Increasing network monitoring for signs of malicious activity
- (C) Applying the available patch in a timely manner
- (D) Migrating to a different e-commerce platform

Explanation 499. Correct Answer: C. Applying the available patch in a timely manner. Patches are developed by software vendors to address known vulnerabilities in their software. Timely application of these patches is crucial for ensuring that systems are protected against known threats. In this scenario, applying the available patch would have directly addressed the vulnerability that was exploited.

Option A is incorrect. While implementing stronger user authentication methods can enhance security, it wouldn’t directly mitigate a vulnerability in the software that could be exploited without authentication.

Option B is incorrect. Increasing network monitoring can help detect malicious activity, but it doesn’t prevent the exploitation of a known software vulnerability.

Option D is incorrect. Migrating to a different platform is a drastic measure that might introduce new vulnerabilities and would not ensure security unless accompanied by good patch management practices.
