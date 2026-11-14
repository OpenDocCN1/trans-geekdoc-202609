# - Tunnel mode:

+   - the integrality of the original IP packet is protected;
+   - IPSec encapsulates the original packet, encrypts it, adds a new IP header and then sends it to the other side of the VPN tunnel;
+   - tunnel mode is most commonly used between IPsec gateways (Cisco routers or ASA firewalls).

# 9.2. IKE protocol

# 9.2.1. Introduction

Internet Key Exchange (IKE) is a protocol used to dynamically negotiate the security settings associated with IPSec communication. It must be noted that an IPsec implementation can also support the manual management of this exchange of settings. However, the IKE protocol is considered faster and more secure.

IKE is available in two versions. The version v2 offers several advantages, including, among others, the fixing of vulnerabilities in IKEv1 and optimal bandwidth use.

# 9.2.2. Components of IKE

IKE is the combination of three protocols, namely: ISAKMP, SKEME and Oakley. These protocols are grouped together to ensure negotiation and the establishment of a secured communication.

+   - ISAKMP: makes it possible to negotiate SAs between two ends of an IPsec communication.
+   - Oakley: uses the Diffie-Hellman algorithm to carry out key exchanges between both sides of the IPsec connection.
+   - SKEME: defines key exchange techniques that ensure anonymity and non-repudiation.

# 9.2.3. IKE phases

The IKE protocol operates in two main phases to create a secured communication channel between the two IPsec points. The first phase makes it possible to negotiate the tunnel security settings, while the second phase ensures the secured transmission of data.