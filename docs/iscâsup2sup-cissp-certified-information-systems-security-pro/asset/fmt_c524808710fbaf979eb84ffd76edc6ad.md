
# NAT

NAT is used to hide the internal structure of a private network as well as to enable multiple internal clients to gain internet access through a few public IP addresses. NAT is often a native feature of border security devices, such as firewalls, routers, gateways, and proxies.

# Circuit Switching vs. Packet Switching

In circuit switching, a dedicated physical pathway is created between the two communicating parties. Packet switching occurs when the message or communication is broken up into small segments (usually fixed-length packets, depending on the protocols and technologies employed) and sent across the intermediary networks to the destination. Within packet-switching systems are two types of communication: paths and virtual circuits. A virtual circuit is a logical pathway or circuit created over a packet-switched network between two specific endpoints. There are two types of virtual circuits: permanent virtual circuits (PVCs) and switched virtual circuits (SVCs).

# WAN Links

WAN links, or long-distance connection technologies, can be divided into two primary categories: dedicated and nondedicated lines. A dedicated line connects two specific endpoints and only those two endpoints. A nondedicated line is one that requires a connection to be established before data transmission can occur. A nondedicated line can be used to connect with any remote system that uses the same type of nondedicated line. WAN connection technologies include X.25, Frame Relay, ATM, SMDS, SDLC, HDLC, SDH, and SONET.

# Security Controls for Network Communications

When selecting or deploying security controls for network communications, you need to evaluate numerous characteristics in light of your circumstances, capabilities, and security policy. Security controls should be transparent to users. Hash totals and CRC checks can be used to verify message integrity. Record sequences are used to ensure sequence integrity of a transmission. Transmission logging helps detect communication abuses.

# Virtualization

Virtualization technology is used to host one or more operating systems within the memory of a single host computer. This mechanism allows virtually any OS to operate on any hardware. It also allows multiple operating systems to work simultaneously on the same hardware. Virtualization offers several benefits, such as being able to launch individual instances of servers or services as needed, real-time scalability, and being able to run the exact OS version needed for the application.

# Email Security

Internet-based email is insecure unless you take steps to secure it. To secure email, you should provide for nonrepudiation, restrict access to authorized users, make sure integrity is maintained, authenticate the message source, verify delivery, and even classify sensitive content. These issues must be addressed in a security policy before they can be implemented in a solution. They often take the form of acceptable use policies, access controls, privacy declarations, email management procedures, and backup and retention policies.

Email is a common delivery mechanism for malicious code. Filtering attachments, using antivirus software, and educating users are effective countermeasures against that kind of attack. Email spamming or flooding is a form of denial of service that can be deterred through filters and IDSs. Email security can be improved using S/MIME, MOSS, PEM, and PGP.

# Fax and Voice Security

Fax and voice security can be improved by using encryption to protect the transmission of documents and prevent eavesdropping. Training users effectively is a useful countermeasure against social engineering attacks.

# Security Boundaries

A security boundary can be the division between one secured area and another secured area, or it can be the division between a secured area and an unsecured area. Both must be addressed in a security policy.

# Communication System Vulnerabilities

Communication systems are vulnerable to many attacks, including distributed denial of service (DDoS), eavesdropping, impersonation, replay, modification, spoofing, and ARP and DNS attacks. Fortunately, effective countermeasures exist for each of these. PBX fraud and abuse and phone phreaking are problems that must also be addressed.

# Exam Essentials

## Understand the issues around remote access security management

Remote access security management requires that security system designers address the hardware and software components of an implementation along with issues related to policy, work tasks, and encryption.

## Be familiar with the various protocols and mechanisms that may be used on LANs and WANs for data communications

These are `SKIP`, `SWIPE`, `SSL`, `SET`, `PPP`, `SLIP`, `CHAP`, `PAP`, `EAP`, and `S-RPC`. They can also include `VPN`, `TLS/SSL`, and `VLAN`.

## Know what tunneling is

Tunneling is the encapsulation of a protocol-deliverable message within a second protocol. The second protocol often performs encryption to protect the message contents.

## Understand VPNs

VPNs are based on encrypted tunneling. They can offer authentication and data protection as a point-to-point solution. Common VPN protocols are `PPTP`, `L2F`, `L2TP`, and `IPsec`.

## Be able to explain NAT

NAT protects the addressing scheme of a private network, allows the use of the private IP addresses, and enables multiple internal clients to obtain internet access through a few public IP addresses. NAT is supported by many security border devices, such as firewalls, routers, gateways, and proxies.

## Understand the difference between packet switching and circuit switching

In circuit switching, a dedicated physical pathway is created between the two communicating parties. Packet switching occurs when the message or communication is broken up into small segments and sent across the intermediary networks to the destination. Within packet-switching systems are two types of communication paths, or virtual circuits: permanent virtual circuits (PVCs) and switched virtual circuits (SVCs).

## Understand the difference between dedicated and nondedicated lines

A dedicated line is always on and is reserved for a specific customer. Examples of dedicated lines include `T1`, `T3`, `E1`, `E3`, and cable modems. A nondedicated line requires a connection to be established before data transmission can occur. It can be used to connect with any remote system that uses the same type of nondedicated line. Standard modems, `DSL`, and `ISDN` are examples of nondedicated lines.

## Know various issues related to remote access security

Be familiar with remote access, dial-up connections, screen scrapers, virtual applications/desktops, and general telecommuting security concerns.

## Know the various types of WAN technologies

Know that most WAN technologies require a channel service unit/data service unit (CSU/DSU), sometimes called a WAN switch. There are many types of carrier networks and WAN connection technologies, such as `X.25`, `Frame Relay`, `ATM`, `SMDS`, `SDH`, and `SONET`. Some WAN connection technologies require additional specialized protocols to support various types of specialized systems or devices.

## Understand the differences between PPP and SLIP

The Point-to-Point Protocol (`PPP`) is an encapsulation protocol designed to support the transmission of IP traffic over dial-up or point-to-point links. `PPP` includes a wide range of communication services, including assignment and management of IP addresses, management of synchronous communications, standardized encapsulation, multiplexing, link configuration, link quality testing, error detection, and feature or option negotiation (such as compression). `PPP` was originally designed to support `CHAP` and `PAP` for authentication. However, recent versions of `PPP` also support `MS-CHAP`, `EAP`, and `SPAP`. `PPP` replaced Serial Line Internet Protocol (`SLIP`). `SLIP` offered no authentication, supported only half-duplex communications, had no error-detection capabilities, and required manual link establishment and teardown.
