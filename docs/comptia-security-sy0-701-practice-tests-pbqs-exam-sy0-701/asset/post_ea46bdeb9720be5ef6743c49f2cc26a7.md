
emergency situation. It allows for an assessment of an incident response strategy without performing any actual tasks.

**Option A is incorrect.** A live fire exercise is a real-world test, often unannounced, and could impact actual operations.

**Option B is incorrect.** System hardening test focuses on making a system more secure against attacks and does not evaluate incident response.

**Option C is incorrect.** Red team/blue team exercises involve simulating real-world cyber attacks to test an organization’s defense and response capabilities, which is more hands-on than what is described.

**Question 505.** A company is attempting to verify the legitimacy of an email sent from a senior executive to a number of employees. The email requests the recipients to click on a link and enter their credentials for a “system upgrade.” The security team wants to ascertain if the email genuinely comes from the executive. Which of the following metadata from the email would be MOST beneficial in this investigation?

- (A) The email's subject line
- (B) The email's send time and date
- (C) The originating IP address in the email headers
- (D) The size of the email in bytes

**Explanation 505.** **Correct Answer: C. The originating IP address in the email headers.** Email headers often contain metadata about the originating IP address of the email. This can help investigators determine if the email was sent from an

**Explanation 506. Correct Answer: D. Integrity.** The integrity pillar of the CIA triad ensures the accuracy and reliability of data. By logging out users after a period of inactivity, the banking website aims to prevent unauthorized modifications (potentially by someone else who might gain access to the unattended session) to the user’s banking details, thereby maintaining the integrity of the data.

**Option A is incorrect.** While logging out users does have a confidentiality aspect, the primary aim in this scenario is to prevent unauthorized changes rather than unauthorized viewing.

**Option B is incorrect.** Availability ensures that data and systems are accessible to authorized users when they need it. This scenario doesn’t discuss providing or restricting access based on system uptime or accessibility.

**Option C is incorrect.** Authentication ensures that users are who they claim to be. While the scenario does touch on security measures, the primary concern here is preventing unauthorized changes to data, which aligns with integrity, not authentication

**Question 507.** An IT department in a large corporation spends several hours each day manually deploying patches and updates to thousands of workstations. Which of the following solutions would BEST enhance the efficiency of this process and save time for the IT team?

- (A) Disable automatic updates and conduct monthly patching sessions
- (B) Implement an automated patch management system
- (C) Design a dedicated team for patching that operates in shifts
- (D) Educate users to install updates on their own

**Explanation 507.** Correct Answer: Implement an automated patch management system. By implementing automated patch management system, the IT department can streamline the deployment of patches and updates across all workstations, ensuring consistency, reducing manual efforts, and saving valuable time.

**Option A is incorrect.** Disabling automatic updates and conducting monthly patching sessions does not address the inefficiency of manual patching and might expose the systems to vulnerabilities for a longer time.

**Option C is incorrect.** While designating a dedicated team might distribute the workload, it doesn’t eliminate the inefficiencies associated with manual patching.

**Option D is incorrect.** Relying on users to install updates introduces inconsistency, potential delays, and additional risks, as not all users might have the technical knowledge or remember to update regularly.

**Question 508.** Epsilon Inc. recently hired Jenny as a junior network administrator. To ensure security, they give Jenny only the access permissions necessary to complete her specific tasks, such as monitoring network traffic, but not modifying firewall rules. This approach of granting Jenny’s permissions aligns with which security principle?

- (A) Mandatory Access Control (MAC)
- (B) Role-Based Access Control (RBAC)
- (C) Time-of-Day Restrictions
- (D) Least Privilege

**Explanation 508.** **Correct Answer: D. Least Privilege.** The principle of Least Privilege dictates that users should be granted the minimum levels of access – or the least amount of privileges – necessary to complete their job functions. In Jenny’s case, she’s only granted the permissions necessary for her role, which aligns with this principle.

**Option A is incorrect.** MAC involves classifying information and matching user clearance levels to these classifications. Jenny’s access isn’t based on classifications.

**Option B is incorrect.** RBAC assigns permissions based on roles within an organization. While Jenny’s permissions may be aligned with her role, the scenario specifically emphasizes granting the minimal necessary access, which is a characteristic of Least Privilege.

**Option C is incorrect.** Time-of-Day Restrictions determine access based on the current time and have no direct relation to the principle of Least Privilege.

**Question 509.** As part of a cloud infrastructure project, AlphaTech plans to deploy multiple virtualized resources for his new application. The deployment includes databases, web servers, and load balancers. What is the PRIMARY benefit of using automation scripts in the resource provisioning process for this project?

- (A) It enables AlphaTech to use a single operating system for all resources
- (B) It guarantees 100% uptime for all virtualized resources
- (C) It ensures standardized, repeatable, and rapid deployments across the infrastructure
- (D) It prevents unauthorized users from accessing the cloud infrastructure

**Explanation 509.** Correct Answer: C. It ensures standardized, repeatable, and rapid deployments across the infrastructure. Automation in resource provisioning provides consistency in deployments, allowing for standardized configurations, rapid scaling, and the ability to repeat deployments without human error.

**Option A is incorrect.** While automation can deploy similar or environments, it does not inherently enforce a single operating system.

**Option B is incorrect.** Automation can increase efficiency and reduce human errors, but it cannot guarantee 100% uptime, as there are other factors involved, like hardware failures or network issues.

**Option D is incorrect.** While automation can implement security configurations, it does not, by itself, prevent unauthorized access. Security measures need to be designed and implemented.

**Question 510.** CyberSec Corp’s CISO wants to determine if there have been any anomalies in user behavior over the past month. Specifically, they’re concerned about unauthorized transfers outside of regular hours. Which of the following automated reports would be MOST useful in this investigation?

- (A) After-hours network activity reports
- (B) User password change frequency reports
- (C) Hardware inventory audit reports
- (D) Software licensing compliance reports

**Explanation 510.** **Correct Answer: A. After-hours network activity reports.** For the specific concern of unauthorized data transfers outside of regular hours, the after-hours network activity reports would be most useful. These reports would provide details on network activities, including data transfers, that took place outside typical working hours.

**Option B is incorrect.** While user password change frequency reports indicate if users are frequently changing passwords, which could be a sign of suspicious activity, it wouldn’t directly address the concern of data transfers outside of regular hours.

**Option C is incorrect.** Hardware inventory audit reports would provide information about the hardware assets of the company but wouldn’t give insights into data transfer activities.

**Option D is incorrect.** Software licensing compliance reports would detail the compliance status of software licenses, which isn’t relevant to the concern about unauthorized data transfers after hours.

**Question 511.** During a review of IDS logs, a security specialist notices a series of alerts indicating that a single external IP has been sending payloads that exploit a known vulnerability. However, the internal system to which these payloads are sent is patched and is not vulnerable to the exploit. Which of the following describes this type of IDS alert?

- (A) False positive
- (B) False negative
