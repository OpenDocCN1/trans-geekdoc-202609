
bombarding members through the internal messaging systems directly.

## Tunneling Firewalls and Other Restrictions

Similar to streaming audio and video applications, corporate firewalls were perceived as an obstacle in establishing direct contact with Internet peers. The easy, but arguably illegitimate, solution for developers was to enable tunneling through the protocol that would always be available, HTTP.

Depending on the client, it can even be possible to enable incoming connections by polling an external server. (This technique has been widely exploited in another type of application, a certain kind of remote-access software.) Control of HTTP tunneling can happen on the firewall or the proxy server. It should, however, be considered that in the case of peer-to-peer protocols, this would require a "deny by default" policy, and blocking instant messaging without providing a legitimate alternative is not likely to foster user acceptance and might give users incentive to utilize even more dangerous workarounds.

It should be noted that inbound file transfers can also result in circumvention of policy or restrictions in place, in particular for the spreading of viruses. An effective countermeasure can be found in on-access anti-virus scanning on the client, which should be enabled anyway.

## Remote Access

### VPN

### Virtual Private Network (VPN)

A VPN (Figure 4.15) is an encrypted tunnel between two hosts that allows them to securely communicate over an untrusted network; e.g., the Internet. Remote users employ VPNs to access their organization’s network, and depending on the VPN’s implementation, they may have most of the same resources available to them as if they were physically at the office. As an alternative to expensive dedicated point-to-point connections, organizations use gateway-to-gateway VPNs to securely transmit information over the Internet between sites or even with business partners.

### IPSec Authentication and Confidentiality for VPNs

IP Security (IPSec) is a suite of protocols for communicating securely with IP by providing mechanisms for authentication and encryption. Implementation of IPSec is mandatory in IPv6, and many organizations are using it over IPv4. Further, IPSec can be implemented in two modes: one that is appropriate for end-to-end protection and one that safeguards traffic between networks.

Standard IPSec only authenticates hosts with each other. If an organization requires users to authenticate, they must employ a nonstandard proprietary IPSec implementation or use IPSec over L2TP (Layer 2 Tunneling Protocol). The latter approach uses L2TP to authenticate the users and encapsulate IPSec packets within an L2TP tunnel.

Because IPSec interprets the change of IP address within packet headers as an attack, NAT does not work well with IPSec. To resolve the incompatibility of the two protocols, NAT-Transversal (a.k.a. NAT-T) encapsulates IPSec within UDP port 4500 (see RFC 3948 for details).39

**Example A**

![](img/3be1e4f35d99b14a974b22ecf8355b5e_743_0.png)

**Example B**

![](img/3be1e4f35d99b14a974b22ecf8355b5e_743_1.png)

**Example C**

![](img/3be1e4f35d99b14a974b22ecf8355b5e_743_2.png)

**Example D**

![](img/3be1e4f35d99b14a974b22ecf8355b5e_743_3.png)

Figure 4.15 – VPN Types

- Example A: Two hosts establish secure peer communications over the Internet.
- Example B illustrates a typical gateway-to-gateway VPN with the VPN terminating at the gateways to provide connectivity for internal hosts.
- **Example C** combines Examples A and B to allow secure communications from host to host in an existing gateway-to-gateway VPN.
- **Example D** details the situation when a remote host connects to an ISP, receives an IP address, and then establishes a VPN with the destination network's gateway. A tunnel is established to the gateway, and then a tunnel- or transport-mode communication is established to the internal system. In this example, it is necessary for the remote system to apply the transport header prior to the tunnel header. Also, it will be necessary for the gateway to allow IPSec connectivity and key management protocols from the Internet to the internal system.

> (From Tiller, J.S., **IPSec virtual private networks**, **Information Security Management Handbook**, 6th edn., Tipton H.F., and Krause, M. Eds., Auerbach Publications, Boca Raton, FL, 2005. With permission.)

### Authentication Header (AH)

The authentication header is used to prove the identity of the sender and ensure that the transmitted data has not been tampered with. Before each packet (headers + data) is transmitted, a hash value of the packet’s contents (except for the fields that are expected to change when the packet is routed) based on a shared secret is inserted in the last field of the AH. The end points negotiate which hashing algorithm to use and the shared secret when they establish their security association. To help thwart replay attacks (when a legitimate session is retransmitted to gain unauthorized access), each packet that is transmitted during a security association has a sequence number, which is stored in the AH. In transport mode, the AH is shimmed between the packet’s IP and TCP header. The AH helps ensure integrity, not confidentiality. Encryption is implemented through the use of encapsulating security payload (ESP).

### Encapsulating Security Payload (ESP)

The encapsulating security payload encrypts IP packets and ensures their integrity. ESP contains four sections:

- ESP header: Contains information showing which security association to use and the packet sequence number. Like the AH, the ESP sequences every packet to thwart replay attacks.
- ESP payload: The payload contains the encrypted part of the packet. If the encryption algorithm requires an initialization vector (IV), it is included with the payload. The end points negotiate which encryption to use when the security association is established. Because packets must be encrypted with as little overhead as possible, ESP typically uses a symmetric encryption algorithm.
- ESP trailer: May include padding (filler bytes) if required by the encryption algorithm or to align fields.
- Authentication: If authentication is used, this field contains the integrity check value (hash) of the ESP packet. As with the AH, the authentication algorithm is negotiated when the end points establish their security association.

### Security Associations

A security association (SA) defines the mechanisms that an end point will use to communicate with its partner. All SAs cover transmissions in one direction only. A second SA must be defined for two-way communication. Mechanisms that are defined in the SA include the encryption and authentication algorithms, and whether to use the AH or ESP protocol. Deferring the mechanisms to the SA, as opposed to specifying them in the protocol, allows the communicating partners to use the appropriate mechanisms based on situational risk.

### Transport Mode and Tunnel Mode

End points communicate with IPSec using either transport or tunnel mode. In transport mode, the IP payload is protected. This mode is mostly used for end-to-end protection, for example, between client and server. In tunnel mode, the IP payload and its IP header are protected. The entire protected IP packet becomes a payload of a new IP packet and header. Tunnel mode is often used between networks, such as with firewall-to-firewall VPNs.

### Internet Key Exchange (IKE)

Internet key exchange allows communicating partners to prove their identity to each other and establish a secure communication channel, and it is applied as an authentication component of IPSec. IKE uses two phases:

- **Phase 1** — In this phase, the partners authenticate with each other, using one of the following:
  - **Shared Secret** — A key that is exchanged by humans via telephone, fax, encrypted email, etc.
  - **Public Key Encryption** — Digital certificates are exchanged.
  - **Revised Mode of Public Key Encryption** — To reduce the overhead of public key encryption, a nonce (a cryptographic function that refers to a number or bit string used only once, in security engineering) is encrypted with the communicating partner’s public key, and the peer’s identity is encrypted with symmetric encryption using the nonce as the key.

Next, IKE establishes a temporary security association and secure tunnel to protect
