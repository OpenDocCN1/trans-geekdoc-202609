
Another technique used to assess the security of a system or network is to look into the architecture of the system. For example, computer processors use a ring architecture to run software (see [Figure 20-4](#ch20.xhtml#ch20fig4)). Software running in the lower rings (ring 0 is the lowest) has more privileges than software running in higher rings. Part of the ring architecture is that software running in a ring can access resources at that ring or higher. Therefore, core operating system code that runs in ring 0 can access anything in rings 1, 2, and 3. However, applications running on the system, which run in ring 3, cannot access core operating system code and as a result cannot corrupt those processes.

![Image](f0786-01.jpg)

**FIGURE 20-4**

The processor’s four-ring architecture helps create a secure environment to run applications.

#### Design Reviews

Another tool you can use to assess security is to perform design reviews before and after a solution is implemented. It is also critical to identify a system’s security concerns right from the start so that you can claim a `secure by design` status (meaning security was a focus from beginning to end with the creation of the solution). Once the solution has been completed, whether it be an application or network solution, do a design review and ensure that what was requested as a solution is actually what has been implemented.

### CERTIFICATION OBJECTIVE 20.02

### Performing a Security Assessment

This section gives you a good overview of the steps you should take to perform a good penetration test. Be sure to follow each step closely in order to protect yourself as a penetration tester. You do not want the company or organization coming back at you stating they did not ask you to perform the test.

When performing a security assessment, ensure you take the time to plan your steps and to follow a methodology. The methodology may be your own, or you can follow industry-standard methodologies (recommended). The following are some standard methodologies you should be aware of as a security professional:

- **OVAL** — Open Vulnerability and Assessment Language is an international standard for assessing vulnerabilities to a system. OVAL has three stages to the assessment: represent system information, assess vulnerabilities, and report on the vulnerabilities. Learn more about OVAL from [http://oval.mitre.org/about/index.html](http://oval.mitre.org/about/index.html).

- **OCTAVE** — Operationally Critical Threat, Asset, and Vulnerability Evaluation is a self-directed security assessment methodology. “Self-directed” means that an organization chooses a team from its own employees to do the security assessment. OCTAVE has four phases: (1) Develop risk management criteria consistent with the goals of the business, (2) Create a profile for each information asset that identifies the security requirements, (3) Identify threats to each of those assets, and (4) Identify and analyze risks and begin mitigation approaches. Learn more about OCTAVE at [www.cert.org/octave/](http://www.cert.org/octave/).

- **OWASP** — Open Web Application Security Project is a project that standardizes web application security testing procedures. You can learn more at [www.owasp.org](http://www.owasp.org). OWASP has some great guides published on web application testing and code review.

#### Threat Hunting

*Threat hunting* is the term used to describe the action of identifying threats to company assets before the assets are attacked and compromised by an attacker. Threat hunters monitor network and system activity to discover potential new threats and vulnerabilities that may exist in their environment. A threat hunter may use a number of tools, including the following:

- **Intelligence fusion** — Intelligence fusion is the gathering of individual streams of “intelligence” or surveillance data and the combining of that data together to get a full picture of the current situation. For example, in the world of IT security, you could be “fusing” antivirus data, data from network sensors, server logs, and firewall connection information to show an attack occurred and the extent of the attack.

- **Threat feeds** — Threat feeds are listings of indicators of a threat that are published and distributed through web sites to automate the sharing of indicators of a threat. The threat feed database may contain information such as malicious IP addresses or malicious e-mail senders. The benefit is anyone subscribed to the feed has knowledge of this information as it is updated.

- **Advisories and bulletins** — Advisories and security bulletins can be sent out to notify the public of new security threats.

- **Maneuvering** — Maneuvering is the concept of strategically moving to get a competitive advantage. With threat management, you should be dynamic in your strategies to discover new threats (for example, placing honeypots within specific areas of the network to detect threats).

#### Vulnerability Scans

When performing a vulnerability assessment, you can use a vulnerability scan as a technique to automate the process of identifying vulnerabilities within the environment. This section identifies a number of considerations that should be made when performing a vulnerability scan and the different ways to identify vulnerabilities.

##### Considerations with Vulnerability Scans

When using a vulnerability scanner to automate the process of identifying vulnerabilities, you should keep the following key points in mind:

- **Intrusive vs. nonintrusive** — It is important to know that a vulnerability scan is considered a nonintrusive scan because you are not actually trying to hack the system or exploit it (a penetration test does try to exploit the system).

- **Credentialed vs. noncredentialed** — When performing a vulnerability scan, you should ensure that you perform one as an unauthenticated user (noncredentialed) to find out what information is being exposed to unknown persons to the network. You then should perform the scan logged in as an administrative account so that you can collect as much information about the system as possible.

- **False positives** — As with any kind of scan, it is important to watch for false positives—something that is being reported as a vulnerability but is not.

- **False negatives** — False negatives could be seen as being worse than false positives because they are events that occurred that were not detected by the system. In regard to vulnerability scans, a false negative is a vulnerability that exists that was not identified by the vulnerability scanner.

##### Types of Checks

As discussed earlier in the chapter, vulnerability scanners can perform a number of different types of checks on the system:

- **Configuration review** — The vulnerability scanner can check the configuration of a system and report back to you any vulnerable settings that should be changed.

- **Log reviews** — The vulnerability scanner may review log files on the system to identify events that have occurred that could be considered suspicious.

- **Application** — The vulnerability scanner may perform vulnerability checks on applications and look for flaws in the application design.

- **Web application** — There are specific vulnerability scanners for web applications, such as `Nikto`, that look for common vulnerabilities that may exist on a web site.

- **Network** — A vulnerability scanner may have the capability to perform a scan of multiple systems on the network as well as scan network devices such as switches, routers, and printers.

##### Understanding CVE and CVSS
