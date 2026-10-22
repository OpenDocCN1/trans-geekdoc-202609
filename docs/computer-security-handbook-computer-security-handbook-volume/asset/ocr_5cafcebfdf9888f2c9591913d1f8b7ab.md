the issues start. The firewall does not have a problem with passing SIP traffic back and forth to the Internet, as the internal address of the VoIP device is stored in the translation table. However, the SIP signaling has passed on the private address of the user’s VoIP device. This means that a device outside of the local network is trying to send the RTP/UDP audio stream to a fictional IP address. Essentially, NAT prevents VoIP from functioning.

Several work-arounds are commonly used. Sometimes the NAT device can be configured to provide VoIP support. Sometimes VoIP devices can be configured to work over otherwise open ports, overloading a common protocol such as HTTP, unfortunately, often with unintended side effects. Or VoIP proxy servers can be used on either side of the NAT in order to facilitate the traversal. Each of these solutions opens up its own security concerns, which should be carefully addressed; these concerns include the consequences of external proxy servers or creating anomalous traffic over other protocols, as in the overloading example.

# 34.5 ENCRYPTION.

Encryption plays a critical role in communications security. For a general introduction to encryption, see Chapter 7 in this Handbook; for more details of public key encryption, see Chapter 37.

# 34.5.1 Secure SIP.

Transport Layer Security (TLS) was sponsored by the Internet Engineering Task Force (IETF) to secure and encrypt data communications crossing public networks. It is intended to replace Secure Sockets Layer (SSL) as a widely accepted form of securing data communication. This protocol consists of a “handshake” and a “record.” TLS was designed to be application independent so developers could choose their own way of initiating a TLS session.

Secure SIP is a mechanism designed to send SIP signaling messages over an encrypted TLS channel. A SSIP session is initiated by a SIP client contacting a SIP proxy and requesting a TLS session. The proxy returns a certificate that the SIP client then authenticates. The client and proxy then exchange encryption keys for the session. If the call is destined for another network segment, the SIP proxy will contact that segment and negotiate a sequential TLS session, so the SIP message is protected by TLS the entire time.

# 34.5.2 Secure Real-Time Protocol.

Secure Real-Time Protocol (SRTP) is an enhancement of RTP that provides encryption, authentication, and integrity to the VoIP audio stream. The Advanced Encryption Standard (AES) originally was a block cipher; SRTP incorporates AES into the data stream with an implementation that utilizes it as a stream cipher.

Encryption is good but it does not protect the user or organization against replay attacks. SRTP uses a Hashed Message Authentication Code (HMAC-SHA1) algorithm to provide authentication and integrity checks. The MAC is calculated using a cryptographic hashing function in conjunction with a private key. SRTP uses one of the five Secure Hash Algorithms (SHA) designed by the National Security Agency. All five of these algorithms are compliant with requirements set in the Federal Information Processing Standards (FIPS).

# 34.5.3 Session Border Control.

To this point, a number of issues affecting a VoIP deployment have been identified. Session border control (SBC) is a set of services that address VoIP issues related to security, QOS, NAT traversal, and network