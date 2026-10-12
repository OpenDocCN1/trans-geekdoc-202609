
# Comprehensive Security Solutions

Today's systems are much more distributed than in the past and have a much greater reliance on the Internet. At the same time, there has been a move toward service-enabled delivery of services. Service-enabled delivery of web-based applications includes services such as `SOAP`, `XML-RPC`, and `JSON-RPC`. Securing those services is a big concern to the CASP.

There has also been a move to create web services that have a more abstract architectural style, `SOA`, which attempts to bind together disjointed pieces of software. `SOA` can be implemented using ad hoc architectures, `Common Object Request Broker Architecture (CORBA)`, or other distributed architectures.

## Summary

This chapter focused on comprehensive security solutions. The two broad topics of this chapter examined:

*   Network protocols
*   Applications and services

Modern networks are built on the `TCP/IP` protocol stack. As a CASP, you should have a good understanding of how `TCP/IP` works and know the purpose and weaknesses of the primary protocols such as `IPv4`, `IPv6`, `TCP`, `UDP`, and `ICMP`.

You should also have a grasp of network flow analysis. You must also understand the importance of securing routing protocols and be familiar with controls put in place to improve transport security, trucking security, and route protection.

Applications and services are also of importance to the CASP. You must know how to secure `DNS`, understand the importance of securing zone transfers, and know how to configure `LDAP`.

Finally, there is authentication, along with authentication protocols such as `PAP`, `CHAP`, and `EAP`. This critical component is used as a first line of defense to keep hackers off your network. Systems such as federated ID, `AD`, and single sign-on can be used to more securely manage this process.

## Exam Essentials

1.  **Be able to describe advanced network design concepts.** Advanced network design requires an understanding of remote access and firewall deployment and placement. Firewall placement designs include packet filtering, dual-homed gateway, screened host, and screened subnet.

2.  **Be familiar with the process of remote access.** Cisco has implemented a variety of remote access methods through its networking hardware and software. Originally, this was `Terminal Access Controller Access Control System (TACACS)`. The most current version is `TACACS+`. Another, newer standard is `DIAMETER`. Although both operate in a similar manner, `DIAMETER` improves upon `RADIUS` by resolving discovered weaknesses.

3.  **Be able to describe switches, routers, and wireless devices.** A security professional must understand various types of network equipment and the attacks that can be performed against them. Both switches and routers can be used to increase network security, but techniques such as MAC flooding and route poisoning can be used to overcome their security features.

4.  **Be able to describe SCADA systems.** `SCADA` systems are digital controls that are designed to do such things as open valves and control switches. From a security standpoint, these systems are an important consideration because they are typically used by the utilities industry to monitor critical infrastructure systems, control power distribution, and for many other forms of automation.

5.  **Be able to describe VoIP.** `VoIP` is packetized voice traffic sent over an IP network. `VoIP` offers cost savings and the ability to make use of existing data networks to send voice traffic. `VoIP` uses protocols such as `Session Initiation Protocol (SIP)`, `H.323`, `Inter-Asterisk Exchange Protocol (IAXv2)`, and `Real-time Transport Protocol (RTP)`.

6.  **Be able to describe TCP.** `TCP` is a connection-based protocol that uses a startup, handshaking process, flow control, flags, and shutdown to reliably deliver data through applications such as `FTP`, `HTTP`, and `SMTP`. At the heart of `TCP`'s reliable communication is a 1-byte flag field. Flags help control the `TCP` process. Common flags include synchronize (`SYN`), acknowledge (`ACK`), push (`PSH`), and finish (`FIN`).

7.  **Be able to describe IPv6.** `Internet Protocol version 6 (IPv6)` is the newest version of the IP and is the designated replacement for `IPv4`. `IPv6` brings many improvements to modern networks. `IPv6` moves the address space from 32 bits to 128 bits and has `IPSec` built in. Security concerns include the fact that older devices may not be compatible or able to provide adequate protection.

8.  **Know how DNSSEC works.** `DNSSEC` is designed to provide a layer of security to `DNS`. `DNSSEC` allows hosts to validate that domain names are correct and have not been spoofed or poisoned.

9.  **Know the importance of securing zone transfers.** Securing zone transfers begins by making sure that your `DNS` servers are not set to allow zone transfers. If your host has external `DNS` servers and internal `DNS` servers, the security administrator should also close `TCP` port 53. Internal `DNS` servers should be configured to talk to only the root servers.

10. **Be able to explain the characteristics of TSIG.** When the `DNS` client and `DNS` server exchange a set of `DNS` messages to establish a secure session, the update message sent by the `DNS` client contains a `TSIG` record used to validate the `DNS` client. `TSIG` is used to provide a means of authenticating updates to a Dynamic `DNS` database.

11. **Know how LDAP operates.** `LDAP` was created to be a lightweight alternative protocol for accessing `X.500` directory services. With `LDAP`, each object is made up of attributes that are indexed and referenced by a distinguished name. Each object has a unique name designed to fit into a global namespace that helps determine the relationship of the object and allows for the object to be referenced uniquely.

12. **Be able to describe the importance of transport security.** Increased network security risks and regulatory compliances have driven the need for WAN transport security. Examples of transport security include `IPSec`, `TLS`, and `SSL`. `IPSec` is the Internet standard for security.

## Review Questions

1.  **What separates the authentication and authorization process into three operations?**
    *   **A.** `XTACACS`
    *   **B.** `TACACS+`
    *   **C.** `TACACS`
    *   **D.** `RADIUS`

2.  **Which of the following is proprietary to Cisco?**
    *   **A.** `XTACACS`
    *   **B.** `DIAMETER`
    *   **C.** `TACACS`
    *   **D.** `RADIUS`

3.  **Which of the following designs uses one packet filtering router between a trusted and untrusted network?**
    *   **A.** Screened host
    *   **B.** Screened subnet
    *   **C.** Dual-homed gateway
    *   **D.** Single-tier packet filter

4.  **Which of the following correctly represents a broadcast physical address?**
    *   **A.** `00 00 0C 34 44 01`
    *   **B.** `01 00 00 FF FF FF`
    *   **C.** `FF FF FF FF FF FF`
    *   **D.** `01 00 0C 34 44 01`

5.  **You have been asked to examine some traffic with Wireshark and have noticed that some traffic is addressed to 224.3.9.5. What class of address is this?**
    *   **A.** Class C
    *   **B.** Class D
    *   **C.** Class B
    *   **D.** Class A

6.  **You have been scanning a network and have found TCP 53 open. What might you conclude from this?**
    *   **A.** `DNS` is configured for lookups.
    *   **B.** A `DNS` zone transfer might be possible.
    *   **C.** `DNSSEC` has been configured.
    *   **D.** `SMTP` is being used.

7.  **You have just scanned your network and found UDP port 123. What service makes use of this port?**
    *   **A.** Portmapper
    *   **B.** `NTP`
    *   **C.** Finger
    *   **D.** `LDAP`

8.  **Which of the following is not offered by Kerberos for Windows users?**
    *   **A.** Interoperability
    *   **B.** Nondelegated authentication
    *   **C.** Mutual authentication
    *   **D.** Simplified trust management

9.  **LDAPS provides for security by making use of _______________.**
    *   **A.** `DES`
    *   **B.** `SSL`
    *   **C.** `SET`
    *   **D.** `PGP`

10. **DNSSEC does not protect against which of the following?**
    *   **A.** Masquerading
    *   **B.** Domain spoofing
    *   **C.** Domain kiting
