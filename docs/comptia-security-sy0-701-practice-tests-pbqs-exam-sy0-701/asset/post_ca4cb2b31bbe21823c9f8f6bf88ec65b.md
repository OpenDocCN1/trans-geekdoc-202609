
Question 444. After a security incident, a forensic investigation revealed that a compromised internal workstation was communicating with a known malicious IP address. To prevent further communication, the security team decided to take immediate action. Which of the following is the BEST immediate action to ensure the workstation cannot communicate with that IP?

-   (A) Implement a block rule on the web filter for the IP address
-   (B) Disable the network port of the compromised workstation
-   (C) Use a honeypot to divert the traffic from the malicious
-   (D) Update the firewall's firmware

**Explanation 444. Correct Answer: A. Implement a block rule on the web filter for the IP address.** By implementing a block rule specifically for the known malicious IP address on the web filter, any attempt to communicate with that IP would be stopped, effectively preventing further malicious communications.

**Option B is incorrect.** Clearing the network port of the compromised workstation would disconnect the machine from the network, but it wouldn't specifically prevent communication with the malicious IP if the port were to be re-enabled.

**Option C is incorrect.** While honeypots can be used to divert or study attacker behavior, they are not the most direct way to block communication with a known malicious IP address.

**Option D is incorrect.** Updating the firewall’s firmware is a general maintenance task and does not specifically address blocking communications with the known malicious IP.

Question 445. Jennifer, an IT administrator, is asked to onboard a new remote employee for a sales role. Which of the following is the BEST approach for provisioning the user account?

-   (A) Assign the new user the same access privileges as the CEO because they might require all resources
-   (B) Provide the new user with administrative rights to ensure they can install and configure any needed software
-   (C) Use the access privileges from a template of a salesperson to provide the required resources
-   (D) Allow the new user to decide and self-select the necessary access based on their job role

**Explanation 445. Correct Answer: C. Use the access privileges from a template of a salesperson to provide the required resources.** Provisioning users based on role templates ensures that users have just the access they need, adhering to the principle of least privilege.

**Option A is incorrect.** This goes against the principle of least privilege and can introduce significant security risks.

**Option B is incorrect.** Giving administrative rights to employees without a proper need can expose the organization to unnecessary risks.

**Option D is incorrect.** Users should not self-select access rights as they might not be aware of potential security implications.

Question 446. The IT department of a large organization receives reports from employees that they are unable to access resources on the network. Upon investigation, the IT department discovers that the Access Control List (ACL) settings have been recently modified. Which of the following would be the PRIMARY reason to review and modify the ACL settings?

-   (A) To balance the network load
-   (B) To update the organization's firewall rules.
-   (C) To ensure appropriate access rights to resources
-   (D) To update the organization's password policy

**Explanation 446. Correct Answer: C. To ensure appropriate access rights to resources.** ACLs are essential tools in determining who has access to which resources within a network or system. Regularly reviewing and modifying the ACL settings ensures that users have the appropriate access rights, preventing unauthorized access and ensuring that authorized users can access the resources they need.

**Option A is incorrect.** While network load balancing is crucial, it is not directly related to ACLs. ACLs focus on access control, not traffic distribution.

**Option B is incorrect.** Firewall rules are different from ACLs. While they can work together, firewall rules primarily focus on allowing or blocking network traffic, while ACLs determine access permissions to resources.

**Option D is incorrect.** While updating the organization’s password policy is a vital security measure, it is not related to ACLs, which control access to resources based on user or group permissions.

Question 447. TechWorld Corp is concerned about cybercriminals sending emails that appear to come from its domain. The company wants to implement a solution that would allow receiving emails to validate that an email claiming to come from TechWorld Corp’s domain indeed originates from an approved server. Which of the following should the company implement?

-   (A) SMTP authentication
-   (B) DKIM
-   (C) POP3 over SSL
-   (D) S/MIME

**Explanation 447. Correct Answer: B. DKIM.** DomainKeys Identified Mail (DKIM) is a method used to authenticate the origin and integrity of an email. With DKIM, a digital signature is added to the headers of outgoing emails. Receiving email servers then use this signature to validate the email by checking it against the sending domain’s public key, which is published in the DNS records.

**Option A is incorrect.** SMTP authentication ensures that users provide valid credentials before they can send emails through a server, but it doesn’t validate the domain of the sender to the receiver.

**Option C is incorrect.** POP3 over SSL (Secure Sockets Layer) is about securely retrieving email messages from a server. It doesn’t provide a way to authenticate the sender’s domain.

**Option D is incorrect.** S/MIME (Secure/Multipurpose Internet Mail Extensions) is used to encrypt and sign email messages. While it ensures the integrity and confidentiality of the email content, it does not validate the sender’s domain to the recipient.

Question 448. A cloud-based collaboration tool used by a company displays a warning to a user stating, “You are logged in two locations.” However, the user has only one active session on the workstation. What should be the primary concern for the security team?

-   (A) The user might be using multiple devices
-   (B) There’s a potential misconfiguration in the tool’s settings
-   (C) The collaboration team is facing an outage
-   (D) There might be unauthorized access to the account

**Explanation 448. Correct Answer: D. There might be unauthorized access to the account.** Warnings of concurrent sessions, especially when the user is certain they are using one device, are red flags for unauthorized access. The security team should investigate for signs of a breach.

**Option A is incorrect.** While users often use multiple devices, the scenario mentions the user has only one, making this option unlikely.

**Option B is incorrect.** While misconfigurations can cause various issues, they don't typically manifest as false concurrent sessions.

**Option C is incorrect.** An outage in the collaboration tool would not typically cause a false warning of multiple sessions.

Question 449. A company is looking for a cryptographic solution that provides an immutable and transparent record of transactions in a distributed ledger. Which of the following would BEST meet this?

-   (A) Symmetric key algorithm
-   (B) Public key infrastructure
-   (C) Blockchain
-   (D) Digital watermark

**Explanation 449. Correct Answer: C. Blockchain.** Blockchain is a decentralized and distributed ledger that provides an immutable record of transactions. Each block contains a list of transactions and is linked to the previous block, creating a chain. The transparency and immutability of blockchain make it especially suitable for applications where an irrefutable record is essential.

**Option A is incorrect.** Symmetric key algorithms are encryption methods where the same key is used for both encryption and decryption but don’t inherently provide an immutable record of transactions.

**Option B is incorrect.** Public key infrastructure (PKI) is used for digital certificates and keys distribution but doesn’t offer an immutable record of transactions.

**Option D is incorrect.** Digital watermarking embeds information into a digital signal, but it does not provide an immutable record of transactions.

Question 450. TechCorp is collaborating with SoftTech, a business partner. To streamline collaboration without managing multiple accounts, TechCorp wants its employees to use their existing credentials to access SoftTech’s online project management system. Which of the following approaches would BEST enable this functionality?

-   (A) TechCorp should create new accounts for its employees on SoftTech’s system
-   (B) SoftTech should allow anonymous access for TechCorp’s employees
-   (C) TechCorp should implement federation between its identity provider and SoftTech’s service provider
-   (D) SoftTech should reset all passwords and provide them to TechCorp’s employees

**Explanation 450. Correct Answer: TechCorp should implement federation between its identity provider and SoftTech’s service provider.** Federation allows two organizations to trust each other’s identity systems. TechCorp’s
