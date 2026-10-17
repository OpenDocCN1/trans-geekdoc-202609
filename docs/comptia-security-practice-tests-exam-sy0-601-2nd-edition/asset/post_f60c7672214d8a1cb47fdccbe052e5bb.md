
- **C.** Data masking
- **D.** Data washing

**117.** Which of the following is the most common reason to include a privacy notice on a website?

- **A.** To warn attackers about security measures
- **B.** To avoid lawsuits
- **C.** Due to regulations or laws
- **D.** None of the above

**118.** Nicole determines how her organization processes data that it collects about its customers and also decides how and why personal information should be processed. What role does Nicole play in her organization?

- **A.** Data steward
- **B.** Data custodian
- **C.** Data controller
- **D.** Data consumer

**119.** The virtual machine cluster that Pat is in charge of has suffered a major failure in its primary controller. The entire organization is offline, and customers cannot get to the organization’s website which is its primary business. What type of disaster has Pat’s organization experienced?

- **A.** An MRO disaster
- **B.** An internal disaster
- **C.** An RTO disaster
- **D.** An external disaster

**120.** What important step should be taken early in the information life cycle to ensure that organizations can handle the data they collect?

- **A.** Data retention
- **B.** Data classification
- **C.** Data minimization
- **D.** Data exfiltration

**121.** Kirk’s organization has been experiencing large-scale denial-of-service (DoS) attacks against their primary website. Kirk contracts with his Internet service provider to increase the organization’s bandwidth and expands the server pool for the website to handle significantly more traffic than any of the previous DoS attacks. What type of risk management strategy has he employed?

- **A.** Acceptance
- **B.** Avoidance
- **C.** Transfer
- **D.** Mitigation

**122.** The co-location facility that Joanna contracts to host her organization’s servers is in a flood plain in a hurricane zone. What type of risk best describes the risk that Joanna and other customers face?

- **A.** A multiparty risk
- **B.** An internal risk
- **C.** A legacy risk
- **D.** An IP theft risk

**123.** The cloud service that Natasha’s organization has used for the past five years will no longer be available. What phase of the vendor relationship should Natasha plan for with this service?

- **A.** Preparing a service MOU
- **B.** An EOL transition process
- **C.** Creating an NDA
- **D.** A last will and testament

**124.** Gary wants to use a secure configuration benchmark for his organization for Linux. Which of the following organizations would provide a useful, commonly adopted benchmark that he could use?

- **A.** Microsoft
- **B.** NIST
- **C.** CIS
- **D.** All of the above

**125.** After Angela left her last organization, she discovered that she still had access to her shared drives and could log in to her email account. What critical process was likely forgotten when she left?

- **A.** An exit interview
- **B.** Job rotation
- **C.** Offboarding
- **D.** Governance

**126.** Frank knows that businesses can use any classification labels they want, but he also knows that there are a number of common labels in use. Which of the following is not a common data classification label for businesses?

- **A.** Public
- **B.** Sensitive
- **C.** Private
- **D.** Secret

**127.** Where are privacy notices frequently found?

- A. The terms of an agreement for customers
- B. A click-through license agreement
- C. A website usage agreement
- D. All of the above

## Appendix

### Answers and Explanations

![](img/a9d117a1cc3b6e0dee61fc3cc6c7b63e_210_0.png)

## Chapter 1: Threats, Attacks, and Vulnerabilities

- 1. **C.** The correct answer is spear phishing. Spear phishing is targeted to a specific group, in this case insurance professionals. Although this is a form of phishing, the more specific answer is the one you will need to choose on questions like this. Phishing uses social engineering techniques to succeed but is once again a broader answer than spear phishing and thus is not the correct choice. Finally, a Trojan horse pretends to be a legitimate or desirable program or file, which this scenario doesn’t describe.

- 2. **B.** A logic bomb is malware that performs its malicious activity when some condition is met. A worm is malware that self-propagates. A Trojan horse is malware attached to a legitimate program, and a rootkit is malware that gets root or administrative privileges.

- 3. **C.** This is a very basic form of SQL injection. Cross-site scripting would have JavaScript in the text field and would be designed to impact other sites from a user’s session. Cross-site request forgery would not involve any text being entered in the web page, and ARP poisoning is altering the ARP table in a switch; it is not related to website hacking.

- 4. **B.** This describes a jamming attack, where legitimate traffic is interfered with by another signal. Jamming can be intentional or unintentional and may be intermittent. IV attacks are obscure cryptographic attacks on stream ciphers. Wi-Fi protected setup (WPS) uses a PIN to connect to the wireless access point (WAP). The WPS attack attempts to intercept that PIN in transmission, connect to the WAP, and then steal the WPA2 password. A botnet is a group of machines that are being used, without their consent, as part of an attack.

- 5. **B.** The best option listed to defend against the attacks mentioned is input validation. Encrypting the web traffic will not have any effect on these two attacks. A web application firewall (WAF) might mitigate these attacks, but it would be secondary to input validation, and an intrusion detection system (IDS) will simply detect the attack—it won’t stop it.

- 6. **C.** If users have been connecting but the AP does not show them connecting, then they have been connecting to a rogue access point. This could be the cause of an architecture and design weakness such as a network without segmentation and control of devices connecting to the network. Session hijacking involves taking over an already authenticated session. Most session hijacking attacks involve impersonation. The attacker attempts to gain access to another user’s session by posing as that user. Clickjacking involves causing visitors to a website to click on the wrong item. Finally, bluejacking is a Bluetooth attack.

- 7. **C.** Cross-site scripting involves entering a script into text areas that other users will view. SQL injection is not about entering scripts, but rather SQL commands. Clickjacking is about tricking users into clicking on the wrong thing. Bluejacking is a Bluetooth attack.

- 8. **D.** Retaining the actual password is not a best practice, and thus encrypting password plain text is not a common technique to make passwords harder to crack. Since the application would need the cryptographic key to read the passwords, anybody who had access to that key could decrypt the passwords. Using a salt, a pepper, and a cryptographic hashing algorithm designed for passwords are all common best practices to prevent offline brute-force attacks.

management (SIEM) and doesn’t specifically help with this need. Both sentiment analysis and user behavior analysis are aimed at users and groups rather than at how data is collected and managed.

- 16. **B.** White teams act as judges and observers during cybersecurity exercises. Blue teams act as defenders, red teams act as attackers, and purple teams are composed of both blue and red team members to combine attack and defense knowledge to improve organizational security.

- 17. **A.** The simplest way to ensure that APIs are only used by legitimate users is to require the use of authentication. API keys are one of the most frequently used methods for this. If an API key is lost or stolen, the key can be invalidated and reissued, and since API keys can be matched to usage, Cynthia’s company can also bill customers based on their usage patterns if they want to. A firewall or IP restrictions may be able to help, but they can be fragile; customer IP addresses may change. An intrusion prevention system (IPS) can detect and prevent attacks, but legitimate usage would be hard to tell from those who are not customers using an IPS.

- 18. **B.** Buffer overflow attacks cram more data into a field or buffer than they can accept, overflowing into other memory locations and either crashing the system or application, or potentially allowing code to be inserted into executable locations. Bluesnarfing and bluejacking are both Bluetooth attacks. Cross-site scripting attacks allow attackers to inject scripts into pages viewed by other users.

- 19. **A.** Attackers are attempting to influence Gurvinder with a combination of scarcity and urgency. Thus, for this question you should answer scarcity since urgency is not listed. In many social engineering principle questions, more than one of the principles may be in play, and you will need to answer with the principle that is correct or more correct for the question. In this case, there is no intimidation or claim to authority, and consensus would require some form of validation from others.

- 20. **A.** Vulnerability scans use automated tools to look for known vulnerabilities in systems and applications and then provide reports to assist in remediation activities. Penetration tests seek to actually exploit the vulnerabilities and break into systems. Security audits usually focus on checking policies, incident reports, and other documents. Security test is a generic term for any sort of test.

- 21. **C.** Username complexity has no impact in credential harvesting. Multifactor authentication can help prevent successful credential harvesting by ensuring that even capture of username and password is not enough to compromise the account. Awareness training helps to reduce the likelihood of credential exposure, and limiting or preventing use of third-party web scripts makes websites less likely to have credentials stolen through the use of those scripts, plug-ins, or modules.

- 22. **C.** Greg can clone a legitimate Media Access Control (MAC) address if he can identify one on the network. This can be as easy as checking for a MAC label on some devices or by capturing traffic on the network if he can physically access it.

- 23. **A.** From the description it appears that they are not connecting to the real web server but rather a fake server. That indicates typo squatting: have a URL that is named very similarly to a real site so that when users mistype the real site’s URL they will go to the fake site.
