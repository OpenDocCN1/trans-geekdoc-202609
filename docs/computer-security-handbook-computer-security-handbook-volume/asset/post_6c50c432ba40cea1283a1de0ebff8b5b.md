
## 35.3.4 Case Study

Misconfiguration, unintentional use, curiosity, and experimentation with P2P in the workplace do happen, with consequences. Although this case is only one type of specific security incident involving P2P technology, it should serve as an example of how such a situation can occur.

An employee of one organization reported a slow-running computer to the helpdesk. All of the usual helpdesk suggestions and tricks were exhausted with little effect on the performance of the computer. The usual symptoms of a slow computer were present—massive wait times to accomplish simple tasks, random errors and shutdowns, lockups, and other operational problems. However, there was one difference: After a reboot, it would take several minutes for the computer to slow down and become unresponsive. After some time, an employee commented, "I did try installing a music sharing program last week, but I didn't like it and uninstalled it." This led the engineer to examine each and every process that was running on the computer.

Although it appeared that the P2P application had been uninstalled, it actually had not been; it was still installed and running in a stealth mode. The uninstaller only masked the P2P application. Not only was the P2P application still running, but it was misconfigured to share the entire contents of the C: drive. There were literally thousands of other P2P users attached to the machine actively searching, uploading, downloading, and altering the contents of the computer's hard drive. The computer was not only giving away all of its data, it was being used for a server to host thousands of media files. Since the computer was on a network segment that had full TCP/IP 1-to-1 network address translation, it was effectively completely open to the outside world—and the outside world was taking full advantage of the opportunity. The hard drive was virtually full, and files were being added and deleted at will by remote users. The host's firewall was even modified by the P2P application's install to open all necessary ports to the world.

It is unknown if the user's personal data was actually accessed, downloaded, or used for any malicious activity, but the capability was certainly there. Because of a user's unauthorized download, inadequate network security, and other policy violations, the organization could not be sure of the confidentiality or integrity of the computer or its data. Necessary steps were taken to prevent this incident from occurring again, but this scenario has played out at other organizations, and will continue to do so as long as the P2P risk exists.

## 35.4 SECURING INSTANT MESSAGING

Instant messaging has become an integral part of communications—both business and personal—for many people. It was fairly easy in the recent past to simply create a policy that banned IM for personal use and only allowed internal, business-related IM within the company. However, IM has become an integral part of life. IM is pervasive in most organizations—for personal and business use. As a result, from executives to interns, IM may be found on many desktops, but it must be managed and secured on all.

### 35.4.1 Dangers to the Business

With any technology, especially those that make connections to the Internet, there is a risk to the organization. Instant messaging is not a petty annoyance that should be taken lightly; if the technology is not controlled by the organization, a serious breach of security could occur. Remember, IM applications today go well beyond just text; they are capable of transmitting much more than just interpersonal casual banter.

#### 35.4.1.1 Loss of Information

Information loss and loss of confidentiality, intentionally or unintentionally, is most likely the biggest threat of IM to the business. There are several ways information can be harmfully conveyed via IM⁸:

- Revealing secrets via text chat, especially when a company has taken extensive effort to filter and block such communication via email with email gateways, intellectual property data management, and other technologies
- Copy-and-paste functions (including screen captures) used to transmit confidential or secret information from other secured applications or environments
- File transfers
- Screen sharing and real-time collaboration functions such as shared whiteboards or desktop sharing functions
- Forgetting to turn off a voice or video session and unintentionally relaying sound or images to the original correspondent—especially dangerous when leaving voice mail through the IM client
- Relaying voice, video, or both to another party (unintentional or intentional)
- Use of Webcam technology to relay visual information within a secure facility
- Downloading malware to collect and steal data
- Impersonation (This tactic usually involves stealing a known IM account or creating a fake account to impersonate someone the victim knows.)
- Subpoenas or search warrants executed to collect IM logs, conversations, and so on

Although this is not a complete list, it should serve to aid in security planning and policy development. There are many good resources on the Internet to further explain similar threats and consequences, but the preceding list should encourage thoughtful brainstorming about the ways in which an organization may lose data. Some of the listed methods would be extremely difficult to detect and remedy. With high-speed networks and high-speed Internet links at most organizations, a massive amount of data can be conveyed within a small amount of time.

#### 35.4.1.2 Consequences

Like other security threats, the consequences of not securing IM technology can be serious. Many organizations today have experienced a security breach that involved IM, and there are probably more to come. Instant messaging security breaches can be deadly to an organization by themselves or as part of a much larger attack on the business. Stealing or transmitting information through IM is no less risky than any other form of information theft. One single file, whether sent through an IM file transfer or meticulously cut and pasted, bit by bit over a great period of time, can destroy a company’s reputation and standing in the public eye or even benefit a competitor. A breach from a single IM conversation has the potential to depress a corporation’s stock price in a matter of hours or days. There have even been cases where a chief executive officer’s confidential information was captured and posted on the Internet for all to see.⁹

#### 35.4.1.3 Denial of Service

IM cannot be written off as a tiny application with no real footprint on network resources. Instant messaging can be a tool used to create a denial of service attack on an organization, resulting in a loss of availability. IM technology can be a powerful and useful tool for an attacker, including the use of IM clients with a direct connection to the Internet. With the right combination of malware and access, an attacker may be able to exploit one of many vulnerabilities discovered in IM applications, including the ever-popular buffer overflow. The National Vulnerability Database listed 38 current vulnerabilities in instant messaging software as of March 2012.¹⁰

### 35.4.2 Prevention and Mitigation

Every organization must guard against the threats caused by IM technology. Proper review and analysis of the risks associated with IM must be carried out within the organization, and the organization must determine the amount of risk it is willing to take. It is also necessary to evaluate the costs and efforts associated with the prevention and mitigation of this threat. Organizations will judge the risks and rewards of using IM differently. There is no set standard for every organization or business; there is no universal set of rules that can be applied in all situations. (For a discussion of risk assessment and management, see Chapter 62 in this Handbook.) The next sections provide strategies, tactics, and considerations for securing IM.

#### 35.4.2.1 Policy

Policy must come first, especially with the popularity and widespread use of IM. Without adequate policies, the organization has no chance of actually protecting itself. Policy must be the foundation that all other considerations rest on. Clearly defined, well-communicated, and equally enforced policy is one of the most important fundamentals information security relies on. No matter what the organization decides when it comes to IM rules, it must be stated in a policy.

Instant messaging, while risky, is one of the most visible policy decisions a business will make for employees. While it might be best, and preferred for best security, to completely disallow IM, this could lead to frustrated employees, unable to use the facility for personal use, business use, or both. Every management team should be conscious of the potential ramifications of an overly strict policy. Conversely, allowing unfettered IM is certainly not the best solution.

Some organizations, depending on their software platform, may be able to provide employees with a managed IM environment where the employee can connect to the organization’s official IM platform, as well as some of the popular IM services used for personal communications. At the same time, the organization can centrally deploy settings such as which services are allowed, how they connect (encrypted or not), and what logging options are in use—including if conversations can be recorded or archived.

Compliance and governmental regulations must be taken into consideration. If IM communications are to be allowed, they may become part of the organization’s business communications, and therefore may be subject to subpoena, open records requests, and archiving and document retention requirements. This can be especially dangerous if the chosen IM platform is integrated into the organization’s voice over IP system. New regulations and legal rules may greatly affect policy decisions. It is important to remember that instant messaging logs and conversations may be subject to legal discovery, search, and seizure. Consult counsel for proper legal advice.

#### 35.4.2.2 Effects of a Complete Ban

A ban on all IM technology would be the best way to ensure better enterprise security. However, this will only produce dissatisfied users, without being effective. Users can become technology-savvy in a hurry if they are determined to circumvent a policy. A block on IM communications often
