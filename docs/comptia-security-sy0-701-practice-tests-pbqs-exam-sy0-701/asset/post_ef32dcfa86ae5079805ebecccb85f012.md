
cloud-based database was accessible without a password. This is a common oversight when default configurations, which may have no password or a widely known default password, are left unchanged upon deployment.

**Option B is incorrect.** While network segmentation is crucial for security, the primary issue in this scenario is the database’s lack of password protection, not its network placement.

**Option C is incorrect.** Though encryption at rest is a best practice for data protection, the immediate issue here is unauthorized access due to a lack of password, not data exposure from the database’s stored data.

**Option D is incorrect.** An intrusion detection system (IDS) might have detected the unauthorized access sooner, but the core vulnerability was the unchanged default configurations.

**Question 340.** During a routine security review, a security analyst discovers multiple failed login attempts to a secure server room’s electronic access control system, all within a short time span. The access logs show a sequential pattern of access codes being tried. What type of physical attack is likely attempted?

- (A) Tailgating
- (B) Phishing
- (C) Brute force
- (D) Social engineering

**Explanation 340.** **Correct Answer: C. Brute force.** A brute force attack involves trying every possible combination in an attempt to find the correct one. The sequential pattern of access codes being tried in the logs suggests that the attacker is systematically going through all potential combinations.

**Option A is incorrect.** Tailgating involves an attacker following an authorized person into a secure area without the proper credentials. It doesn’t involve multiple electronic access code attempts.

**Option B is incorrect.** Phishing is a type of social engineering attack that typically involves tricking someone into divulging their credentials or other sensitive information. It doesn’t involve direct physical access attempts.

**Option D is incorrect.** While social engineering does involve manipulating individuals to gain unauthorized access, it is not specific to a brute force attack on an electronic system.

**Question 341.** A multinational e-commerce company is expanding its infrastructure to handle increasing traffic. The primary goal is to distribute the incoming web traffic across multiple servers to ensure that no single server is overwhelmed. Which method should the company use?

- (A) Deploy a web application firewall
- (B) Implement server clustering
- (C) Use hardware-based firewalls
- (D) Set up a load balancer

**Explanation 341.** **Correct Answer: D. Set up a load balancer.** Load balancers distribute incoming traffic across multiple servers to ensure no single server is overwhelmed, which enhances the availability and fault tolerance of applications.

**Option A is incorrect.** While a web application firewall can protect against web-based threats, it doesn’t distribute incoming traffic across servers.

**Option B is incorrect.** Server clustering primarily focuses on providing redundancy and failover capabilities rather than distributing incoming traffic.

**Option C is incorrect.** Hardware-based firewalls are primarily used to filter traffic and protect networks from external threats, not to distribute incoming web traffic.

**Question 342.** Alice needs to provide proof of the authenticity of a digital document she’s sending to Bob. Which of the following cryptographic elements should Alice use to accomplish this task and ensure Bob knows the document came from her?

- (A) Encrypt the document with Bob's private key
- (B) Encrypt the document with her public key
- (C) Sign the document with her private key
- (D) Sign the document with Bob's public key

**Explanation 342.** **Correct Answer: C. Sign the document with her private key.** To prove authenticity, a digital signature is created using the sender’s private key. When Bob receives the document, he can verify the signature using Alice’s public key. This proves that the document was signed by Alice and has not been tampered with during transit.

**Option A is incorrect.** Bob’s private key is known only to Bob and should never be used by anyone else, including for encryption.

**Option B is incorrect.** Encrypting with Alice’s public key doesn’t prove authenticity. It would also mean Alice’s private key could decrypt it, which isn’t the intent.

**Option D is incorrect.** One does not sign documents with the recipient’s public key. Signatures are created using the sender’s private key.

**Question 343.** Sarah, a cybersecurity analyst, receives a report that a company laptop was stolen from an employee’s car. The laptop contained sensitive financial data. Sarah checked the company’s security configurations and found that the laptop was equipped with full-disk encryption. How does this impact the potential data breach situation?

- (A) The data remains easily accessible, as only the boot sector was encrypted
- (B) The data is protected, as the entire hard drive’s contents are encrypted
- (C) The data is partially encrypted, with only the user directories protected
- (D) The data is vulnerable since full-disk encryption only applies when the laptop is connected to the company network

**Explanation 343. Correct Answer: B. The data is protected, as the entire hard drive’s contents are encrypted.** Full-disk Encryption (FDE) encrypts the entirety of a hard drive, ensuring that all its contents, including system and user files, are unreadable without the appropriate decryption key or credentials. As such, even if the laptop is stolen, the data remains secured unless the attacker has the decryption key.

**Option A is incorrect.** Full-disk Encryption does not encrypt only the boot sector; it encrypts the entire disk.

**Option C is incorrect.** Full-disk Encryption doesn’t only encrypt user directories; it encrypts the whole disk.

**Option D is incorrect.** Full-disk Encryption protects the data at all times, irrespective of the laptop’s connection to a network.

**Question 344.** A large news website was rendered unavailable during a major news event. Network logs show an overwhelming amount of traffic from IoT devices. Which type of DDoS attack leveraged IoT devices is this indicative of?

- (A) Reflected Attack
- (B) Botnet Attack
- (C) Amplification Attack
- (D) Teardrop Attack

**Explanation 344.** **Correct Answer: B. Botnet Attack.** Botnets, which are networks of compromised devices (including IoT devices), are often used to conduct large-scale DDoS attacks by directing the combined bandwidth of the devices towards a target.

**Option A is incorrect.** In a reflected attack, an attacker sends traffic to a third party, disguising it as if it came from the victim, which then reflects the traffic to the victim. It doesn’t primarily involve IoT devices.

**Option C is incorrect.** An amplification attack leverages vulnerable network services to amplify the amount of traffic sent to a victim. The primary focus isn’t the use of IoT devices.

**Option D is incorrect.** A teardrop attack involves sending mangled IP fragments with overlapping and oversized payloads to crash a target system. It doesn’t specifically utilize IoT devices.

**Question 345.** A security administrator needs to apply a configuration change to a critical service, requiring a service restart. Before initiating the restart, which of the following service is MOST important to ensure continuous service availability?

- (A) Implement automatic service restart on failure
- (B) Announce the restart to all company employees
- (C) Schedule the restart during off-peak hours
- (D) Take a backup of the current service configuration

**Explanation 345. Correct Answer: A. Implement automatic service restart on failure.** Having an automatic service restart on failure ensures that if any issues arise after applying the configuration change, the service will attempt to restart itself, ensuring minimal interruption to its availability.

**Option B is incorrect.** While notifying company employees is good practice, it doesn’t directly ensure continuous service availability.
