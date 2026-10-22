introduction to the protocols used and then progresses to associated threats. Following that is a discussion of best practices and then encryption.

# 34.3.1 Protocol Basics

# 34.3.1.1 Audio Stream Protocols: RTP and UDP.

Real-time Transport Protocol (RTP) is the packet-based communication protocol that provides the base for virtually all VoIP architectures. Part of RTP is timing and packet sequence information that can be used to reconstruct audio streams. Like TCP, User Datagram Protocol (UDP) is a layer 4 network communication protocol. Both of these protocols provide the basic packet addressing needed to get from one network address to another. When dealing with VoIP, packet delivery time is of the essence. Both TCP and UDP add overhead to the organization’s network communication. This overhead results in greater time delays to the communication. UDP adds less overhead as it provides comparatively little packet error checking. The compromise is that UDP will help deliver packets quicker but will also result in more lost packets. It has been observed that a packet loss of 10 percent spread over a VoIP call may be virtually undetectable to most users. However, all of the features that can make VoIP secure also add latency. Added latency means more lost or discarded packets, which then results in an unpleasant or unacceptable user experience. In the end, a slow packet is a lost packet.

# 34.3.1.2 Signaling Protocols: SIP and H.323.

Session Initiation Protocol (SIP) is a protocol that is used to establish interactive multimedia sessions between users. In addition to VoIP, it is also used for video conferencing and online gaming. SIP appears to be the most commonly accepted form of establishing VoIP calls. Secure SIP (SSIP) is discussed in Section 34.5.1. Like SIP, H.323 can be used for video conferencing or VoIP call setup. While SIP appears to be the standard for new installations. One may find H.323 in use at enterprise scale installations that have large investments in older, analog communication equipment.

Briefly, the basics of a VoIP call include these details. A VoIP client application, whether on a personal computer or a dedicated handset, uses SIP or H.323 to set up the call. This call setup is an exchange of control parameters that may include encryption and compression algorithms to be used. This is called "signaling." Once the call is set up, the VoIP client uses RTP to start packetizing the voice data. The RTP packets are incorporated into a UDP packet that adds addressing and sequencing information. The UDP packets are collected and sorted by sequence number at the receiving station. Some systems use a "jitter buffer" to assemble and store the packets. The endpoint VoIP client then reads the jitter buffer and turns the RTP packets back into voice.

# 34.3.2 VoIP Threats.

Although not an exhaustive list, these hacks represent some of the vulnerabilities likely to be encountered when using VoIP:

+   - SPam over Internet Telephony (SPIT)
+   - Eavesdropping
+   - Theft of service
+   - Man-in-the-middle attacks

# 34.3.2.1 SPIT.

Most users have become accustomed to finding 10 or 20 (or 100 or 200) spam email messages in an inbox on daily basis. The thought of receiving an equal number of voicemails on a daily basis leads to the unappetizing acronym