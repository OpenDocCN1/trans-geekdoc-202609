# Exam Warning

Do not confuse 802.1X (EAP) with 802.11 (Wireless).

EAP addresses many issues, including the “roaming infected laptop” problem. A user with an infected laptop plugs into a typical office network and requests an IP address from a DHCP server. Once you get an IP, the malware installed on the laptop begins attacking other systems on the network.

By the time it is late to request an IP address, it is already in a position to cause harm on the network, including confidentiality, integrity, and availability attacks. This problem is most acute on WLANs (where an outside laptop 100 feet away from a building may be able to access the network). Ideally, authentication should be required before the laptop can join the network: EAP does exactly this.

Fig.3.2 shows Step 1 shows the Supplicant authenticating via EAPOL, Layer 2 EAP implementation. Step 2 shows the Authenticator receiving the EAPOL (EAP Over LAN) traffic and using RADIUS or Diameter to carry EAP traffic to the Authentication Server (AS). Step 3 shows the Authenticator allowing Supplicant access to the internal network after successful authentication.

There are many types of EAP, we will focus on EAP-MD5, EAP-FAST, EAP-TLS, EAP-TTLS, and PEAP:

+   - EAP-MD5 is one of the weakest forms of EAP. It offers client-server authentication (all other forms of EAP discussed in this section support mutual authentication of client and server); this makes it vulnerable to man-the-middle attacks. EAP-MD5 is also vulnerable to password cracking attacks.
- LEAP (Lightweight Extensible Authentication Protocol) is a Cisco-proprietary protocol released before 802.1X was finalized. LEAP has significant security flaws and should not be used.
- EAP-FAST (EAP-Flexible Authentication via Secure Tunneling) was designed by Cisco to replace LEAP. It uses a Protected Access Credential (PAC), which acts as a pre-shared key.

![](bbox=[0.156, 0.715, 0.718, 0.863])

FIG. 5.23 Successful 802.1X authentication.