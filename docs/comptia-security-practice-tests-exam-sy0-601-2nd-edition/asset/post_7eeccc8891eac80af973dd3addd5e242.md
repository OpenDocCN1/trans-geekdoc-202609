
- C. A snapshot of the VM using the underlying virtualization environment
- D. All of the above

**112.** James has a PCAP file that he saved while conducting an incident response exercise. He wants to determine if his intrusion prevention system (IPS) could detect the attack after configuring new detection rules. What tool will help him use the PCAP file for his testing?

- A. `hping`
- B. `tcpreplay`
- C. `tcpdump`
- D. Cuckoo

**113.** What type of file is created when Windows experiences a blue screen of death?

- A. A security log
- B. A blue log
- C. A dump file
- D. A tcpdump

**114.** Ed wants to ensure that a compromise on his network does not spread to parts of the network with different security levels. What mitigation technique should he use prior to the attack to help with this?

- A. Isolation
- B. Fragmentation
- C. Tiering
- D. Segmentation

**115.** Derek has acquired over 20 hard drives as part of a forensic investigation. What key process is important to ensure that each drive is tracked and managed properly over time?

- A. Tagging the drives
- B. Taking pictures of each drive
- C. Labeling each drive with its order of volatility
- D. Interviewing each person whose drive is imaged

**116.** What term describes the ownership, custody, and acquisition of digital forensic artifacts and images?

- A. E-discovery
- B. Provenance
- C. Jurisdiction
- D. Volatility

**117.** Elle wants to acquire the live memory (RAM) from a machine that is currently turned on. Which of the following tools is best suited to acquiring the contents of the system’s memory?

- A. Autopsy
- B. The Volatility framework
- C. `dd`
- D. `netcat`

**118.** Randy believes that a misconfigured firewall is blocking traffic sent from some systems in his network to his web server. He knows that the traffic should be coming in as HTTPS to his web server, and he wants to check to make sure the traffic is received. What tool can he use to test his theory?

- A. `tracert`
- B. `Sn1per`
- C. `traceroute`
- D. Wireshark

**119.** Ryan wants to implement a flexible and reliable remote logging environment for his Linux systems. Which of the following tools is least suited to that requirement?

- A. `rsyslog`
- B. `syslog`
- C. NXLog
- D. `syslog-ng`

**120.** Susan has been reading about a newly discovered exploit, and wants to test her IPS rules to see if the sample code will work. In order to use the exploit, she needs to send a specifically crafted UDP packet to a DHCP server. What tool can she use to craft and send this test exploit to see if it is detected?

- A. `hping`
- B. `scanless`
- C. `curl`
- D. `pathping`

**121.** Valerie wants to check to see if a SQL injection attack occurred against her web application on a Linux system. Which log file should she check for this type of information?

- A. The security log
- B. The DNS log
- C. The auth log
- D. The web server log

**122.** Olivia’s company has experienced a breach and believes that the attackers were able to access the company’s web servers. There is evidence that the private keys for the certificates for the server were exposed and that the passphrases for the certificates were kept in the same directory. What action should Olivia take to handle this issue?

- A. Revoke the certificates.
- B. Change the certificate password.
- C. Change the private key for the certificate.
- D. Change the public key for the certificate.

**123.** Jean’s company is preparing for litigation with another company that they believe has caused harm to Jean’s organization. What type of legal action should Jean’s lawyer take to ensure that the company preserves files and information related to the legal case?

- A. A chain of custody demand letter
- B. An e-discovery notice
- C. A legal hold notice
- D. An order of volatility

**124.** Cynthia wants to display all of the active connections on a Windows system. What command can she run to do so?

- A. `route`
- B. `netstat -a`
- C. `netstat -c`
- D. `hping`

**125.** What type of mitigation places a malicious file or application in a safe location for future review or study?

- A. Containment
- B. Quarantine
- C. Isolation
- D. Deletion

**126.** What location is commonly used for Linux swap space?

- A. `\root\swap`
- B. `\etc\swap`
- C. `\proc\swap`
- D. A separate partition

**127.** Marco is conducting a forensic investigation and is preparing to pull eight different storage devices from computers that he will analyze. What should he use to track the drives as he works with them?

- A. Tags with system, serial number, and other information
- B. MD5 checksums of the drives

**133.** Which of the following is not information that can be gathered from a system by running the `arp` command?

- A. The IP address of the local system
- B. The MAC addresses of recently resolved external hosts
- C. Whether the IP address is dynamic or static
- D. The MAC addresses of recently resolved local hosts

**134.** What log will `journalctl` provide Selah access to?

- A. The event log
- B. The auth log
- C. The systemd journal
- D. The authentication journal

**135.** What phase of the incident response process often involves adding firewall rules and patching systems to address the incident?

- A. Preparation
- B. Eradication
- C. Recovery
- D. Containment

**136.** Gary wants to use a tool that will allow him to download files via HTTP and HTTPS, SFTP, and TFTP from within the same script. Which command-line tool should he pick from the following list?

- A. `curl`
- B. `hping`
- C. `theHarvester`
- D. `nmap`

**137.** Tim wants to check the status of malware infections in his organization using the organization's security information and event management (SIEM) device. What SIEM dashboard will tell him about whether there are more malware infections in the past few days than normal?

- A. The alerts dashboard
- B. The sensors dashboard
- C. The trends dashboard
- D. The bandwidth dashboard

**138.** Warren is gathering information about an incident and wants to follow up on a report from an end user. What digital forensic technique is often used when end users are a key part of the initial incident report?

- A. Email forensics
- B. Interviews
- C. Disk forensics
- D. Chain of custody

**139.** Aaron wants to use a multiplatform logging tool that supports both Windows and Unix/Linux systems and many log formats. Which of the following tools should he use to ensure that his logging environment can accept and process these logs?

- A. IPFIX
- B. NXLog
- C. `syslog`
- D. `journalctl`

**140.** Which of the following is not a common type of incident response exercise?

- A. Drills
- B. Simulations
- C. Tabletop
- D. Walk-throughs

**141.** Susan needs to run a port scan of a network. Which of the following tools would not allow her to perform that type of scan?

- A. `netstat`
- B. `netcat`
- C. `nmap`
- D. Nessus

**142.** What term belongs at point A on the Diamond Model of Intrusion Analysis shown below?

![](img/a9d117a1cc3b6e0dee61fc3cc6c7b63e_181_0.png)

**6.** What standard is used for credit card security?

- A. GDPR
- B. COPPA
- C. PCI-DSS
- D. CIS

**7.** You are a security manager for your company and need to reduce the risk of employees working in collusion to embezzle funds. Which of the following policies would you implement?

- A. Mandatory vacations
- B. Clean desk
- C. NDA
- D. Continuing education

**8.** After your company implemented a clean desk policy, you have been asked to secure physical documents every night. Which of the following would be the best solution?

- A. Department door lock
- B. Locking cabinets and drawers at each desk
- C. Proximity cards
- D. Onboarding

**9.** Which of the following techniques attempts to predict the likelihood a threat will occur and assigns monetary values should a loss occur?

- A. Change management
- B. Vulnerability assessment
- C. Qualitative risk assessment
- D. Quantitative risk assessment

**10.** Which of the following agreements is less formal than a traditional contract but still has a certain level of importance to all parties involved?

- A. SLA
- B. BPA
- C. ISA
- D. MOU

**11.** As part of the response to a credit card breach, Sally discovers evidence that individuals in her organization were actively working to steal credit card information and personally identifiable information (PII). She calls the police to engage them for the investigation. What has she done?

- A. Escalated the investigation
- B. Public notification
