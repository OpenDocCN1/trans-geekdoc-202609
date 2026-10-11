
## Authenticator

Authenticator: a device such as an access point that allows a supplicant to authenticate and connect.

### Exam Warning

Do not confuse `802.1X` (EAP) with `802.11` (Wireless).

EAP addresses many issues, including the "roaming infected laptop" problem. A user with an infected laptop plugs into a typical office network and requests an IP address from a DHCP server. Once given an IP, the malware installed on the laptop begins attacking other systems on the network.

By the time the laptop is able to request an IP address, it is already in a position to cause harm on the network, including confidentiality, integrity, and availability attacks. This problem is most acute on WLANs (where an outside laptop 100 feet away from a building may be able to access the network). Ideally, authentication should be required before the laptop can join the network: EAP does exactly this.

[Fig. 5.23](#Ch005_225-293_B9780443187346000039.xhtml#f0120) shows a supplicant successfully authenticating and connecting to an internal network. Step 1 shows the Supplicant authenticating via `EAPOL` (*EAP Over LAN*), a Layer 2 EAP implementation. Step 2 shows the Authenticator receiving the `EAPOL` traffic and using `RADIUS` or `Diameter` to carry EAP traffic to the Authentication Server (AS). Step 3 shows the Authenticator allowing Supplicant access to the internal network after successful authentication.

![Fig. 5.23 Successful 802.1X authentication.](images/B9780443187346000039/f05-23-9780443187346.jpg)

[Fig. 5.23](#Ch005_225-293_B9780443187346000039.xhtml#B-f0120) Successful 802.1X authentication.

There are many types of EAP; we will focus on `EAP-MD5`, `LEAP`, `EAP-FAST`, `EAP-TLS`, `EAP-TTLS`, and `PEAP`:

*   **EAP-MD5** is one of the weakest forms of EAP. It offers client-server authentication only (all other forms of EAP discussed in this section support mutual authentication of client and server); this makes it vulnerable to man-in-the-middle attacks. `EAP-MD5` is also vulnerable to password cracking attacks.
*   **LEAP** (*Lightweight Extensible Authentication Protocol*) is a Cisco-proprietary protocol released before `802.1X` was finalized. `LEAP` has significant security flaws and should not be used.
*   **EAP-FAST** (*EAP-Flexible Authentication via Secure Tunneling*) was designed by Cisco to replace `LEAP`. It uses a *Protected Access Credential* (PAC), which acts as a pre-shared key.
*   **EAP-TLS** (*EAP-Transport Layer Security*) uses PKI, requiring both server-side and client-side certificates. `EAP-TLS` establishes a secure TLS tunnel used for authentication. `EAP-TLS` is very secure due to the use of PKI but is complex and costly for the same reason. The other major versions of EAP attempt to create the same TLS tunnel without requiring a client-side certificate.
*   **EAP-TTLS** (*EAP Tunneled Transport Layer Security*), developed by Funk Software and Certicom, simplifies `EAP-TLS` by dropping the client-side certificate requirement, allowing other authentication methods (such as password) for client-side authentication. `EAP-TTLS` is thus easier to deploy than `EAP-TLS`, but less secure when omitting the client-side certificate.
*   **PEAP** (*Protected EAP*), developed by Cisco Systems, Microsoft, and RSA Security, is like (and may be considered a competitor to) `EAP-TTLS`, including not requiring client-side certificates.

## VPN

Virtual Private Networks (VPNs) secure data sent via insecure networks such as the Internet. The goal is to provide the privacy provided by a circuit such as a T1, virtually. The nuts and bolts of VPNs involve secure authentication, cryptographic hashes such as `SHA-1` to provide integrity, and ciphers such as `AES` to provide confidentiality.

> **Note**
> The cryptographic details of the VPN protocols discussed here are covered in depth in [Chapter 4](#Ch004_107-223_B9780443187346000076_1.xhtml), Domain 3: Security Architecture and Engineering.

### SLIP and PPP

`SLIP` (Serial Line Internet Protocol) is a Layer 2 protocol that provides IP connectivity via asynchronous connections such as serial lines and modems. When `SLIP` was first introduced in 1988, it allowed routing packets via modem links for the first time (previously, modems were primarily used for non-routed terminal access). `SLIP` is a bare-bones protocol that provides no built-in confidentiality, integrity, or authentication. `SLIP` has largely faded from use, replaced with `PPP`.

`PPP` (Point-to-Point Protocol) is a Layer 2 protocol that has largely replaced `SLIP`. `PPP` is based on `HDLC` (discussed previously), and adds confidentiality, integrity, and authentication via point-to-point links. `PPP` supports synchronous links (such as T1s) in addition to asynchronous links such as modems.

### PPTP and L2TP

`PPTP` (Point-to-Point Tunneling Protocol) tunnels `PPP` via IP. A consortium of vendors, including Microsoft, 3COM, and others, developed it. `PPTP` uses `GRE` (Generic Routing Encapsulation) to pass `PPP` via IP and uses TCP for a control channel (using TCP port 1723).

`L2TP` (Layer 2 Tunneling Protocol) combines `PPTP` and `L2F` (Layer 2 Forwarding, designed to tunnel `PPP`). `L2TP` focuses on authentication and does not provide confidentiality: it is frequently used with `IPsec` to provide encryption. Unlike `PPTP`, `L2TP` can also be used on non-IP networks, such as ATM.

### IPsec

`IPv4` has no built-in confidentiality; higher-layer protocols such as `TLS` are used to provide security. To address this lack of security at Layer 3, `IPsec` (Internet Protocol Security) was designed to provide confidentiality, integrity, and authentication via encryption for `IPv6`. `IPsec` has been ported to `IPv4`. `IPsec` is a suite of protocols; the major two are Encapsulating Security Protocol (`ESP`) and Authentication Header (`AH`). Each has an IP protocol number: `ESP` is protocol 50; `AH` is protocol 51.

> **Note**
> This chapter describes the network aspects of `IPsec`, `SSL`, and `TLS`: see [Chapter 4](#Ch004_107-223_B9780443187346000076_1.xhtml), Domain 3: Security Architecture and Engineering, for the cryptographic aspects of these protocols.

#### IPsec Architectures

`IPsec` has three architectures: host-to-gateway, gateway-to-gateway, and host-to-host. Host-to-gateway mode (also called client mode) is used to connect one system that runs `IPsec` client software to an `IPsec` gateway. Gateway-to-gateway (also called point-to-point) connects two `IPsec` gateways, which form an `IPsec` connection that acts as a shared routable network connection, like a T1. Finally, host-to-host mode connects two systems (such as file servers) to each other via `IPsec`. Many modern operating systems, such as Windows 10 or Ubuntu Linux, can run `IPsec` natively, allowing them to form host-to-gateway or host-to-host connections.

#### Tunnel and Transport Mode

`IPsec` can be used in tunnel mode or transport mode. Tunnel mode provides confidentiality (`ESP`) and/or authentication (`AH`) to the entire original packet, including the original IP headers. New IP headers are added (with the source and destination addresses of the `IPsec` gateways). Transport mode protects the IP data (layers 4–7) only, leaving the original IP headers unprotected. Both modes add extra `IPsec` headers (an `AH` header and/or an `ESP` header). [Fig. 5.24](#Ch005_225-293_B9780443187346000039.xhtml#f0125) shows the differences between tunnel and transport modes.

![Fig. 5.24 IPsec tunnel and transport modes.](images/B9780443187346000039/f05-24-9780443187346.jpg)

[Fig. 5.24](#Ch005_225-293_B9780443187346000039.xhtml#B-f0125) IPsec tunnel and transport modes.

### SSL and TLS

Secure Sockets Layer (`SSL`) was designed to protect HTTP (Hypertext Transfer Protocol) data: HTTPS uses TCP port 443. `TLS` (Transport Layer Security) 1.0 was equivalent to `SSL` version 3.1. The current version of `TLS` is 1.3, described in RFC 8446 (see [https://datatracker.ietf.org/doc/html/rfc8446](https://datatracker.ietf.org/doc/html/rfc8446)).
