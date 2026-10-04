
12. C. A router uses the ICMP Time Exceeded message when it has decremented an IPv4 TTL or IPv6 Hop Limit field to 0. traceroute uses the source IP address of the ICMP Time Exceeded message sent by the router to determine the router's IP address.

13. C and D. The ping command verifies that the destination IP address is reachable and displays the average round-trip time between the source and destination.

14. D. The traceroute utility identifies the routers in the path to the destination. When a router receives an IP packet from traceroute, it decrements the IPv4 TTL or IPv6 Hop Limit field by 1. When the field's value is 0, the router returns an ICMP Time Exceeded message to the source. traceroute uses the source IP address of the ICMP Time Exceeded message sent by the router to determine the router's IP address.

## Chapter 14

1. C. The client selects a source port number to uniquely identify this process for this device.

2. B. The TCP three-way handshake is used to establish a connection-oriented session between a client and a server.

3. B. TCP and UDP port numbers 0 to 1023 are reserved for well-known network applications.

4. B. A socket is the combination of source IP address and source port number or destination IP address and destination port number. The two combinations together are known as a socket pair.

5. B. A server receives segments from clients, each with a source port number and a destination port number. Along with the source IP address of the client, the server can uniquely identify each service request.

6. B and E. DNS and VoIP commonly use UDP as the transport protocol. DNS uses UDP because it is a transaction-based application. VoIP uses UDP to avoid unnecessary delays and because it can tolerate some data loss.

7. C. TCP tracks multiple conversations to ensure reliability and flow control.

8. C. 192.168.1.1:80 is an example of a socket using a destination IPv4 address and well-known destination port 80 (HTTP).

9. A and E. The ACK and SYN flags are used in the TCP three-way handshake in the following order: (1) SYN, (2) SYN, ACK, (3) ACK.

10. C. FTP uses TCP, so any segments not received are re-sent.

11. A. UDP is best suited for applications that are sensitive to delay and can tolerate some loss of data.

12. A. If the source determines that the TCP segments are either not being acknowledged or are not being acknowledged in a timely manner, it can reduce the number of bytes it sends before receiving an acknowledgment.

13. B and D. TCP acknowledges data received and retransmits any unacknowledged data.

14. D. Sliding window allows a device to continuously send segments as long as the destination is continuously sending acknowledgments as it processes the bytes received.

15. B. Both TCP and UDP identify individual conversations using port numbers and, more specifically, socket pairs.

## Chapter 15

1. B. POP3 transfers messages from an email server to an email client.

2. A. IMAP is used to store email messages on an email server, and the client can read, delete, and send messages from any location.

3. D. SMB is a Microsoft file sharing and print services application protocol.

4. A. The author would be using a client version of file transfer software, using a protocol such as FTP. The file server would be using the server version of the same application.

5. B. FTP uses TCP for reliability and flow control. FTP allows a client device to download or upload data to an FTP file server.

6. C. IPv4 devices obtain their IPv4 addressing information from a DHCP for IPv4 server.

7. A. Users interact with a network by using a client network application such as a web browser. These applications use application layer protocols such as HTTP or HTTPS.

8. B, C, and D. The application layer of the TCP/IP model is the equivalent of the application, presentation, and session layers of the OSI model. HTTP, MPEG, and GIF are all used at this layer. TCP and UDP are transport layer protocols, and IP is an internet layer protocol.

9. D. HTTPS uses TLS (Transport Layer Security) or its predecessor, SSL (Secure Sockets Layer), for encryption.

10. D. DHCP for IPv4 is more efficient and less error prone than assigning IPv4 address information statically on client devices. Static IPv4 address assignment is still done on devices where the addresses need to be consistent, such as servers and intermediary devices.

11. C and D. DNS is used to map a domain name to an IP address. DNS is available for both IPv4 and IPv6.

12. B. Typically, a home router provides private IPv4 addressing to clients using DHCP. It also performs NAT between the private IPv4 addresses and a public IPv4 address.

13. A. The top-level domain (TLD) is .com.

14. C and D. The application layer creates dialogues between source and destination applications, typically clients and servers (for example, HTTP GET request and HTTP response). Users interact with the network by using a client network application such as a web browser. These applications use application layer protocols such as HTTP or HTTPS.

15. A. A client's browser uses an HTTP or HTTPS GET message to request data from a web server.

## Chapter 16

1. E. A firewall protects computers and networks by preventing undesirable traffic from entering internal networks and protecting devices from sending or receiving undesirable messages.

2. B. The syntax for the login block-for command is login block-for seconds attempts tries within seconds.

3. C. The network security accounting function tracks the actions of users and stores that information in a log file.

4. B. nslookup and fping are commands commonly used in reconnaissance attacks, to aid in the discovery and mapping of systems, services, or vulnerabilities.

5. A. Telnet sends passwords in plaintext, whereas SSH encrypts both the username and the password.

6. A. A firewall protects computers and networks by preventing undesirable traffic from entering internal networks and protecting devices from sending or receiving undesirable messages.

7. A. A DoS (denial-of-service) attack disables a server with bogus message in order to prevent the device from servicing authorized users.

8. A, C, and D. AAA makes it possible to control who is permitted to access a network (authenticate), what they can do while they are there (authorize), and what actions they perform while accessing the network (accounting).

9. B. Computer worms are similar to viruses in that they replicate functional copies of themselves and can cause the same type of damage. In contrast to viruses, which require the spreading of an infected host file, worms are standalone software and do not require a host program or human help to propagate.

10. B. Failure of an air conditioning unit causing a networking device to overheat would be an environmental situation.

11. A. A vulnerability such as an unpatched security issue or a weak password makes a device susceptible to an attack.

12. B, C, and E. To require an IP domain name, use the ip domain name global configuration command. Unless an authentication server is used, there must be a local database username entry; you add this by using the username global configuration command. A device must have a unique hostname other than the default.

13. A. A reconnaissance attack aids in the discovery and mapping of systems, services, or vulnerabilities.

14. B. Firewall settings on network devices or end devices can prevent ICMP Echo Request and Echo Reply messages from being forwarded or received.

15. D. Unlike Telnet, which sends the passwords in plaintext, SSH encrypts the username and password.

## Chapter 17

1. D. Redundancy might not be critical to the business operations in a smaller size business, but it can be very important in a large corporation.

2. D. Devices with support for modularity allow for device expansion. Ensuring modularity can be less expensive than purchasing additional devices to accommodate additional growth.

3. C. Voice traffic is more delay sensitive than FTP, instant messaging, and SNMP, and it benefits from QoS during times of congestion.

4. C. Microsoft Windows uses the tracert command in place of traceroute.

5. C. If a remote device can be reached directly by using the IP address but not its domain name, the issue may be that the DNS server is unreachable or is unable to resolve the name. It is not always possible to reach a
