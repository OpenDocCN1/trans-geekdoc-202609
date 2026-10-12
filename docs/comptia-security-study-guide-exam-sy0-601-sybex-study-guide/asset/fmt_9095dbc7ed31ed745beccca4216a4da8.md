
## Chapter 5: Security Assessment and Testing

### Questions 16-20

**16. D.** This is an example of an invoice scam. Most invoice scams involve sending fake invoices hoping to be paid. No information is being gathered, so this isn't reconnaissance or credential harvesting. This could be a hoax, but the more accurate answer is an invoice scam. Note that some social engineering uses false invoices to deploy malware by including it as an attachment or by using an attachment with malicious scripts built into a Microsoft Office file.

**17. B.** Smishing is a type of phishing that occurs via text (SMS) message.

**18. A.** Elicitation is the process of using casual conversation and subtle direction to gather information without the targets realizing they have disclosed details to that social engineer. Suggestion is not one of the terms used in the Security+ exam outline, pharming redirects traffic to malicious sites, and prepending can include a variety of techniques that add data or terms.

**19. D.** The caller was attempting to create a sense of urgency that would cause the help desk staff member to bypass normal procedures and let them set the board member's password to something that the social engineer would know. There is no implication of something scarce or that the caller is trying to get the help desk member to feel like others agree about the topic, thus using consensus. Familiarity takes more than using a board member's name or details about the company.

**20. B.** Spear phishing is aimed at specific groups. Whaling would target VIPs and executives, smishing uses SMS (text) messages, and vishing is done via voice or voicemail.

### Questions 1-20

**1. C.** Threat hunting is an assessment technique that makes an assumption of compromise and then searches the organization for indicators of compromise that confirm the assumption. Vulnerability scanning, penetration testing, and war driving are all assessment techniques that probe for vulnerabilities but do not assume that a compromise has already taken place.

**2. D.** Credentialed scans only require read-only access to target servers. Renee should follow the principle of least privilege and limit the access available to the scanner.

**3. C.** Ryan should first run his scan against a test environment to identify likely vulnerabilities and assess whether the scan itself might disrupt business activities.

**4. C.** An attack complexity of "low" indicates that exploiting the vulnerability does not require any specialized conditions.

**5. A.** A false positive error occurs when the vulnerability scanner reports a vulnerability that does not actually exist.

**6. B.** By allowing students to change their own grades, this vulnerability provides a pathway to unauthorized alteration of information. Brian should recommend that the school deploy integrity controls that prevent unauthorized modifications.

**7. C.** `Nmap` is a port scanning tool used to enumerate open network ports on a system. `Nessus` is a vulnerability scanner designed to detect security issues on a system. `Nslookup` is a DNS information gathering utility. All three of these tools may be used to gather information and detect vulnerabilities. `Metasploit` is an exploitation framework used to execute and attack and would be better suited for the Attacking and Exploiting phase of a penetration test.

**8. A.** This vulnerability is corrected by a patch that was released by Microsoft in 2017. A strong patch management program would have identified and remediated the missing patch.

**9. B.** Intrusion detection systems do not detect vulnerabilities; they detect attacks. The remaining three tools could all possibly discover a cross-site scripting (XSS) vulnerability, but a web application vulnerability scanner is the most likely to detect it because it is specifically designed to test web applications.

**10. A.** Moving from one compromised system to other systems on the same network is known as lateral movement. Privilege escalation attacks increase the level of access that an attacker has to an already compromised system. Footprinting and OSINT are reconnaissance techniques.

**11. A.** Offensive hacking is used by red teams as they attempt to gain access to systems on the target network. Blue teams are responsible for managing the organization's defenses. White teams serve as the neutral moderators of the exercise. Purple teaming is conducted after an exercise to bring together the red and blue teams for knowledge sharing.

**12. C.** Bug bounty programs are designed to allow external security experts to test systems and uncover previously unknown vulnerabilities. Bug bounty programs offer successful testers financial rewards to incentivize their participation.

**13. D.** Backdoors are a persistence tool, designed to make sure that the attacker's access persists after the original vulnerability is remediated. Kyle can use this backdoor to gain access to the system in the future, even if the original exploit that he used to gain access is no longer effective.

**14. C.** `WHOIS` lookups use external registries and are an example of open source intelligence (OSINT), which is a passive reconnaissance technique. Port scans, vulnerability scans, and footprinting all require active engagement with the target and are, therefore, active reconnaissance.

**15. B.** Common Vulnerabilities and Exposures (CVE) provides a standard nomenclature for describing security-related software flaws. Common Configuration Enumeration (CCE) provides a standard nomenclature for discussing system configuration issues. Common Platform Enumeration (CPE) provides a standard nomenclature for describing product names and versions. The Common Vulnerability Scoring System (CVSS) provides a standardized approach for measuring and describing the severity of security-related software flaws.

**16. C.** White-box tests are performed with full knowledge of the underlying technology, configurations, and settings that make up the target. Black-box tests are intended to replicate what an attacker would encounter. Testers are not provided with access to or information about an environment, and instead, they must gather information, discover vulnerabilities, and make their way through an infrastructure or systems like an attacker would. Gray-box tests are a blend of black-box and white-box testing. Blue-box tests are not a type of penetration test.

**17. C.** The rules of engagement provide technical details on the parameters of the test. This level of detail would not normally be found in a contract or statement of work. The lessons learned report is not produced until after the test.

**18. B.** All of these techniques might provide Grace with information about the operating system running on a device. However, footprinting is a technique specifically designed to elicit this information.

**19. B.** Vulnerabilities with CVSS base scores between 4.0 and 6.9 fit into the medium risk category.

**20. C.** The privileges required (PR) metric indicates the type of system access that an attacker must have to execute the attack.

## Chapter 6: Secure Coding

### Questions 1-2

**1. B.** Adam is conducting static code analysis by reviewing the source code. Dynamic code analysis requires running the program, and both mutation testing and fuzzing are types of dynamic analysis.

**2. C.** Charles should perform user input validation to strip out any SQL code or other unwanted input. Secure session management can help prevent session hijacking, logging may provide useful information for incident investigation, and implementing TLS can help protect network traffic, but only input validation helps with the issue described.
