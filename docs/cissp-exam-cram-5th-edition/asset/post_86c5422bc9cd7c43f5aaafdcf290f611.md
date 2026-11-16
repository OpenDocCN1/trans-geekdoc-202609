
### 4. addresses found in IP headers into public addresses for transmission over the Internet?

- A. ARP
- B. DNS
- C. DHCP
- D. NAT

### 5. Samuel has been asked to start the implementation of IPv6 on an existing IPv4 network. The current system has no native connection to an IPv6 network. It has about 130 hosts. The internal routing protocol is OSPF. Which technology would you recommend that Samuel use?

- A. VRRP
- B. Teredo
- C. 802.1AE
- D. 6to4

### 6. You have been brought on as a consultant to a small nonprofit that is using a routing protocol based on Bellman-Ford algorithms. Although the network has reached convergence, one path is no longer available and shows an infinite hop count. What is the proper term to describe this situation?

- A. Loopback
- B. Split horizon
- C. Classless inter-domain routing
- D. Poison reverse

### 7. Which of the following is considered an update to WEP?

- A. WPA2
- B. SMLI
- C. PGP
- D. POP

### 8. Which of the following closely resembles a packet-filtering device that makes decisions on addresses, ports, and protocols?

- A. Stateless firewall
- B. Circuit-level proxy
- C. Application proxy
- D. Stateful firewall

### 9. Which protocol is considered a forerunner to Frame Relay and works over POTS lines?

- A. SMDS
- B. ATM
- C. X.25
- D. T-carrier

### 10. Which of the following is true of RADIUS?

- A. It provides authentication and accountability.
- B. It provides authorization and accountability.
- C. It provides authentication and authorization.
- D. It provides authentication, authorization, and accountability.

### 11. You have been asked to implement a WAN technology for your client. The client is based in a rural area in the southern United States. The client does not want to use a circuit-switched technology. In this situation, which of the following is a cell-switched technology that you could use?

- A. DSL
- B. T1
- C. ISDN
- D. ATM

### 12. Which of the following is considered a third-generation firewall?

- A. Packet filter
- B. Circuit-level proxy
- C. Application-level proxy
- D. Stateful firewall

### 13. Which of the following is a list of protocols that work at OSI Layers 2, 6, 3, 4, and 7?

- A. ARP, SQL, ICMP, SMB, and SNMP
- B. L2TP, SMB, IP, SQL, and HTTP
- C. WEP, ASCII, IPX, TCP, and BootP
- D. PPP, ZIP, SPX, UDP, and TFTP

### 14. Which of the following wireless standards has a frequency range of 5.15–5.35 GHz to 5.725–5.825 GHz and can be used for distances of approximately 60 feet?

- A. 802.11a
- B. 802.11b
- C. 802.11g
- D. 802.11n

### 15. Which of the following is the BEST description of ISAKMP?

- A. Defines procedures and packet formats to establish, negotiate, modify, and delete security associations and defines payloads for exchanging key generation and authentication data. Typically uses IKE for key exchange, although other methods can be implemented.
- B. Enables the authentication of the parties involved in a secure transition and contains the certificate issuer’s name, a valid from date and a valid to date, the owner of the certificate (the subject), the subject’s public key, the timestamp, and the certificate issuer's digital signature.
- C. A framework for managing private keys and certificates that provides a standard for key generation, authentication, distribution, and storage; establishes who is responsible for authenticating the identity of the owners of the digital certificates; and follows the X.509 standard.
- D. A standard that defines how to protect keys and establish policies for setting key lifetimes and that sets out essential elements of business continuity and disaster recovery planning.

## Answers to Exam Prep Questions

- 1. C. EAP-TLS is one of the most secure but expensive solutions as it requires certificates for both the server and the client. Answers A and B are incorrect because both EAP-LEAP and EAP-MD5 are known to be insecure. Answer D is incorrect because EAP-SIM is used for smartphones and mobile devices.

- 2. D. Cell phone hackers scan for electronic serial numbers and mobile identification numbers, which are used to clone phones. Answer A is incorrect because bank card hacking would most likely target a database. Answer B is incorrect because the individuals who target modems are known as war dialers. Answer C is incorrect because PBX hacking is performed by phreakers.

- 3. B. IPsec in tunnel mode provides link encryption, is compatible with IPv6, and can be used to encrypt any traffic supported by IP. It can also be used with L2TP or alone and operates at Layer 3 of the OSI model. Answer A is incorrect because transport mode encrypts only the IP payload. Answer C is incorrect because PPTP does not offer encryption. Answer D is incorrect because it works at Layer 2 of the OSI model and does not provide data encryption.

- 4. D. NAT allows a single device, such as a router, to act as an agent between the Internet and the internal network. ARP is used for physical address resolution, so answer A is incorrect. DNS is used for IP address resolution, so answer B is incorrect. DHCP is used to assign dynamic addresses, so answer C is incorrect.

- 5. B. Teredo is a transition technology that can be used for IPv6-capable hosts that are on the IPv4 Internet and have no native connection to an IPv6 network. Answer A is incorrect because Virtual Router Redundancy Protocol (VRRP) is used for router redundancy. Answer C is incorrect because 802.1AE is a Layer 1 OSI technology known as MACsec. Answer D is incorrect because although 6to4 is an Internet transition mechanism for migrating from IPv4 to IPv6, it is typically used where there is connectivity to an IPv6 network.

- 6. D. Poison reverse sets the number of hops to the unconnected gateway to a number that indicates infinite. All other answers are incorrect. Answer A describes the loopback address, which has no relevance to the question. Answer B is incorrect because split horizon is a route advertisement that prevents routing loops in distance-vector routing protocols by prohibiting a router from advertising a route back onto the router interface from which it was discovered. Answer C is incorrect because classless inter-domain routing was designed to slow the growth of routing tables on routers across the Internet and to help slow the rapid exhaustion of IPv4 addresses.

- 7. A. WPA2 is the current standard for wireless security. Answer B is incorrect because SMLI is a firewall technology. Answer C is incorrect because PGP is an email-protection mechanism, and POP, answer D, is associated with email, so it is incorrect.

- 8. B. Circuit-level proxies closely resemble packet-filtering devices because they examine addresses, ports, and protocols. Stateless firewalls are packet-filtering devices and application proxies, and stateful firewalls examine higher-level content, so answers A, C, and D are incorrect.

- 9. C. X.25 predates Frame Relay. Although it is not fast, it is reliable and works over analog phone lines. SMDS is a high-speed MAN/WAN packet-switched protocol, so answer A is incorrect. ATM is a modern protocol that offers high speed and various classes of service, so answer B is incorrect. T-carrier is a circuit-switched technology, so answer D is incorrect.

- 10. C. RADIUS is a client/server protocol used to authenticate dial-in users and authorize access. The other answers are incorrect because they do not meet the specification of RADIUS.

- 11. D. ATM is a cell-switched technology. DSL, T1, and ISDN are not based on cell-switching technology, and therefore answers A, B, and C are incorrect.

- 12. D. Stateful firewalls are considered intelligent firewalls and are third-generation devices. Circuit-level proxies and application-level proxies are second-generation devices, and packet filters are first-generation devices, so answers A, B, and C are incorrect.

- 13. C. WEP is found at Layer 2. ASCII is found at Layer 6, IPX is found at Layer 3, TCP is found at Layer 4, and BootP is found at Layer 7.

- 14. A. 802.11a has a frequency range of 5.15–5.35 GHz to 5.725–5.825 GHz and can operate over a distance of approximately 60 feet.

- 15. A. ISAKMP is Internet Security Association and Key Management Protocol. It defines procedures and packet formats to establish, negotiate, modify, and delete security associations, and it defines payloads for exchanging key generation and authentication data. It typically uses IKE for key exchange, although other methods can be implemented. Answers B and C are both incorrect because they deal specifically with certificate management. Answer D is incorrect because it deals with key management.

## Need to Know More?

- Introduction to TCP/IP: www.cse.wustl.edu/~jain/tutorials/ftp/t_2tcp.pdf
- Introduction to the OSI model: www.studynotesandtheory.com/single-post/Quick-Breakdown-of-OSI-Model
- Encapsulation: www.tcpipguide.com/free/t_IPDatagramEncapsulation.htm
- Bluetooth keyboard sniffing: www.helpnetsecurity.com/2016/07/26/keystroke-sniffing-wireless-keyboards/
- Microsegmentation: www.cisco.com/c/en/us/products/security/what-is-
