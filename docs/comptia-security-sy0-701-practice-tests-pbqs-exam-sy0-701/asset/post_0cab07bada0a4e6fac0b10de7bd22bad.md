
Explanation 570. **Correct Answer: C. Honeypot.** A honeypot is a security mechanism designed to lure attackers into interacting with a seemingly vulnerable system. Its primary purpose is not to block or prevent attacks but to log and study them. By analyzing the activities on the honeypot, security professionals can gain insights into the methods and motivations of the attackers.

**Option A is incorrect.** An Intrusion Detection System (IDS) is designed to detect malicious activities on a network and alert administrators. While it can identify threats, it doesn’t actively lure attackers.

**Option B is incorrect.** A firewall is designed to block or allow traffic based on specific rules. It doesn’t present itself as a vulnerable target to lure attackers.

**Option D is incorrect.** A VPN Concentrator is a device that provides remote access to a network over a secure connection. Its primary purpose is to ensure secure remote access, not as a decoy for attackers.

**Question 571.** A large financial organization wants to ensure that all employees understand the importance of cybersecurity and the role they play in safeguarding company assets. Which of the following managerial security controls will be MOST effective in achieving this?

- (A) Installing a firewall at the network perimeter
- (B) Regular security awareness training for employees
- (C) Deploying an Intrusion Detection System (IDS)
- (D) Encrypting all company data

Explanation 571. **Correct Answer: B. Regular security awareness training for employees.** Security awareness training is a managerial control aiming to educate employees about security risks and the necessary precautions they need to take. By regularly training employees, the organization ensures that all staff are aware of potential threats and their roles in cybersecurity.

**Option A is incorrect.** Installing a firewall is a technical control focused on preventing unauthorized access to or from a private network. While it protects the network, it doesn't directly educate employees about their roles in cybersecurity.

**Option C is incorrect.** Deploying an Intrusion Detection System (IDS) is a technical control. It monitors network traffic for suspicious activities but does not directly focus on educating employees.

**Option D is incorrect.** Encrypting company data is a technical control. While it ensures the confidentiality of data, it doesn't address the employees' knowledge or awareness regarding cybersecurity.

**Question 572.** You are an IT security professional for a large corporation. After receiving reports about some users being unable to access external websites, you decided to review the firewall logs. Which of the following would be a PRIMARY indicator in the logs that a rule is blocking authorized outbound traffic?

- (A) Multiple entries of the same external IP address being ALLOWED
- (B) Timestamps showing large gaps between entries
- (C) Entries showing DROP/REJECT action for outbound traffic to port 80 and 443
- (D) Logs showing inbound traffic from multiple unknown external IP addresses

Explanation 572. Correct Answer: C. Entries showing DROP/REJECT action for outbound traffic to port 80 and 443. Port 80 and 443 are standard ports for HTTP and HTTPS respectively, which are commonly used for accessing websites. If users are unable to access external websites, it would make sense to check for DROP or REJECT actions for these ports in the firewall logs.

Option A is incorrect. If an external IP address is being ALLOWED multiple times, it wouldn’t be the cause of users being unable to access websites.

Option B is incorrect. Large gaps between timestamps in logs can indicate various issues, but they aren’t a direct indicator of a specific rule blocking outbound traffic.

Option D is incorrect. While inbound traffic from unknown addresses might be of concern, it doesn't specifically indicate an outbound traffic rule blocking users from accessing websites.

**Question 573.** A digital forensics investigator has just concluded an investigation regarding a potential insider threat. Before presenting the findings to the organization’s board, which of the following should the investigator ensure about the forensic report?

- (A) The report includes technical jargon to showcase depth of the investigation
- (B) The report emphasizes the investigator's credentials and experience
- (C) The report provides a clear, concise summary of findings without unnecessary technical details
- (D) The report contains detailed logs of every action taken by the investigator

Explanation 573. Correct Answer: C. The report provides a clear, concise summary of findings without unnecessary technical details. A forensic report’s primary purpose is to convey the results of an investigation in a clear and understandable manner, especially to non-technical stakeholders. By avoiding unnecessary technical jargon and providing a concise summary, it ensures that the report’s findings are accessible to all intended readers.

**Option A is incorrect.** While the depth of an investigation is important, inundating a report with technical jargon can make it difficult for non-technical individuals, such as board members, to understand the findings.

**Option B is incorrect.** While the investigator’s credentials and experience might be important, they should not be the emphasis of the report. The focus should remain on the investigation’s findings and their implications.

**Option D is incorrect.** While maintaining a detailed log of every action taken is crucial for the investigator’s records and ensuring the integrity of the investigation, including every detail in the report can be overwhelming and detract from its main findings.

**Question 574.** The security team at WidgetCorp is trying to identify potential insider threats. They have set up a SIEM solution with a custom dashboard showing unusual activities. Which of the following dashboard views would be MOST effective for quickly identifying an employee uploading large amounts of data to an external cloud storage service?

- (A) Display of users who logged in during off-hours
- (B) Graph of highest network bandwidth users
- (C) List of most frequently used applications
- (D) Visualization of failed login attempts

Explanation 574. **Correct Answer: B. Graph of highest network bandwidth users.** When an employee uploads large amounts of data to an external service, it typically results in a significant spike in network bandwidth. Therefore, a dashboard that visually displays the highest network bandwidth users can quickly alert the security team to potential data exfiltration activities.

**Option A is incorrect.** While logging in during off-hours can be suspicious, it doesn’t directly correlate to data upload activities.

**Option C is incorrect.** A list of the most frequently used applications might help in determining the common tools used within the organization, but it doesn’t specifically point to data upload actions.

**Option D is incorrect.** Visualization of failed login attempts could show potential brute-force or unauthorized access attempts, but it doesn’t directly indicate data uploading activities.

**Question 575.** During a regular review of system logs, Alex, a security analyst, noticed an unusual pattern of network traffic originating from a single IP address. Instead of waiting for an automated system to flag this as suspicious, he decides to manually dive deeper into the data to identify any potential threats. What is Alex engaging in?

- (A) Incident management
- (B) Threat modeling
- (C) Threat hunting
- (D) Security monitoring

Explanation 575. **Correct Answer: C. Threat hunting.** Threat hunting is a proactive approach where security professionals or analysts actively and manually search for signs of malicious activities within their network or systems, especially those threats that haven’t been automatically detected by traditional security tools.

**Option A is incorrect.** Incident management refers to the process followed when managing and responding to a security incident. In this scenario, Alex is taking a proactive approach to find potential threats, not responding to an identified incident.

**Option B is incorrect.** Threat modeling involves identifying potential threats and designing countermeasures to prevent or
