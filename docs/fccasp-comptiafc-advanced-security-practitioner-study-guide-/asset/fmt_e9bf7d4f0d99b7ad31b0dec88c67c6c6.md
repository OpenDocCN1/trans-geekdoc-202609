
## 3. Simple Mail Transfer Protocol (SMTP)

SMTP is a TCP service that operates on port 25. It is designed for the exchange of email between networked systems. Messages sent through SMTP have two parts: an address header and the message text. All types of computers can exchange messages with SMTP. Spoofing and spamming are two of the vulnerabilities associated with SMTP, in addition to the fact that it is also transmitted in clear text. Mailsnarf is a tool from the dsniff package created by Dug Song that can be used to sniff SMTP and POP traffic in an automated fashion. Of course, you can also accomplish this with any protocol analyzer.

## 4. Trivial File Transfer Protocol (TFTP)

TFTP operates on port 69. TFTP operates like FTP but with less overhead. It not only does so without the session management offered by TCP, but it also requires no authentication, which could pose a big security risk. It is used to transfer router configuration files and by cable companies to configure cable modems. TFTP is a favorite of hackers and has been used by programs like the Nimda worm to move data without having to use input usernames or passwords.

## 5. Hypertext Transfer Protocol (HTTP)

HTTP is one of the best-known applications. HTTP makes use of TCP port 80. Even though HTTP uses TCP, it makes use of a stateless connection. HTTP uses a request–response protocol in which a client sends a request and a server sends a response. Attacks that exploit HTTP can target the server, browser, or scripts that run on the browser. Cross-site scripting (XSS) and cross-site request forgery (XSRF or CSRF) attacks are two such examples. Basically, hackers craft special packets in a way that exploits vulnerable code on the web server. Again, there are automated tools that can do this, and a good place to start researching this technology is the Open Web Application Security Project (OWASP) website at `www.owasp.org/index.php/Main_Page`. Code Red is an example of code that targeted a web server, specifically Microsoft's IIS Server back in 2001.

## 6. Simple Network Management Protocol (SNMP)

SNMP is a UDP service that operates on ports 161 and 162 and is used for network management. SNMP allows agents to gather such information as network statistics and report back to their management stations. Most large corporations have implemented some type of SNMP management. Some of the security problems that plague SNMP are caused by the fact that v1 and v2 community strings can be passed as clear text, and that the default community strings (public/private) are well known. SNMP version 3 is the most current; it offers encryption for more robust security.

# Secure Communication Solutions

The TCP/IP suite was not built for security. Its primary design consideration was for usability, and although that was acceptable for the early Internet, today secure data flows are needed to meet changing business needs. Some of these weaknesses are due to protocol weaknesses, whereas others are defects in the software that implements the protocols. Many transmission protocols do not provide encryption. CASP candidates must know how to secure this data to meet current and future data needs.

## Network Data Flow

In exercises earlier in this chapter, you used the tool Wireshark; it is an example of a network sniffer. The topic of this section is not network sniffers; however, if you were to use a network sniffer to look at the traffic on your local network, you might be surprised by what you would see. That is because most of the network data that is flowing or traversing a typical network is very easy to inspect. This in turn is because most of the protocols, such as FTP, HTTP, SMTP, NTP, Telnet, and others, are sending data across the network via clear text. This simply means that the traffic is not encrypted and is easy to view. The early designers of TCP/IP and what has become the modern Internet were not concerned about encryption; they were simply trying to get everything to work. This is a concern for the security professional because attackers can easily intercept and view this network traffic. The concept of protection of data and secure protocols such as SSH and SSL came much later.

Even when data is protected with technologies such as SSL and IPSec, an intruder may still be able to break your network. One way to detect current threats and multiple sources of internal and external information is to analyze network data flow. This is known as *network flow analysis*. The concept involves using existing network infrastructure that's already available. Flow analysis provides a different perspective on traffic movement in networks. It allows you to look at how often an event occurred in a given time. As an example, how often was traffic containing encrypted zip files leaving your network between midnight and 2 a.m. headed to Russia on weekends? With flow analysis tools, security professionals can view this type of user activity in near-real time.

Distilling the massive amount of data that flows through modern networks requires tools that allow for the aggregation and correlation of data. Cisco Systems was one of the first to market this technology in the 1990s with the development of NetFlow. Many others have now followed in this field, such as Vitria, Riverbed Technology, and Arbor Networks; each offers flow analysis tools.

## SSL Inspection

The previous section helped make you aware of the need to encrypt traffic as it flows across your network. One common solution is Secure Sockets Layer (SSL). SSL is a cryptographic protocol designed to provide communication security over the Internet or network. It is described in detail in Chapter 1, “Cryptographic Tools and Techniques.” SSL is widely used to protect information in transit.

Although it offers a high level of security, SSL is not foolproof. My point is that every countermeasure, such as SSL, has some vulnerability. One such vulnerability with SSL is SSL inspection, which simply means that an attacker might watch the flow, direction, and amount of traffic. This can lead to something known as an *inference attack*. An inference attack occurs any time an attacker notices a spike in activity and infers that there is some pending event. One way to prevent this type of attack is by means of traffic padding. As an example, a military agency could have a connection between the United States and Ukraine. Although Russian monitors might be able to see that traffic is flowing, the amount transmitted stays at a constant flow and thereby prevents attackers from performing an inference attack.

## Domain Name Service

Domain Name Service (DNS) is one of the workhorses of the Internet. DNS operates behind every address translation, working to resolve fully qualified domain names (FQDNs) into numeric IP addresses. DNS serves a critical function in that if someone were to bring down DNS, the Internet would continue, but it would require that users know the IP address of every site they wish to visit. DNS is a request–response protocol. When a DNS server sends a response for a request, the reply message contains the transaction ID and questions from the original request as well as any answers that it was able to find.

Over the years, computer criminals have found a large number of vulnerabilities in the DNS protocol and the software that implements it. Sometimes an attacker may not even target DNS directly and just target the registration process. One method is the practice of repeatedly registering and deleting a domain name so that the registrant can temporarily own the domain name without paying for it. This is known as *domain kiting*.
