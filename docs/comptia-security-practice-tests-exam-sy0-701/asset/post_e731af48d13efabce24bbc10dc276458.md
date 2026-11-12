
186. Laura wants to harden an ICS and SCADA devices her organization uses to manage critical infrastructure. The devices are old and unsupported, without recent updates. What hardening techniques are most likely to be available to her to help deal with these devices?
- A. Isolation
- B. Segmentation
- C. Adding host-based firewalls
- D. Configuring host-based IPS

187. Bob uses an IoC feed to allow his SIEM to identify and correlate common malicious activity. What phase of the incident response process best describes this?
- A. Preparation
- B. Detection
- C. Containment
- D. Eradication

188. Yael's organization has received a very convincing phishing email that has resulted in staff clicking on a malicious link. If Yael can't remove the email from inboxes, which of the following options will allow her to quickly prevent users from being compromised?
- A. Set up DNS filtering using the URL from the email.
- B. Disable the organization's Internet connection.
- C. Block inbound traffic from the phishing email's source IP.
- D. Enable reputation services for the email.

189. Nick is reviewing his system configurations and notes that logon event auditing settings on the system are set as shown in the example figure. What concern should he express about the setting?

![](img/6235ce7fd783ff5aa1747e05db82f94e_181_0.png)

- A. Log files may fill up quickly.
- B. Successful authentication will not be logged.
- C. Failed authentication will not be logged.
- D. Policy may not be enforced properly.

190. Brian is reviewing vulnerabilities discovered as part of a vulnerability scan. He sees a score for a vulnerability of 3.0. What does he know about this vulnerability based on its score?
- A. It is a high-severity vulnerability and should be addressed quickly.
- B. It is a low-severity vulnerability and may not need to be addressed.
- C. It is a medium-severity vulnerability and should be reviewed before being addressed.
- D. It is a critical vulnerability and should be addressed immediately.

191. Nick wants to allow email servers to validate that email from his servers is actually from them. What email security framework should he adopt to allow this?
- A. DKIM
- B. DMARC
- C. SPF
- D. SMTP

192. Jack wants to configure a Linux system to use mandatory access controls. What tool should he select that is commonly used to provide this functionality?
- A. Group Policy
- B. CIS benchmarks
- C. SELinux
- D. Containerization

193. What process is commonly used with open source tools to ensure that dependencies are secure?
- A. Static analysis
- B. Package monitoring
- C. Fagan testing
- D. Port scanning

194. Yarif wants to harden his SaaS cloud infrastructure. Which of the following hardening techniques is he most likely to be able to implement in an SaaS environment?
- A. Host-based firewalls
- B. Least privilege
- C. Operating system security configuration
- D. Physical security for systems

195. Which of the following is not a technical control used to address a vulnerability?
- A. Insurance
- B. Patching
- C. Segmentation
- D. Firewalling

196. Kelsey's organization has established an asset and inventory management process for servers. Which of the following is not a common part of asset tracking?
- A. Data classification
- B. Identifying owners
- C. Documenting acquisition dates
- D. Sanitization

197. Kirk needs to allow system administrators to access root passwords in emergencies. What type of solution could he implement to allow them to check out passwords when needed while also tracking those checkouts and requiring the passwords to be changed after use?
- A. EAP
- B. Multifactor authentication
- C. An enterprise password manager
- D. Passwordless

198. Selah wants to prevent staff in her organization from visiting malicious websites while they're in the office. If she wants to use the most up-to-date threat data, what web filter capability should she take advantage of?
- A. Agent-based web filtering
- B. Reputation tools
- C. A centralized web filtering proxy
- D. URL scanning

199. Joe has configured ACLs on a Cisco network device. The ACL he has configured is as follows:

What does this ACL do?

```
interface ethernet0
 ip access-group 111 in
!
access-list 111 deny tcp any any eq http
access-list 111 permit ip any any
access-list 111 deny tcp any any eq https
```

- A. Blocks HTTP traffic
- B. Blocks both HTTP and HTTPS traffic
- C. Prevents web application attacks
- D. Allows for inspection of web traffic

200. The use of machine learning and algorithms to analyze user behavior in order to identify anomalous behavior is a feature of what specialized type of tool?
- A. UEBA
- B. SIEM
- C. EDR
- D. DMARC

201. What password best practice is supported by the ability to set password history in Windows?
- A. Password length
- B. Password complexity
- C. Password reuse
- D. Password age

202. Donna is reviewing a script that was found on a Windows system. What does the following script do?

```
$ip = "10.1.1.101"
$svc_name = "WinDefend"
get-service -ComputerName $ip | Where-Object {$_ .Name -eq $svc_name} | Stop-Service | Set-Service -StartupType Disabled
```

- A. Stops the Windows Defender service
- B. Starts the Windows Defender service
- C. Stops and disables the Windows Defender service
- D. Enables the Windows Defender service

203. Batu has been asked to build scripts that will allow automated ticket creation through a new help desk tool for his organization. As he considers the lifespan of the scripts, which of the following concerns should he address to ensure that the scripts do not become an issue over time?
- A. Their initial creation cost
- B. Their ongoing supportability
- C. Existing technical debt
- D. Whether they’re a single point of failure

204. Alex is responsible for his organization’s vulnerability management program. A recent vulnerability scan shows that IoT devices that are used for building automation are vulnerable to a known issue with their built-in web server. After reviewing the manufacturer’s website, Alex is unable to find an updated operating system or software update. He chooses to move the IoT devices to a protected VLAN and require a jump server to access them. What vulnerability remediation option has he used?
- A. A compensating control
- B. Patching
- C. Insurance
- D. An exemption

205. Wiping a drive and reinstalling from known good media is an example of what incident response option?
- A. Recovery
- B. Containment
- C. Eradication
- D. Root cause elimination

206. Melissa's company wants to contract with a third-party organization to oversee their hardware decommissioning and disposal process. What should she ask the company to do to prove that the disposal process was done properly?
- A. Certification.
- B. Follow a data retention policy.
- C. Provide photographic evidence.
- D. Keep a log of devices.

207. Sally wants to identify a way to prioritize vulnerabilities discovered by her vulnerability scanner. Which of the following options will allow her to prioritize vulnerabilities effectively while taking her own organization's needs into account?
- A. Use CVSS base and temporal metrics.
- B. Use a qualitative risk assessment process.
- C. Use CVSS scores that include environmental metrics.
- D. Use a quantitative risk assessment process.

208. Henry wants to prevent password reuse outside of his organization from impacting the accounts his staff use. Which of the following password settings can have the largest impact if passwords are reused outside of his organization and they are breached due to a security issue at the third-party site or service?
- A. Password expiration policies
- B. Password length policies
- C. Password complexity policies
- D. Password minimum age policies

209. Fuzzing is an example of what type of code analysis?
- A. Static analysis
- B. Code review
- C. Pentesting
- D. Dynamic analysis

210. Steve's organization is concerned about the potential for devices they are purchasing to be modified before they reach the organization. Which of the following solutions will help the most in preventing this potential issue?
- A. Buying from a value-added reseller
- B. Buying directly from the OEM
