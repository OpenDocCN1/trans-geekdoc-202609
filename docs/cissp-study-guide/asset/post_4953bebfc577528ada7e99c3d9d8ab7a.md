
# Network Architecture and Design 259

frames can range in size from under 100 bytes to over 1500 bytes. In contrast, all ATM cells are 53 bytes.

SMDS (Switched Mult Gigabit Data Service) is older and similar to ATM, also using 53-byte cells.

# MPLS

Multiprotocol Label Switching MPLS provides a way to forward WAN data via labels, via a shared MPLS cloud network. This allows MPLS networks to carry many types of network traffic, including ATM, Frame relay, IP, and others. Decisions based on labels, such as an IP header), MPLS can carry data and be used to simplify WAN routing. If T1s were used, the data center would require T12 circuits (one to each office); with MPLS, the data center and each office would require a single connection to connect to the MPLS cloud.

# SDLC and HDLC

Synchronous Data Link Control (SDLC) is a synchronous Layer 2 protocol that uses polling to transmit data. Combined nodes can act as primary or secondary. SDLC supports NRM transmission only (below).
High-Level Data Link Control (HDLC) is the successor to SDLC. HDLC adds error correction and flow control, as well as two additional modes (ARM and ABM). The three modes of HDLC are:

- Normal Response Mode (NRM)—Secondary nodes can transmit when permission by the primary
- Asynchronous Response Mode (ARM)—Secondary nodes may initiate communication with the primary
- Asynchronous Balanced Mode (ABM)—Combined mode where nodes act as primary or secondary, initiating transmissions without receiving permission

# Converged Protocols

“Convergence” is a recent network buzzword. It means providing services such as industrial controls, storage, and voice (that were delivered via non-IP devices and networks) via Ethernet and TCP/IP.

# DNP3

The Distributed Network Protocol (DNP3) provides an open standard primarily within the energy sector for interoperability between various vendors’ SCADA and smart grid applications. According to the US Department of Energy, “Smart grid” generally refers to a class of technology people who are bringing utility electricity delivery systems into the 21st century, using computer-based remote control and automation. These systems are made possible by two-way communication technology and computer processing that has been used for decades in other industries. They are beginning to be used on electricity networks, from the power plants and wind farms all

# 260 CHAPTER 5 Domain 4: Communication and Network Security

the way to the consumers of electricity in homes and businesses. They offer many benefits to utilities and consumers—mostly seen in big improvements in energy efficiency on the electricity grid and in the users' homes and offices [8].

Some protocols, as SMTP, fit into one layer. DNP3 is a multipayer protocol and may be carried via TCP/IP (another protocol): "Many vendors offer products that use TCP/IP to transport DNP3 messages in lieu of the media discussed above. Link layer frames, which we have not talked about yet, are embedded into TCP/IP packets. This approach has enabled DNP3 to take advantage of Internet technology and permitted economical data collection and control between widely separated devices" [9].

Recent improvements in DNP3 allow for "Secure Authentication," which addresses challenges with the original specification that could have allowed, for example, spoofing or replay attacks. DNP3 became an IEEE standard in 2010, called IEEE 1815-2010 (now deprecated). It allowed pre-shared keys only. IEEE 1815-2012 is the current standard; it supports Public Key Infrastructure (PKI).

# Storage Protocols

Fibre Channel over Ethernet (FCoE) and Internet Computer System Interface (iSCSI) are both Storage Area Network (SAN) protocols that provide cost-effective ways to leveraging network infrastructure technologies and protocols to interface with storage. A Storage Area Network allows block-level access across a network, like a directly attached drive. However fibre channel uses the Canadian/UK spelling of "fiber," while fiber optic cable uses the American spelling of "fiber."

FCoE leverages Fibre Channel, which has long been used for storage networking, but with the requirements for completely different cabling and hardware. Instead, FCoE can be transmitted across Ethernet networks. In FCoE, Fibre Channel's HBA (Host Bus Adapters), which were historically unique cards to interface with storage, are combined with the network interface (NIC) for economies of scale. FCoE uses Ethernet, but not TCP/IP. Fibre Channel over IP (FIP) encapsulates Fibre Channel frames via TCP/IP.

Like FCoE, iSCSI is a SAN protocol that allows for leveraging network infrastructure and protocols to interface with storage. Fibre uses Ethernet for communication and can be routed like any IP protocol (the same is for FCIP). By employing protocols beyond Layer 2 (Ethernet), iSCSI can be transmitted beyond the local network. Thus, iSCSI could allow even for accessing storage that resides across a WAN. iSCSI uses Logical Unit Numbers (LUNs) to provide a way of addressing storage across the network. LUNs can also be used for basic access control for network accessible storage.

# Virtual SAN

Storage Area Networks have historically tended to be proprietary and used dedicated hardware and protocols that did not easily interoperate. Though many implementations now leverage protocols such as FCoE, FCIP, or iSCSI that

# Network Architecture and Design 261

can allow for converged traditional networking technologies and protocols, the scalability and security of the Storage Area Networking has proven cumbersome.

Traditional approaches to storage security often required hard-coding changes to switches or the HBAs to achieve access control. One approach to a virtual SAN feels analogous to the switching of VLANs and tries allow for a conceptually simplistic isolation within the SAN. The concept of a virtual SAN is not limited to security concerns. Recent use of the virtual SAN as analogous to VLANs is commonly employed by networking.

Virtualization vendors employ the virtual SAN to imply an approach to the SAN that allows for more rapid provisioning of virtualized storage. Beyond provisioning, virtualization tour the virtual SAN as a means to afford simpler linear scalability to storage.

# VoIP

Voice over Internet Protocol (VoIP) carries voice via data networks, a fundamental change from analog POTS (Plain Old Telephone Service), which remains in use after 100 years. VoIP brings the advantages of packet-switched networks, such as lower cost and resiliency, to the telephone.

Recently, many organizations have maintained at least two distinct networks: a phone network and a data network, each with associated maintenance costs. The reliability of packet-switched data networks has grown as organizations have made substantial investments. With the advent of VoIP, many organizations have lowered costs by combining voice and data services on packet-switched networks.

Common VoIP protocols include Real-time Transport Protocol (RTP), which rely upon session and signaling protocols including SIP (Session Initiation Protocol, a signaling protocol) and H.323. SRTP (Real-time Transport Protocol) may be used to provide secure VoIP, including confidentiality, integrity, and security authentication.

While VoIP can provide cost advantages (especially for new sets, without a large voice investment), there are security concerns. If the network goes down, both voice and network data go down. Also, there is no true "out of band" channel for wired voice. If an attacker has compromised a network, may be able to compromise the confidentiality or integrity of the VoIP calls on that network. VoIP protocols, such as RTP, provide little or no security by sniffing with a tool like Wireshark (a high-quality free network protocol analyzer, as sees https://www.wireshark.org), selecting the "Telephony → VoIP Calls" menu, choosing a call and pressing "Player," as shown in Fig. 5.16.

Organizations that deploy VoIP must ensure reliability by making sufficient investments in their data networks, and in staff expertise to support them. In the event of network compromise, use other methods such as cell phones for
