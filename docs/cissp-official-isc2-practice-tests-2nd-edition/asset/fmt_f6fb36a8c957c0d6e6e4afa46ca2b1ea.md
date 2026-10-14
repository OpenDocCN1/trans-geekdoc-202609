
## 26. B
ARP and RARP operate at the Data Link layer, the second layer of the OSI model. Both protocols deal with physical hardware addresses, which are used above the Physical layer (layer 1) and below the Network layer (layer 3), thus falling at the Data Link layer.

## 27. D
iSCSI is a converged protocol that allows location-independent file services over traditional network technologies. It costs less than traditional Fibre Channel. VoIP is Voice over IP, SDN is software-defined networking, and MPLS is Multiprotocol Label Switching, a technology that uses path labels instead of network addresses.

## 28. A
A repeater or concentrator will amplify the signal, ensuring that the 100-meter distance limitation of 1000BaseT is not an issue. A gateway would be useful if network protocols were changing, while Cat7 cable is appropriate for a 10Gbps network at much shorter distances. STP cable is limited to 155 Mbps and 100 meters, which would leave Chris with network problems.

## 29. B
The use of TCP port 80 indicates that the messaging service is using the HTTP protocol. Slack is a messaging service that runs over HTTPS, which uses port 443. SMTP is an email protocol that uses port 25.

## 30. C
HTTP traffic is typically sent via TCP 80. Unencrypted HTTP traffic can be easily captured at any point between A and B, meaning that the messaging solution chosen does not provide confidentiality for the organization’s corporate communications.

## 31. B
If a business need requires messaging, using a local messaging server is the best option. This prevents traffic from traveling to a third-party server and can offer additional benefits such as logging, archiving, and control of security options like the use of encryption.

## 32. B
Multilayer protocols create three primary concerns for security practitioners: They can conceal covert channels (and thus covert channels are allowed), filters can be bypassed by traffic concealed in layered protocols, and the logical boundaries put in place by network segments can be bypassed under some circumstances. Multilayer protocols allow encryption at various layers and support a range of protocols at higher layers.

## 33. C
A bus can be linear or tree-shaped and connects each system to trunk or backbone cable. Ethernet networks operate on a bus topology.

## 34. B
When a workstation or other device is connected simultaneously to both a secure and a nonsecure network like the Internet, it may act as a bridge, bypassing the security protections located at the edge of a corporate network. It is unlikely that traffic will be routed improperly leading to the exposure of sensitive data, as traffic headed to internal systems and networks is unlikely to be routed to the external network. Reflected DDoS attacks are used to hide identities rather than to connect through to an internal network, and security administrators of managed systems should be able to determine both the local and wireless IP addresses his system uses.

## 35. A
Wardriving and warwalking are both processes used to locate wireless networks, but are not typically as detailed and thorough as a site survey, and `design map` is a made-up term.

## 36. C
The DARPA TCP/IP model was used to create the OSI model, and the designers of the OSI model made sure to map the OSI model layers to it. The Application layer of the TCP model maps to the Application, Presentation, and Session layers, while the TCP and OSI models both have a distinct Transport layer.

## 37. B
ARP cache poisoning occurs when false ARP data is inserted into a system’s ARP cache, allowing the attacker to modify its behavior. `RARP flooding`, `denial of ARP attacks`, and `ARP buffer blasting` are all made-up terms.

## 38. C
The process of using a fake MAC (Media Access Control) address is called spoofing, and spoofing a MAC address already in use on the network can lead to an address collision, preventing traffic from reaching one or both systems. Tokens are used in token ring networks, which are outdated, and EUI refers to an Extended Unique Identifier, another term for MAC address, but token loss is still not the key issue. Broadcast domains refers to the set of machines a host can send traffic to via a broadcast message.

## 39. D
Direct Inward System Access uses access codes assigned to users to add a control layer for external access and control of the PBX. If the codes are compromised, attackers can make calls through the PBX or even control it. Not updating a PBX can lead to a range of issues, but this question is looking for a DISA issue. Allowing only local calls and using unpublished numbers are both security controls and might help keep the PBX more secure.

## 40. D
Application-specific protocols are handled at layer 7, the Application layer of the OSI model.

## 41. D
Ping uses ICMP, the Internet Control Message Protocol, to determine whether a system responds and how many hops there are between the originating system and the remote system. Lauren simply needs to filter out ICMP to not see her pings.

## 42. D
802.1x provides port-based authentication and can be used with technologies like EAP, the Extensible Authentication Protocol. 802.11a is a wireless standard, 802.3 is the standard for Ethernet, and 802.15.1 was the original Bluetooth IEEE standard.

## 43. D
1000BaseT is capable of a 100-meter run according to its specifications. For longer distances, a fiber-optic cable is typically used in modern networks.

## 44. C
PRI, or Primary Rate Interface, can use between 2 and 23 64 Kbps channels, with a maximum potential bandwidth of 1.544 Mbps. Actual speeds will be lower due to the D channel, which can’t be used for actual data transmission, but PRI beats BRI’s two B channels paired with a D channel for 144 Kbps of bandwidth.

## 45. C
SPIT stands for Spam over Internet Telephony and targets VoIP systems.

## 46. D
Bluesnarfing targets the data or information on Bluetooth-enabled devices. Bluejacking occurs when attackers send unsolicited messages via Bluetooth.

## 47. C
Layer 6, the Presentation layer, transforms data from the Application layer into formats that other systems can understand by formatting and standardizing the data. That means that standards like JPEG, ASCII, and MIDI are used at the Presentation layer for data. TCP, UDP, and TLS are used at the Transport layer; NFS, SQL, and RPC operate at the Session layer; and HTTP, FTP, and SMTP are Application layer protocols.

## 48. D
Fully connected mesh networks provide each system with a direct physical link to every other system in the mesh. This is very expensive but can provide performance advantages for specific types of computational work.

## 49. C
PPTP, L2F, L2TP, and IPsec are the most common VPN protocols. TLS is also used for an increasingly large percentage of VPN connections and may appear at some point in the CISSP exam. PPP is a dial-up protocol, LTP is not a protocol, and SPAP is the Shiva Password Authentication Protocol sometimes used with PPTP.

## 50. C
FDDI, or Fiber Distributed Data Interface, is a token-passing network that uses a pair of rings with traffic flowing in opposite directions. It can bypass broken segments by dropping the broken point and using the second, unbroken ring to continue to function. Token Ring also uses tokens, but it does not use a dual loop. SONET is a protocol for sending multiple optical streams over fiber, and a ring topology is a design, not a technology.

## 51. C
The Physical layer includes electrical specifications, protocols, and standards that allow control of throughput, handling line noise, and a variety of other electrical interface and signaling requirements. The OSI layer doesn’t have a Device layer. The Transport layer connects the Network and Session layers, and the Data Link layer packages packets from the network layer for transmission and receipt by devices operating on the Physical layer.
