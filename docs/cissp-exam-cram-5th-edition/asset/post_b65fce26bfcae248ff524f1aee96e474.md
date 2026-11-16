
## Terminal Access Controller Access Control System (TACACS)

TACACS is an access-control protocol used to authenticate a user logging on to a network. TACACS is a UDP-based protocol that provides authentication, authorization, and accountability. It was originally used in Cisco devices.

TACACS is very similar to RADIUS. When TACACS receives an authentication request, it forwards the received username and password to a central database. This database verifies the information received and returns it to TACACS to allow or deny access based on the results. The fundamental reason TACACS did not become popular is because TACACS is a proprietary solution from Cisco, and its use would require the payment of royalties.

TACACS+ is a completely new rewrite of the TACACS protocol that separates authentication and authorization. TACACS+ is not compatible with TACACS. TACACS+ is TCP based and offers extended two-factor authentication. When most people today say “TACACS,” they really mean TACACS+.

## Internet Protocol Security (IPsec)

IPsec was developed to provide security for IP packets. Without IPsec, someone could capture, read, or change the contents of data packets and then send them back to the unsuspecting target. The current version of IP, IPv4, supports IPsec as an add-on; IPv6 has IPsec built in. IPsec offers its users several levels of cryptographic security:

- **Authentication header (AH)**: The AH protects data against modification but does not provide privacy. The AH uses a hashing algorithm and symmetric key to calculate a message authentication code known as the integrity check value (ICV). When the AH is received, an ICV is calculated and checked against the received value to verify integrity.

- **Encapsulating Security Payload (ESP)**: ESP provides privacy and protects against malicious modification. ESP provides confidentiality by encrypting the data packet. The encrypted data is hidden from prying eyes, so its confidentiality is ensured.

- **Oakley protocol**: Oakley is a portion of IKE that is responsible for carrying out the negotiations.

- **Security association (SA)**: For AH and ESP to work, there must be some negotiations regarding the rules of conduct for exchanging information between the client and server. These negotiations include the type of symmetric and asymmetric algorithms that will be used, as well as state-specific information in support of the secure channel. The results of these negotiations are stored in an SA. The SA identifies the details of each one-way connection. Two-way communication channels have two SAs, each distinguished by its *Security Parameter Index (SPI)*. If both AH and ESP are used, four SAs are required. IPsec uses a symmetric shared key to encrypt bulk communications. The Diffie-Hellman algorithm is the key agreement protocol used to generate this shared key.

- **Internet Key Exchange (IKE)**: IKE allows secret keys to be exchanged securely before communications begin. IKE is responsible for creating IPsec's SA and is considered a hybrid protocol because it combines the functions of two other protocols: Internet Security Association and Key Management Protocol (ISAKMP) and Oakley.

Key exchange must be handled securely. IPsec uses ISAKMP. It is defined by RFC 2408 and is used for establishing SAs and cryptographic keys in an Internet environment. Basically, IPsec defines procedures and formats to establish, negotiate, modify, and delete SAs, and it defines payloads for exchanging key generation and authentication data. Each has an IP protocol number; ESP is protocol 50, and AH is protocol 51. Because IPsec is applied at Layer 3 of the OSI model, any layer above Layer 3 can use it transparently. Other Internet security systems in widespread use, such as Transport Layer Security (TLS) and Secure Shell (SSH), operate in the upper layers of the OSI model. IPsec has two modes of operation:

- **Transport mode**: Protects just the payload.

- **Tunnel mode**: Protects the payload and the header. In this configuration, IPsec acts as a gateway; traffic for any number of client computers can be carried. IPsec in tunnel mode provides link encryption and is compatible with IPv6. It can be used to encrypt any traffic supported by IP.

Figure 5.19 illustrates the differences between the two modes.

![](img/cd307d33c10f35ada49ea76811ef60ad_421_0.png)

### FIGURE 5.19 IPsec Tunnel and Transport Modes

RFC 2401 defines three different implementation architectures for IPsec:

- Host-to-gateway: Used to connect one system that runs IPsec client software to an IPsec gateway.
- Gateway-to-gateway: Connects two IPsec gateways to form an IPsec connection that acts as a shared routable network connection.
- Host-to-host: Connects two systems to each other via IPsec.

## Message Privacy and Multimedia Collaboration

New technologies make it possible to monitor all types of information that one individual might send to another. Bullrun is one example of such a program. The NSA developed this controversial program to give the U.S. government the means to defeat the encryption used in specific network communication technologies. Its full capability is unknown.

Some Internet applications have little or poor built-in security. Instant messaging (IM) is a good example. Many corporations allow or use IM applications such as WhatsApp, Viber, and Telegram. However, many IM applications lack strong end-to-end encryption capabilities, have insecure password management, and have features that may work to bypass firewalls.

IM can be vulnerable to sniffing attacks, can be used to spread viruses and worms, and can be targeted for buffer overflow attacks. If these programs are going to be used, security controls such as the Pidgin-Encryption plug-in and SSL-based chat should be considered. IM products are highly vulnerable to malware, such as worm viruses, backdoor Trojan horses, hijacking, impersonation, and denial of service. IM can also be used to exfiltrate sensitive information.

Web conferencing is a low-cost method that allows people in different locations to communicate over the Internet. Common solutions include Adobe Connect, Zoom, and Microsoft Teams. Though useful, web conferencing can potentially be sniffed and intercepted by an attacker. These technologies usually allow users to display PowerPoint slides, share audio or video, and even share documents. Some solutions allow users to remotely control another connected PC.

Remote meeting and web conferencing software is typically designed to tunnel outbound SSL or TLS traffic. These technologies often pass outside the corporate network and as such should be understood, controlled, and made compliant with all applicable policy as they offer attackers and others the ability to exfiltrate data.

Finally, email is a common network application that, in its native state, can be very insecure. As mentioned earlier in this chapter, sending an email message is much like your parents sending a postcard about their vacation to you through the U.S. mail. Anyone who happens to see the card during transit can read the message they sent you from their trip to Niagara Falls. If you need email privacy, you must use encryption. Using encryption is the equivalent of sending a coded letter in a sealed envelope: Even if someone opens the sealed envelope, the coded letter will prevent anyone from learning about your mother’s trip to see the majestic falls. Email protection mechanisms, as described earlier in this chapter, include PGP, Secure Multipurpose Internet Mail Extensions (S/MIME), and Privacy Enhanced Mail (PEM).

## Exam Prep Questions

- 1. You are a security consultant for a new company that is going to sell products online. Customers will be expected to pay for their products on the company website. It is necessary to establish a secure connection between two TCP-based machines to ensure web communications for financial transactions. You have been asked to suggest some type of Extensible Authentication Protocol to help secure this traffic. Which of the following would you consider the most secure and also the most costly?

  - A. EAP-LEAP
  - B. EAP-MD5
  - C. EAP-TLS
  - D. EAP-SIM

- 2. You just overheard two people discussing ways to steal electronic serial numbers (ESNs). What type of attack are they discussing?

  - A. Bank card hacking
  - B. Modem hacking
  - C. PBX hacking
  - D. Cell phone hacking

- 3. You are a security consultant for a company that has locations in Houston, New York City, and Dallas. Your client requires link-to-link communications from the LAN to the WAN for data/traffic encryption supported by IP that includes encryption and authentication. They will be using L2TP at Layer 3 of the OSI model. The CIO for the company plans to migrate to IPv6 over the next year, and he wants something that will be compatible with IPv6. What is the BEST protocol to use for this client?

  - A. IPsec transport mode
  - B. IPsec tunnel mode
  - C. PPTP
  - D. L2F

- 4. Which of the following is a mechanism for converting internal IP
