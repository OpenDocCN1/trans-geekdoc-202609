# 33.4.2 Layer 1 Attacks.

Wireless mediums can be heavily relied upon by staff or business applications to provide connectivity to wired network resources in locations where physical connectivity is difficult to implement. The absence of an enclosed private physical medium allows for tampering of the layer 1 wireless carrier signal regardless of upper layer protective controls. This is a fundamental threat to any form of wireless communication and not necessarily specific to 802.11, although each wireless protocol such as CDMA, 3G, or 802.11 may include a mechanism to detect tampering, they cannot prevent it from occurring.

+   - The 802.11 protocol functions within 2.4 GHz band. The 2.4 Ghz consumer band can be interfered with by using something as simple as a microwave oven
+   - The 2.4 GHz spectrum only provides three nonoverlapping channels. The 802.11 spectrum runs between the range of 2.412 GHz and 2.462 GHz. Overlapping channels are side-by-side channels, which through propagation and other wireless tendencies, can bleed into the neighboring 20 MHz bandwidth allocation. A nearby AP can cause a minor denial of service condition by using an overlapping channel.
+   - Management frame spoofing
+   - 802.11 management frames are part of the MAC layer of the 802.11 protocol. Management frames are used to bootstrap the authentication and association of clients to an AP. Management frames “manage” the connection between an AP and all connected clients. There are various types of management frames, some of which are received by any client within range of the AP, and others which are targeted at connected/connecting clients.

Most significant management frame types:

+   - Probe Request/Response
+   - Authentication
+   - Association Request
+   - Association Response
+   - Dissociation

As with a wired LAN, the unauthenticated nature of initial data link layer protocols, such as 802.11 management frames, can allow an attacker to spoof and interfere with an existing session or the session initiation process. This fundamental issue is comparable to the unauthenticated Ethernet → IP ARP protocol, still vulnerable over 802.11, but easily abused across a wired connection.

The security afforded to wired bootstrap protocols relies on their physical controls, none of which are afforded to wireless. This void prompted IEEE 802.11 family of standards to adopt the 802.11w specification. This specification details the use of MICs to authenticate management frames to their source. This would effectively eliminate the ability for an unauthenticated attacker to force clients off of a legitimate AP to an attacker provided rogue AP. 802.11w sounds great on paper, but in reality, implementation will take years. The process of authenticating material for each management frame increases the load on an AP’s already busy processors, which means a software upgrade may not be feasible for all devices. In addition, all client devices must support 802.11w to create outgoing and process incoming MIC data. Client support would require new