
**Option A is incorrect.** A Web Application Firewall (WAF) is used to protect web applications by filtering and monitoring HTTP traffic. It does not handle data transfers to external storage or cloud storage specifically.

**Option B is incorrect.** A Data Encryption Tool encrypts data to protect it from unauthorized access. While it adds a layer of security, it doesn’t prevent the transfer of data to external devices or cloud storage.

**Option D is incorrect.** A Virtual Private Network (VPN) provides a secure tunnel for data transmission between two endpoints. It does not prevent or monitor the type of data being transferred.

**Question 469.** An online banking platform wants to improve its customer verification process when users open a new account. Which of the following identity proofing methods would be the MOST secure for this purpose?

- (A) Asking users to select a security question and answer from a list
- (B) Requiring users to upload a photo of a government-issued ID and a selfie
- (C) Sending a verification code to the user's email address
- (D) Prompting users to provide their favorite color

**Explanation 469.** **Correct Answer: B. Requiring users to upload a photo of a government-issued ID and a selfie.** This method provides a high level of assurance by comparing the user’s live image (selfie) with a government-issued ID. The combination ensures the person is who they claim to be.

**Option A is incorrect.** While digital signatures can validate the authenticity and integrity of a message or document, they do not provide a decentralized ledger of assets over time.

**Option B is incorrect.** Key escrow is a method where cryptographic keys are held in trust so that a third party can have access under certain conditions. It doesn’t help in validating the integrity and authenticity of assets over time without central authority.

**Option D is incorrect.** A key management system manages the life cycle of cryptographic keys but does not inherently validate the integrity and authenticity of assets over time.

**Question 471.** After a recent cyber attack on a corporation’s central database, the IT department has been tasked with enhancing the security of their network infrastructure. Which of the following would be the BEST technique to ensure that different departments, like HR and Finance, cannot access each other’s sensitive data?

- (A) Implement network segmentation based on departments
- (B) Upgrade the bandwidth of the entire network
- (C) Use a single strong password for all departments
- (D) Move all department data to the cloud

**Explanation 471.** **Correct Answer: A. Implement network segmentation based on departments.** Network segmentation divides a network into multiple segments or subnets, each acting as its own small network. This limits access between segments and can protect sensitive data by ensuring that only those within a segment can access its resources.

**Option B is incorrect.** While upgrading the bandwidth may improve network speeds, it does not address the security concern of segregating departmental data.

**Option C is incorrect.** Using a single strong password for all departments does not prevent one department from accessing another’s data. It also introduces a single point of failure.

**Option D is incorrect.** Moving data to the cloud can offer some security benefits, but without proper access controls and segmentation, different departments could still access each other’s data.

**Question 472.** A finance department employee, Maya, is transferred to the HR department. The IT department is considering her access requirements. Which of the following actions aligns best with the principle of least privilege?

- (A) Retain Maya’s access to the finance system and grant additional access to the HR system
- (B) Remove all previous access rights and provide her access solely to the HR system
- (C) Grant Maya administrative rights to ease her transition between departments
- (D) Limit Maya’s access to read-only for both finance and HR systems for a transitional period

**Explanation 472.** Correct Answer: B. Remove all previous access rights and provide her access solely to the HR system.

When an employee transitions from one department to another, their access requirements change. To uphold the principle of least privilege, it’s essential to re-evaluate and adjust access rights Maya no longer requires access to the finance system and should only have access to the resources necessary for her new role in HR.

**Option A is incorrect.** Retaining access to the finance system when Maya no longer works in that department is unnecessary and could be a security risk.

**Option C is incorrect.** Granting administrative rights excessive and would provide Maya with more access than necessary for her new role.

**Option D is incorrect.** While read-only access limits potential damage, providing access to both systems is unnecessary if Maya’s new role only requires access to the HR system.

**Question 473.** A financial institution, BankCorp, has recently experienced a surge in phishing attacks targeting its employees. These attacks often involve URLs that look similar to legitimate ones but have slight variations. To reduce the risk of employees accidentally accessing these malicious sites, which measure should BankCorp implement?

- (A) Implement a Domain Name System (DNS) firewall
- (B) Employ URL scanning to identify and block malicious URLs
- (C) Rely on manual reporting of suspicious URLs by employees
- (D) Use a Virtual Private Network (VPN) to redirect employee web traffic

**Explanation 473.** Correct Answer: B. Employ URL scanning to identify and block malicious URLs. URL scanning can identify potentially malicious sites by examining the complete URL and comparing it with known malicious URLs or patterns. This method can block access to URLs that are designed to look similar to legitimate ones.

**Option A is incorrect.** While a DNS firewall can help access to malicious domains, URL scanning provides more granular control by examining the full URL, not just the domain.

**Option C is incorrect.** Relying solely on manual reporting by employees may not be efficient or effective as an automated URL scanning. It would also place undue responsibility on employees to recognize every malicious URL.

**Option D is incorrect.** Using a VPN simply changes the route of the traffic and provides encrypted communication. It does not inherently offer URL scanning capabilities.

**Question 474.** The IT team at a manufacturing company is deploying an IoT-based monitoring system for their machinery. They want to ensure that these IoT devices, if compromised, cannot adversely affect their main corporate network. What should they implement to achieve this?

- (A) Install antivirus software on all IoT devices
- (B) Regularly patch and update the IoT device firmware
- (C) Place the IoT devices on a dedicated VLAN
- (D) Enable multi-factor authentication for IoT devices

**Explanation 474.** Correct Answer: C. Place the IoT devices on a dedicated VLAN. Placing the IoT devices on a dedicated VLAN (Virtual Local Area Network) provides network isolation, ensuring that the devices are segregated from the main corporate network. This strategy ensures that if an IoT device is compromised, it doesn’t pose a direct threat to the corporate network systems.

**Option A is incorrect.** Many IoT devices may not support traditional antivirus software, and even if they do, this doesn’t achieve the network isolation desired.

**Option B is incorrect.** While regularly patching and updating device firmware is crucial for security, it doesn’t provide network isolation from the main corporate network.

**Option D is incorrect.** Enabling multi-factor authentication can enhance the security of devices but doesn’t provide the network isolation specified in the scenario.

**Question 475.** The content filtering logs at a retail company display multiple instances of “.exe” blocked access to a file download URL ending with “.exe”. The source IP address belongs to a point of sale (POS) terminal. What should be the primary concern for the security team?

- (A) The POS terminal might have outdated software
- (B) There’s a possible misconfiguration in the content filtering rules
- (C) The POS terminal might be compromised and trying to download malicious executables
- (D) The company’s internet speed is too slow
