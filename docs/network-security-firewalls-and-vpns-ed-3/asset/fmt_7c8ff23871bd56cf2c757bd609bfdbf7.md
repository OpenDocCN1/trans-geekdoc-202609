
## Module-based VPN

A module-based VPN runs as a component on a larger system. These are sometimes included as part of the overall feature set, or in other cases may require the purchase of additional licenses to use the VPN. An example of this would be the VPN capability included with many firewalls. Many routers also offer this type of capability, which permits the easy encryption of wide area network (WAN) links for security-conscious companies. The benefit of this type of VPN solution is reduced complexity of the environment, since you have fewer discrete devices to manage. VPN modules are also typically less expensive than hardware VPN solutions. Some vendors also offer hardware accelerators for improving overall performance of this solution.

## Hardware VPNs

Hardware VPNs are dedicated appliance-based solutions, generally based on a router-type platform. Hardware VPNs are the most common type of VPN deployed in corporations today. Although hardware VPNs can be complex to deploy, these devices are typically more scalable than software counterparts, and they can be easily deployed in a redundant manner. Hardware VPNs can increase the complexity of an environment, because you are deploying additional equipment. The good news is that you can usually manage this additional hardware with the same types of network management tools you use to manage the routers and switches in an environment.

Hardware VPNs can create some security issues, largely related to potential vulnerabilities in the VPN software code on the appliance. A number of security alerts related to VPN vulnerabilities have appeared in recent years. Fortunately, you can manage this issue fairly easily by keeping current on your vendor’s security alerts and by upgrading VPN code in a timely fashion. If your organization does not have the skills or ability to test the solution thoroughly, it might be preferable to run the `N–1` version of code, where `N` is the current version of code, unless a known issue with that previous version of the code has been published.

Ultimately, the requirements of your business will drive your selection of a software or hardware VPN. The good news is that many options are available for every size network.

### NOTE

You must make a risk-based decision on whether to accept the possibility of undiscovered bugs in a new version of hardware or to live with the known bugs in a previous version. If an upgrade is issued primarily for fixing security flaws, you may be better off with the new version, surprises and all.

## Differences Between Layer 2 and Layer 3 VPNs

One distinguishing component of current VPNs is the use of a variety of transport protocols to establish connections. This is helpful not only because the protocols have different capabilities, encryption strengths, and authentication mechanisms, but because each can run at different layers of the Open Systems Interconnection (OSI) Reference Model. The OSI model is the standard seven-layer conceptual tool that describes protocols and their corresponding functions. Each layer communicates with its peer layer on the other end of a communication session. Although the OSI model is helpful in discussing protocols, most protocols are not in full compliance with it.

In the case of VPNs, the protocols used by the vast majority of solutions work at Layers 2 and 3 of the OSI model.

Layer 2 of the OSI model is the Data Link Layer. The Data Link Layer is the protocol layer that transfers data between adjacent network nodes. In the case of a VPN, this protocol transfers data from one VPN endpoint to the other. Layer 2 Transport Protocol (L2TP) is an example of a protocol that communicates using Layer 2. Layer 3 of the OSI model is the Network Layer. The Network Layer is responsible for end-to-end packet delivery and includes the ability to route packets through intermediate hosts. IPSec is an example of a VPN protocol that communicates at Layer 3.

### Technical TIP

SSL/TLS and SSH are protocols that operate at Layer 7 of the OSI model, the Application Layer.

### Technical TIP

An RFC is a [Request for Comments](#30_glossary.xhtml#gloss402). These “requests” are published by the [Internet Engineering Task Force (IETF)](#30_glossary.xhtml#gloss250). The IETF is the standards body for Internet-related engineering specifications. The IETF uses RFCs as a mechanism to define Internet-related standards. (See [www.ietf.org](http://www.ietf.org) for more information.)

## Internet Protocol Security (IPSec)

Internet Protocol Security (IPSec) is a standards-based protocol suite designed specifically for securing Internet Protocol (IP) communications. IPSec authenticates and encrypts each IP packet in an IP data stream. In addition, IPSec has protocols that can establish mutual authentication and cryptographic key negotiation during a session. IPSec operates at the Network Layer (Layer 3) of the OSI model.

The IPSec standard utilizes three major components:

1.  Authentication Header (AH)
2.  Encapsulating Security Payload (ESP)
3.  Internet Key Exchange (IKE)

[Authentication Header (AH)](#30_glossary.xhtml#gloss37) provides integrity protection for packet headers and data, as well as user authentication. It can optionally provide replay protection and access protection. AH cannot encrypt any portion of a packet. In the initial version of IPSec, the ESP protocol could provide only encryption, not authentication, so AH and ESP were often used together to provide both confidentiality and integrity protection for communications. Because authentication capabilities were added to ESP in the second version of IPSec, AH has become less significant; in fact, some IPSec software no longer supports AH. However, AH is still of value because AH can authenticate portions of packets that ESP cannot. Also, many existing IPSec implementations use AH.

[Encapsulating Security Payload (ESP)](#30_glossary.xhtml#gloss159) is the second core IPSec security protocol. In the initial version of IPSec, ESP provided only encryption for packet payload data. Integrity protection was provided by the AH protocol if needed. In the second version of IPSec, ESP became more flexible. It can perform authentication to provide integrity protection, although not for the outermost IP header.

### Technical TIP

Why does the layer matter? Because IPSec operates at Layer 3 of the OSI model, it can encrypt any traffic in Layers 4 through 7 of the OSI model. That means IPSec can be used to encrypt any application traffic.

### NOTE

IPSec supports the Data Encryption Standard (DES), a 56-bit encryption protocol, and 3DES, which effectively yields a 168-bit encryption protocol. (In 3DES, pronounced “triple DES,” data is encrypted three times using DES.)

Therefore, in all but the oldest IPSec implementations, ESP can provide encryption only, encryption and integrity protection, or integrity protection only. This chapter mainly addresses the features and characteristics of the second version of ESP.

[Internet Key Exchange (IKE)](#30_glossary.xhtml#gloss251) negotiates, creates, and manages security associations. Security association (SA) is a generic term for a set of values that define the IPSec features and protections applied to a connection. You can also create SAs manually, using values agreed upon in advance by both parties, but because these SAs cannot be updated, this method does not scale for real-life large-scale VPNs. In IPSec, IKE provides a secure mechanism for establishing IPSec-protected connections.

IPSec supports two different modes:

*   **Transport mode (host-to-host)**—In transport mode, only the data packet payload is encapsulated, while the packet header is left intact. In this mode, the destination host decapsulates the packet. This is the mode used in a Windows environment to secure a client-to-server connection using IPSec.
