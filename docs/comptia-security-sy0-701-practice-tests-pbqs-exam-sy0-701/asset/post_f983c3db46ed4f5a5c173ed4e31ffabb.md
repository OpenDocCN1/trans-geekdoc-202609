
Option A is incorrect. RSA is an asymmetric encryption method, not a key exchange protocol.

Option B is incorrect. HMAC is a specific type of message authentication code that involves hashing and is not used for key exchange.

Option D is incorrect. AES is a symmetric encryption algorithm and does not offer a key exchange mechanism.

Question 426. A company plans to upgrade its email server to ensure that email transmission between their mail server and client applications is encrypted. Which of the following protocols would be the most appropriate for this purpose?

- (A) HTTP
- (B) FTP
- (C) IMAP over SSL/TLS
- (D) SNMP

Explanation 426. Correct Answer: C. IMAP over SSL/TLS.
IMAP over SSL/TLS (commonly known as IMAPS) is a protocol used by mail clients to retrieve messages from a mail server over a secure channel. The use of SSL/TLS provides encryption for the transmitted data, ensuring confidentiality of the email transmission.

Option A is incorrect. HTTP is a protocol for transferring web content and does not provide encryption by default. Furthermore, it’s not designed for email transmission.

Option B is incorrect. FTP is a protocol for transferring files and does not provide secure email transmission capabilities.

Option C is incorrect. SNMP (Simple Network Management Protocol) is used for network management and monitoring, not for email transmission.

Question 427. A medium-sized company has just deployed a new file server for the HR department. They want to ensure that only HR employees can view and edit HR-specific documents, while the IT department should only be able to perform system maintenance tasks. What should the company implement to achieve this requirement?

- (A) Install a firewall between the HR and IT departments
- (B) Implement an Access Control List (ACL) for the file server
- (C) Enforce a strong password policy for the HR department
- (D) Enable full disk encryption on the file server

Explanation 427. Correct Answer: B. Implement an Access Control List (ACL) for the file server. Access Control Lists (ACLs) define who can access a resource and what they can do with it once accessed. By setting up an ACL for the file server, the company can precisely define the permissions for HR and IT departments, ensuring that only authorized users have the right level of access to the data.

Option A is incorrect. Installing a firewall would limit network traffic between departments but would not provide granular access control to files on the server.

Option C is incorrect. While a strong password policy is essential for security, it doesn’t differentiate access between HR and IT or control what users can do once they access the server.

Option D is incorrect. Full disk encryption protects data at rest, but it does not provide differentiated access to specific files or directories based on user roles.

## Question 428. Carla, a security analyst, receives an alert that one of the company’s server certificates may have been exposed in a recent data breach. What is the most immediate action Carla should take to ensure that the exposed certificate cannot be used maliciously?

- (A) Request a new certificate from the CA
- (B) Update the company firewall rules
- (C) Add the certificate to the Certificate revocation list (CRL)
- (D) Perform a vulnerability assessment on the server

Explanation 428. Correct Answer: C. Add the certificate to the Certificate revocation list (CRL). If a certificate is believed to be compromised, the most immediate action is to revoke it. This is done by adding the certificate to the Certificate revocation list (CRL). Systems and applications that check the CRL before establishing secure communications will then know not to trust the compromised certificate.

Option A is incorrect. While requesting a new certificate may be necessary after revoking the compromised one, the immediate action should be revoking the potentially compromised certificate.

Option B is incorrect. Updating firewall rules, while essential for many security scenarios, doesn’t directly address the misuse of a potentially exposed certificate.

Option D is incorrect. A vulnerability assessment is a broader action to identify weaknesses in the system. While valuable, it doesn’t directly address the issue of the compromised certificate.

Question 429. DataFin, a financial analytics firm, experienced a minor fire incident in one of its server rooms. Fortunately, they had backups stored in another wing of the building, allowing for quick data recovery. However, management realizes that in a major disaster, both primary and backup data might be destroyed. To address this, which backup strategy should DataFin consider?

- (A) Mirror Backup
- (B) Local Storage Backup
- (C) Incremental Backup
- (D) Offsite Backup

Explanation 429. Correct Answer: D. Offsite Backup. Offsite Backup involves storing backup data in a different geographical location from the primary data. This ensures that even if a disaster impacts the primary location, the backup remains safe and can be used for recovery.

Option A is incorrect. Mirror Backup refers to a backup that is an exact copy of the source data. It doesn’t specify the geographic location of the backup.

Option B is incorrect. Local Storage Backup typically means backups are stored within the same physical premises or close vicinity of the primary data, which wouldn’t address DataFin’s concern of potential data loss in a major disaster.

Option C is incorrect. Incremental Backup involves backing up only the data that has changed since the last backup, regardless of where it’s stored. It doesn’t address the concern of geographic separation.

Question 430. An online retailer is considering various methods to protect its customers’ credit card information. Instead of storing the actual credit card numbers in their database, they opt for a solution that replaces the numbers with unrelated, random values. What is this method?

- (A) Symmetric encryption
- (B) Digital watermarking
- (C) Hashing
- (D) Tokenization

Explanation 430. Correct Answer: D. Tokenization.
Tokenization is a method where sensitive data is replaced with non-sensitive substitutes, referred to as “tokens”. These tokens act as references to the original data but don’t contain the sensitive data, making it a preferred method for protecting credit card information in many retail environments.

Option A is incorrect. Symmetric encryption is a method of encrypting data using a single key for both and decryption. It changes the original data into a ciphered format but doesn’t replace it with random values as tokenization does.

Option B is incorrect. Digital watermarking embeds data into a digital signal, primarily for asserting rights or ownership and not for replacing sensitive data with random values.

Option C is incorrect. Hashing converts input data into a fixed-length string of characters, which is typically a hash code. It doesn’t produce a random value that can be used as a reference back to the original data.

Question 431. The IT team at TechnoCorp has noticed a consistent pattern over the last week where a particular server’s CPU usage spikes to 100% between 2:00 AM and 4:00 AM, a time when there’s typically minimal user activity. What could be the MOST probable reason for this?

- (A) The server is automatically updating its software
- (B) An employee is running a heavy computational task
- (C) The server is undergoing a DDoS attack
- (D) Malware is performing cryptomining activities

Explanation 431. Correct Answer: D. Malware performing cryptomining activities. Cryptomining malware often causes significant resource consumption, especially CPU usage. Attackers frequently schedule such activities during off-peak hours to reduce the chance of detection. Given the consistent pattern of high CPU usage during off-hours, cryptomining malware is a probable cause.

Option A is incorrect. While software updates can cause resource consumption, they typically don’t result in consistent, prolonged 100% CPU usage over multiple days.
