
Note that authentication and ticket distribution are highly dependent upon system time synchronization in a Kerberos realm; the KDC timestamps all tickets and must have access to a valid time source, such as a Network Time Protocol (NTP) server. If the time settings on devices within the Kerberos realm vary by more than a specified amount, it will create issues with the timestamps on the tickets. This synchronization requirement helps prevent replay attacks.

Kerberos is a very resilient system for authentication and authorization; however, it also has several weaknesses:

• The `KDC` is a single point of failure unless there is redundancy in place with multiple servers.

• The `KDC` must be scalable and able to handle the number of users on the network.

• Weak keys, such as passwords, are vulnerable to attack.

• Secret keys are temporarily stored on user devices (sometimes in a decrypted state), so if the device is compromised, the keys may also be compromised.

The operating system and other security controls can help mitigate Kerberos weaknesses; these include encrypting all traffic and end-user device protection.

##### Remote Access Authentication and Authorization

The CISSP exam objectives require you to understand various remote access authentication and authorization protocols and technologies. We covered some of these earlier in the domain and briefly mentioned both `RADIUS` and `TACACS+` in Objective 4.3. For this objective we will go into more detail regarding `RADIUS`, `TACACS+`, and another remote access protocol, `Diameter`. These protocols are referred to as authentication, authorization, and auditing (or accounting, depending on the source), or AAA, protocols.

AAA protocols provide these services to remote users who may use dial-up, VPN, or other types of remote connections. They make use of remote access servers, running these protocols, that can also connect to authentication databases, such as Microsoft’s Active Directory. Although these remote access technologies are not widely used, having been replaced by more modern VPN technologies, you may still see them used in special circumstances (such as an initial connection to an Internet provider prior to full authentication and connection provisioning), legacy systems, or locations where there is sparse high-speed Internet availability.

###### RADIUS

Remote Authentication Dial-In User Service (`RADIUS`) is an access protocol that can provide authentication, authorization, and accounting services for remote connections into networks. `RADIUS` was originally created to support dial-up connections into larger Internet service providers (`ISPs`) using infrastructure with large modem banks, authentication databases, and accounting and billing services for those connections. `RADIUS` uses a network access server for dial-in but can then offload authentication services to internal credential databases. `RADIUS` supports many of the older authentication protocols, such as `PAP`, `CHAP`, and `MS-CHAP`.

In terms of communications protection, the `RADIUS` server can encrypt passwords but nothing else, including username and other session communications information, such as IP address, hostname, and so on. `RADIUS` also requires more overhead than other protocols, particularly `TACACS+`, discussed in the next section, since it relies on `UDP` (over ports 1812/1813 or 1645/1646) and must have built-in error checking mechanisms to make up for `UDP`’s connectionless design.

###### TACACS+

Terminal Access Controller Access Control System Plus (`TACACS+`) functions like `RADIUS` but is very different. Whereas `RADIUS` uses `UDP`, `TACACS+` uses `TCP` (over port 49). There are three distinct protocols in the `TACACS` family: the original `TACACS` protocol, `TACACS+`, and Extended `TACACS` (`XTACACS`). You should be aware that the original `TACACS`, `XTACACS`, and `TACACS+` are three different protocols; they’re not compatible with each other. In fact, `TACACS+` and `XTACACS` started out as Cisco proprietary protocols, but `TACACS+` has since become an open standard.

`TACACS` combines its authentication and authorization services, but `XTACACS` separates the authentication, authorization, and accounting functions. It’s also worthy to note that `TACACS+` improves upon `XTACACS` by adding multifactor authentication, whereas the original `TACACS` uses only fixed passwords.

###### Diameter

`Diameter` was developed to enhance the functionality of `RADIUS` and overcome some of its many limitations. It provides more flexibility and capabilities than either `RADIUS` or `TACACS+`. It is used by wireless devices and smartphones, and can be used over Mobile IP, Ethernet over PPP, and even VoIP. `Diameter` is different than both `RADIUS` and `TACACS+` in that while they are client/server protocols, `Diameter` is a peer-to-peer protocol where either endpoint can initiate communications. Note that `Diameter` is not backward compatible with `RADIUS`; it is considered an upgrade.

![Images](exam.jpg)

**EXAM TIP** Although not specifically called out in the CISSP exam objectives, you may see `Diameter` as a distractor or incorrect answer when a question focuses on `RADIUS` or `TACACS+`, so it’s a good idea to at least be familiar with it. `Diameter` is a similar technology and is almost always discussed alongside `RADIUS` and `TACACS+` protocols.

### REVIEW

**Objective 5.6: Implement authentication systems** In this objective we discussed authentication mechanisms, systems, and protocols that are widely used to connect systems on the Internet and securely pass credentials from one system to another, enabling single sign-on for users. We discussed the particulars of two important authentication mechanisms, Open Authorization (`OAuth`) and OpenID Connect (`OIDC`), as well as an XML-based language, `SAML`, that allows credentials to be securely exchanged between systems that depend on third-party IdM services. We also discussed protocols such as `Kerberos`, which is prevalent in Microsoft’s Active Directory, and three key AAA protocols used in remote connections for authentication, authorization, and accounting, `RADIUS`, `TACACS+`, and `Diameter`.

#### 5.6 QUESTIONS

**[1](#ch05.xhtml#ch5ques6-1).** You are performing a security review of a web-based application developed by your company. However, the developers have not built in support for any third-party identity provider and are unsure of how to do so. They need to be able to use a common language to help exchange authentication information with third-party providers. Which of the following should you advise them to use?

**A.** `OAuth`

**B.** `RADIUS`

**C.** `SAML`

**D.** `TACACS+`

**[2](#ch05.xhtml#ch5ques6-2).** You are troubleshooting a client’s Active Directory infrastructure. They are having problems with users only sporadically being able to authenticate to the network and access resources. After looking at multiple logs, you see several entries indicating that tickets are expiring rapidly or are being rejected because they are no longer valid. Which of the following could be the source of the problem?

**A.** Time synchronization across the network is not working.

**B.** The `KDC` is offline.

**C.** Users are inputting incorrect credentials.

**D.** Faulty network equipment is causing a disruption of service.

#### 5.6 ANSWERS

**[1](#ch05.xhtml#r_ch5ques6-1).** C You should advise the developers that the web application should support `SAML`, since it is an XML-based standardized language used for exchanging authentication information with third-party identity providers.
