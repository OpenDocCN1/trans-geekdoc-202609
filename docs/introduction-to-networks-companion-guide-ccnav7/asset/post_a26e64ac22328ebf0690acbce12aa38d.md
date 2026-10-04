
3. Which application layer protocol is used to provide file sharing and print services to Microsoft applications?

+ - a. HTTP
- b. SMTP
- c. DHCP
- d. SMB

4. An author is uploading one chapter document from a personal computer to a file server of a book publisher. What role is the personal computer assuming in this network model?

+ - a. client
- b. master
- c. server
- d. slave
- e. transient

5. Which statement is true about FTP?

+ - a. A client can choose whether FTP should establish one or two connections.
- b. A client can download data from or upload to a server.
- c. FTP is a peer-to-peer application.
- d. FTP does not provide reliability during data transmission.

6. A wireless host needs to request an IPv4 address. What protocol would be used to process the request?

+ - a. FTP
- b. HTTP
- c. DHCP
- d. ICMP
- e. SNMP

7. Which TCP/IP model layer is closest to the end user?

+ - a. application
- b. internet
- c. network access
- d. transport

8. Which three protocols or standards are used at the application layer of the TCP/IP model? (Choose three.)

+ - a. TCP
- b. HTTP
- c. MPEG
- d. GIF
- e. IP
- f. UDP

9. Which protocol uses encryption?

+ - a. DHCP
- b. DNS
- c. FTP
- d. HTTPS

10. Why is DHCP for IPv4 preferred for use on large networks?

+ - a. Large networks send more requests for domain-to-IP address resolution than do smaller networks.
- b. DHCP uses a reliable transport protocol.
- c. It prevents sharing of files that are copyrighted.
- d. It is a more efficient way to manage IPv4 addresses than static address assignment.
- e. Hosts on large networks require more IPv4 addressing configuration settings than do hosts on small networks.

11. Which two tasks can be performed by a local DNS server? (Choose two.)

+ - a. providing IP addresses to local hosts
- b. allowing data transfer between two network devices
- c. mapping names to IP addresses for internal hosts
- d. forwarding name resolution requests between servers
- e. retrieving email messages

12. Which device is most likely to provide dynamic IPv4 addressing to clients on a home network?

+ - a. a dedicated file server
- b. a home router
- c. an ISP DHCP server
- d. a DNS server

13. What part of the URL http://www.cisco.com/index.html represents the top-level DNS domain?

+ - a. .com
- b. www
- c. http
- d. index

14. What are two characteristics of the application layer of the TCP/IP model? (Choose two.)

+ - a. responsible for logical addressing
- b. responsible for physical addressing
- c. responsible for the creation and maintenance of dialogues between source and destination applications
- d. closest to the end user
- e. responsible for establishing window size

15. What message type does an HTTP client use to request data from a web server?

+ - a. GET
- b. POST
- c. PUT
- d. ACK

This page intentionally left blank

## Network Security Fundamentals

## Objectives

Upon completion of this chapter, you will be able to answer the following questions:

+ - Why are basic security measures necessary on network devices?
- How do you identify security vulnerabilities?
- How do you identify general mitigation techniques?
- How do you configure network devices with device hardening features to mitigate security threats?

## Key Terms

This chapter uses the following key terms. You can find the definitions in the glossary at the end of the book.

*virus page 546*
*worm page 547*
*Trojan horse page 547*
*reconnaissance attack page 547*
*access attack page 547*
*denial of service (DoS) attack page 547*
*internet query page 548*

*ping sweep page 548*
*port scan page 548*
*AAA (authentication, authorization, and accounting) page 555*
*stateful packet inspection (SPI) page 557*
*brute-force attack page 560*

## Introduction (16.0)

You may have already set up a network, or you may be getting ready to do so. Here is something to think about: Setting up a network without securing it is like opening all the doors and windows to your home and then going on vacation. Anyone could come by, gain entry, steal or break items, or just make a mess. As news articles indicate all the time, it is possible to break into any network! As a network administrator, it is part of your job to make it difficult for threat actors to gain access to your network. This chapter provides an overview of the types of network attacks and what you can do to reduce a threat actor's chances of succeeding. It also has Packet Tracer activities to let you practice some basic techniques for network security. If you have a network, but it is not as secure as possible, you should read this chapter right now!

## Security Threats and Vulnerabilities (16.1)

This section provides an overview of the various types of network security threats and vulnerabilities.

### Types of Threats (16.1.1)

Wired and wireless computer networks are essential to everyday activities. Individuals and organizations depend on their computers and networks. Intrusion by an unauthorized person can result in costly network outages and loss of work. Attacks on a network can be devastating and can result in a loss of time and money due to damage or theft of important information or assets.

Intruders can gain access to a network through software vulnerabilities, through hardware attacks, or by guessing someone's username and password. Intruders who gain access by modifying software or exploiting software vulnerabilities are called threat actors.

After a threat actor gains access to a network, four types of threats may arise:

+ - **Information theft:** This type of threat involves breaking into a computer to obtain confidential information. Information can be used or sold for various purposes. An example is stealing an organization's proprietary information, such as research and development data.
- **Data loss and manipulation:** This type of threat involves breaking into a computer to destroy or alter data records. An example of data loss is a threat actor sending a virus that reformats a computer hard drive. An example of data manipulation is breaking into a records system to change information, such as the price of an item.

+ - **Identity theft:** This type of threat is a form of information theft in which personal information is stolen for the purpose of taking over someone’s identity. Using this information, a threat actor can obtain legal documents, apply for credit, and make unauthorized online purchases. Identity theft is a growing problem that costs billions of dollars per year.
- **Disruption of service:** This type of threat involves preventing legitimate users from accessing services to which they are entitled. Examples include denial-of-service (DoS) attacks on servers, network devices, or network communications links.

### Types of Vulnerabilities (16.1.2)

*Vulnerability* refers to the degree of weakness in a network or device. Some degree of vulnerability is inherent in routers, switches, desktops, servers, and even security devices. Typically, the network devices under attack are the endpoints, such as servers and desktop computers.

There are three primary sources of vulnerabilities or weaknesses: technological, configuration, and security policy. All three of these sources of vulnerabilities can leave a network or device open to various attacks, including malicious code attacks and network attacks. Tables 16-1 through 16-3 describe examples of the vulnerabilities in each category.

Table 16-1 Technological Vulnerabilities

| Vulnerability | Description |
|---|---|
| TCP/IP protocol weakness | Hypertext Transfer Protocol (HTTP), File Transfer Protocol (FTP), and Internet Control Message Protocol (ICMP) are inherently insecure. |
| TCP/IP protocol weakness | Simple Network Management Protocol (SNMP) and Simple Mail Transfer Protocol (SMTP) are related to the inherently insecure structure on which TCP was designed. |
| Operating system weakness | Each operating system has security problems that must be addressed. |
| Operating system weakness | UNIX, Linux, macOS, Mac OS X, Windows Server 2012, Windows 7, and Windows 8 are documented in the Computer Emergency Response Team (CERT) archives at http://www.cert.org. |
| Network equipment weakness | Various types of network equipment, such as routers, firewalls, and switches, have security weaknesses that must be recognized and protected against. Their weaknesses include password protection, lack of authentication, routing protocols, and firewall holes. |
