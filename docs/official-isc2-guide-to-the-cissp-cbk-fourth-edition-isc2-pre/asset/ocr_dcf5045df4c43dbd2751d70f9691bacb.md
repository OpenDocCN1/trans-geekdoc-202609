value (hash) of the ESP packet. As with the AH, the authentication algorithm is negotiated when the end points establish their security association.

# Security Associations

A security association (SA) defines the mechanisms that an end point will use to communicate with its partner. All SAs cover transmissions in one direction only. A second SA must be defined for two-way communication. Mechanisms that are defined in the SA include the encryption and authentication algorithms, and whether to use the AH or ESP protocol. Deferring the mechanisms to the SA, as opposed to specifying them in the protocol, allows the communicating partners to use the appropriate mechanisms based on situational risk.

# Transport Mode and Tunnel Mode

End points communicate with IPSec using either transport or tunnel mode. In transport mode, the IP payload is protected. This mode is mostly used for end-to-end protection, for example, between client and server. In tunnel mode, the IP payload and its IP header are protected. The entire protected IP packet becomes a payload of a new IP packet and header. Tunnel mode is often used between networks, such as with firewall-to-firewall VPNs.

# Internet Key Exchange (IKE)

Internet key exchange allows communicating partners to prove their identity to each other and establish a secure communication channel, and it is applied as an authentication component of IPSec. IKE uses two phases:

+   - **Phase 1** — In this phase, the partners authenticate with each other, using one of the following:
+     - **Shared Secret** — A key that is exchanged by humans via telephone, fax, encrypted email, etc.
+     - **Public Key Encryption** — Digital certificates are exchanged.
+     - **Revised Mode of Public Key Encryption** — To reduce the overhead of public key encryption, a nonce (a Cryptographic function that refers to a number or bit string used only once, in security engineering) is encrypted with the communicating partner’s public key, and the peer’s identity is encrypted with symmetric encryption using the nonce as the key.

Next, IKE establishes a temporary security association and secure tunnel to protect