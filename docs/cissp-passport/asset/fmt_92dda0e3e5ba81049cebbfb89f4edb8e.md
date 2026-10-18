
# Hypertext Transfer Protocol (HTTP)

Hypertext Transfer Protocol (HTTP) is a ubiquitous protocol used to transfer web content, such as text, images, and other multimedia. It is the language that creates web pages. However, by itself it is not secure and sends information in clear text. It must use secure network transmission protocols for authentication and encryption. One of these protocols in widespread use is Transport Layer Security (TLS). TLS was always intended as a replacement for an older protocol, Secure Sockets Layer (SSL) but, in 2014, SSL 3.0 was found to be vulnerable to the POODLE attack, which affects all block ciphers that SSL uses. Both protocols operate in similar manners, however, and when HTTP is tunneled through SSL or TLS, it is known as HTTPS (for HTTP Secure). Both SSL and TLS use TCP port 443 by default.

![Images](caution.jpg)

> **CAUTION** Secure Sockets Layer in all its versions (through 3.0) has been deprecated since 2015 and effectively replaced by Transport Layer Security. However, you may still see references to it on the exam, as well as the ability to configure SSL in legacy applications.

TLS, currently in version 1.3 (as of August 2018), provides end-to-end encryption services and works primarily at the session layer of the OSI model. Version 1.3 supports only five encryption algorithms (as opposed to 37, including some that had known vulnerabilities, in previous versions), so this minimizes the number of vulnerable cipher suites that can be used. This also makes it difficult for an attacker to downgrade the level of encryption to a less secure version. TLS not only is used to secure normal HTTP sessions but can also be used for other secure end-to-end encryption needs, such as virtual private networking. TLS-based virtual private networks (VPNs) carry less overhead and can be used for client-to-site VPNs over modern web browsers. TLS supports both server authentication and mutual authentication between the client and server.

When a client initiates a TLS connection, it sends a “hello” message that lists the cipher suites the client supports and a request for key exchange. The server replies with its choice of cipher suites and secure protocols. The server also sends its digital certificate, which proves the server’s identity, and provides a public key for the client to use for secure key exchange. The client then sends back a secure session key by encrypting it with the server’s public key, which only the server can decrypt. This establishes a secure key for encrypted communications. An optional step is having the client authenticate itself to the server by sending its own digital certificate and public key.

## IPSec

IP Security (IPSec) is a protocol suite that resides at the network layer of the OSI model (or the Internet layer of TCP/IP). It was developed because IPv4 does not have any built-in security mechanisms. IPSec can provide both encryption and authentication services, as well as secure key exchange, protecting IP traffic. IPSec consists of four main protocols in the suite:

- **Authentication Header (AH)** Provides for authentication services and data integrity
- **Encapsulating Security Payload (ESP)** Provides encryption services for data payloads
- **Internet Security Association and Key Management Protocol (ISAKMP)** Allows security key association and secure key exchange
- **Internet Key Exchange (IKE)** Assists in key exchange between two entities using IPSec

![Images](note.jpg)

> **NOTE** IPSec can use AH and ESP separately or together, depending on whether the traffic needs to be encrypted, authenticated, or both.

IPSec can be used to protect communications in one of two modes: transport mode or tunnel mode. In transport mode, IPSec can be used on the local network and can encrypt specific traffic, including specific protocols between multiple hosts, as long as all hosts support the same authentication and encryption methods. This can help secure sensitive traffic within a network. In tunnel mode, IPSec is tunneled into another protocol, most commonly into the Layer 2 Tunneling Protocol (L2TP), and sent outside of local networks across other, nonsecure or public networks, including the Internet, to another network, making it effective for establishing VPN connections. IPSec can protect both data and header information while in tunnel mode.

![Images](exam.jpg)

> **EXAM TIP** Understand the difference between IPSec’s transport and tunnel modes. Transport mode only protects the IP payload and is normally used on an internal network, while tunnel mode encapsulates the entire packet, including header information (e.g., IP address), and is used to carry traffic securely across untrusted networks, such as the Internet. IPSec traffic in tunnel mode must also be encapsulated in a network tunneling protocol such as L2TP.

## Secure Shell

Secure Shell (SSH) is both a secure protocol and a suite of tools used to provide encryption and authentication services to communications sessions. It’s most commonly used in Linux environments, although it has been ported to Windows operating systems as well. It is often used for remote access between hosts to perform secure, privileged operations. This makes SSH ideal to replace previously used remote session protocols, such as Telnet, which offered no security services whatsoever. Although not very scalable, SSH can be used for long-haul remote access on a limited basis. In addition to encrypting data and providing authentication between hosts, SSH can be used to protect nonsecure protocols, such as File Transfer Protocol (FTP), when those protocols are tunneled through it. However, SSH offers its own secure versions of these protocols, such as Secure Copy Protocol (SCP) and Secure Shell FTP (SFTP).

![Images](exam.jpg)

> **EXAM TIP** Don’t confuse SFTP, the Secure Shell version of FTP, with FTP that is simply tunneled through TLS or SSH (known as FTPS). SFTP is not tunneled through SSH—it is actually part of the SSH secure suite.

SSH uses TCP port 22 and can work at several layers of the OSI model, including the session layer and higher. Utilities included in the SSH suite allow users to generate host and user keys to facilitate strong authentication between hosts and users.

## EAP

The Extensible Authentication Protocol (EAP) is a framework that allows multiple types of authentication methods to be used for users and devices to authenticate networks, typically over remote or wireless connections. EAP can use many different authentication methods, such as passwords, tokens, biometrics, one-time passwords (OTPs), Kerberos, digital certificates, and several others. When two entities connect using EAP, they negotiate a list of authentication methods that are common to both entities. EAP can be used over a variety of other protocols, such as PPP, PPTP, and L2TP, and over both wired and wireless networks. There are several different variants of EAP, which use TLS (EAP-TLS), pre-shared keys (EAP-PSK), tunneled TLS (EAP-TTLS), and version 2 of the Internet Key Exchange (EAP-IKE2). These variants are each suitable for different types of authentication requirements, depending on the existing infrastructure and compatibility with legacy devices. EAP is also used extensively with 802.1X authentication methods, discussed next.

## 802.1X

IEEE 802.1X is not part of the 802.11 standards but is often confused with them because it is frequently used in conjunction with WLANs. 802.1X is a port-based authentication protocol and can be used with both wired and wireless networks. Its primary purpose is access control. It allows for both devices and users to be authenticated and can enforce mutual authentication. It is more often encountered in enterprise-level networks than in personal networks.

802.1X has three important components you should be aware of for the exam:

- **Supplicant** Typically a client device
