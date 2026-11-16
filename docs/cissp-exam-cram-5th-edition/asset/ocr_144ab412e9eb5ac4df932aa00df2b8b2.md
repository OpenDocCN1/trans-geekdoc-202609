complete, the public address is returned to the pool.

+   ▶ Port Address Translation (PAT): Most home networks using DSL or cable modems use this type of NAT. PAT is designed to provide many internal users Internet access through one external address.

# Remote Access

Well-designed networks require authentication and access control. Users might be internal to an organization or in a hotel on the road. Being outside the organization raises concerns in addition to proper authentication, such as confidentiality and privacy. This section discusses an array of topics related to remote access, including Password Authentication Protocol (PAP), Challenge Handshake Authentication Protocol (CHAP), VPNs, and IPsec.

# Point-to-Point Protocol (PPP)

PPP is the most commonly used protocol for dialup connections. It can run on a line of any speed, from POTS to T1. Developed in 1994 by the IETF, PPP is a replacement for Serial Line IP (SLIP). SLIP is capable of carrying only IP and had no error detection, whereas PPP supports many types of authentication, including PAP, CHAP, and EAP.

# Password Authentication Protocol (PAP)

PAP uses a two-way handshake to authenticate a client to a server when a link is initially established. PAP sends a password in plaintext, which makes it highly vulnerable to sniffing attacks.

# Challenge Handshake Authentication Protocol (CHAP)

CHAP is an improved version of PAP. It uses a four-way handshake to authenticate the client. CHAPv2 provides for mutual authentication. When a client requests authentication, the server sends the client a challenge. The client hashes the challenge with its password and returns it to the server. This hashed value is compared on the server with a hash that the server created. Although no plaintext ever crosses the network, anyone who knows the