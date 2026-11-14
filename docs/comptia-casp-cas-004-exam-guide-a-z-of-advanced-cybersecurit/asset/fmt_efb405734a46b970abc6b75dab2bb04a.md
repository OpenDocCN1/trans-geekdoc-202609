
You undoubtedly don’t enjoy how your inbox fills up with unwanted emails every day, many of which are attempting to sell you something. When you purchase anything or visit a website, you often cause yourself to get this email by not paying careful attention to all of the facts. Spam is defined as an email that is sent to a large number of people without their permission. Spam is more than an irritation; it may jam inboxes and force email servers to expend resources to transmit it. Because sending spam is against the law, many spammers attempt to disguise their origins by relaying over the email servers of other businesses. This not only conceals the real source but also puts the relaying firm in jeopardy. Today’s email servers may refuse to relay to any email servers that you haven’t specified. This may help prevent your email system from being used for spam. On your email servers, this form of relaying should be prohibited. Spam filtering should also be installed on all email servers.

# Capturing messages

A protocol analyzer may collect email traffic in its raw form, just like any other sort of communication. It is possible to read an email if it is written in plain text. As a result, every email that contains critical information should be encrypted. While this may be done using the intended recipient’s digital certificate, it is usually only practicable if the receiver is a member of your organization and your firm has a PKI. Many email clients come with built-in support for digital signatures and message encryption utilizing digital certificates. While email encryption applications such as `Pretty Good Privacy` (`PGP`) are available, many users find it difficult to utilize them appropriately without training. Encryption equipment or service that automates email encryption is another alternative. Regardless of the method used, the only way to prevent information from being leaked from captured packets is to encrypt communications.

# Information disclosure

Information is sometimes leaked not because an unencrypted communication is intercepted, but because the email is exchanged with people who aren’t always trustworthy. Even if a policy for information sharing exists, it may not be implemented by all employees. You may sanitize all outgoing material for sorts of information that should not be revealed and have it deleted to avoid this type of exposure. `Axway MailGate` is one example of a product that can achieve this. For international organizations or corporations with hundreds of thousands of users, `MailGate` can safeguard email systems against virus assaults, botnets, spam, or Denial-of-Service attacks. `MailGate` helps filter out up to 90% of unwanted emails before they reach corporate email infrastructure, preventing “*accidents*” or even deliberate data leakage that could harm a person’s reputation or violate intellectual property laws, as shown in `Figure 14.7`:

![](images/Image28893.jpg)

`Figure 14.7:` `Axway MailGate`

# Malware

Email is a popular carrier of malware; in fact, email is the most prevalent way for malware to infect computers. Malware scanning software should be installed on both the client PCs and the email server. Malware may still get through despite these precautions; therefore, it’s critical to educate consumers on how to handle emails safely (such as not opening attachments from unknown sources).

# Integration of telephony and VoIP

Traditional analog phone lines and digital, or `Voice over IP` (`VoIP`), telephony systems are also available. Analog phones link to a `private branch exchange` (`PBX`) system in conventional telephony. The organization’s IP data network is independent of the phone network. While analog phone networks may seem to have some security advantages, the US `Federal Communications Commission` (`FCC`) is in the process of deconstructing the analog phone infrastructure that has existed since the days of Bell Labs. While there is no specific date for definitive discontinuance, it seems silly to implement a system that will soon be outdated, no matter how safe it is. Furthermore, as stated in the following section, many of the security vulnerabilities with `VoIP` seem to be being addressed. `Figure 14.8` showcases the `SIP` protocol for `VoIP`:

![](images/Image28901.jpg)

`Figure 14.8:` `SIP` Protocol for `VoIP`

`VoIP` phone systems have several benefits, but they also pose a security risk. `VoIP` spam, often known as `Spam over Internet Telephony` (`SPIT`), is one sort of assault. Unsolicited pre-recorded phone messages are sent in this form of assault. The only way to detect these assaults is to analyze `Session Initiation Protocol` (`SIP`) traffic on a regular basis. For call setup and teardown, `SIP` is utilized. If you’re utilizing `Secure Real-Time Transport Protocol` (`SRTP`), encryption, integrity, and anti-replay protocol for `Real-Time Transport Protocol` (`RTP`) communication, you should do an `SRTP` traffic analysis as well. `RTP` is used to carry audio and video communication. Some protocol analyzers, such as `GL Communications’ PacketScan`, are specifically designed for these protocols. This kind of analysis may aid in the detection of `SPIT` attacks.

While the danger of spying, service theft, and denial-of-service assaults is greater with `VoIP` than with classic analog, there are steps that can be implemented to alleviate the concerns and lower the risks; these steps are as follows:

*   Separate the phone and data networks physically.
*   On infrastructure equipment, secure all management interfaces (for example, switches, routers, and gateways).
*   In high-security environments, use a secure phone of some kind (to provide end-to-end encryption).
*   Use `network address translation` (`NAT`) to mask the phones’ genuine IP addresses.
*   Keep your operating system and `VoIP` software up to date with the latest updates.
*   Turn off any services or features that you don’t need.
*   Use `802.11e` to provide `Quality of Service` (`QoS`) for `VoIP` packets when they transit a wireless segment, just as you would for all wired segments, to avoid performance difficulties, particularly during DoS assaults on the network.
*   Use a firewall to protect the `SIP` servers, which are the servers responsible for generating voice and video sessions.

# Sites for collaboration

Users are increasingly collaborating on cloud-based technologies employing web technology. Organizations are also using social media to communicate with consumers and share information with the rest of the world. While both social media and cloud-based collaboration have their advantages, they also have their drawbacks. The sections that follow examine these challenges and mitigating measures, as well as provide advice for responsible usage of social media and cloud-based collaboration.

# Social media
