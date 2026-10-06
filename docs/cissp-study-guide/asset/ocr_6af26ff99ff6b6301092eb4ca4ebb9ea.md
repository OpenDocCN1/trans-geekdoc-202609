# 282 CHAPTER 5 Domain 4: Communication and Network Security

+   - EAP-TLS (EAP-Transport Layer Security) uses PKI requiring both server-side and client-side certificates. EAP-TLS establishes a secure TLS tunnel for authentication. EAP-TLS is very secure due to the use of PKI but is complex and costly for the same reason. The other major versions of EAP attempt to create the same TLS tunnel without requiring a client-side certificate.
- EAP-TTLS (EAP Tunneled Transport Layer Security), developed by Funk Soft and Cisco, simplifies EAP-TLS by dropping the client-side requirement, allowing other authentication methods (such as password) for client-side authentication. EAP-TTLS is thus easier to deploy than EAP-TLS, but less secure when omitting the client-side certificate.
- PEAP (Protected EAP), developed by Cisco Systems, Microsoft, and RSA Security, is like (and may be considered a competitor to) EAP-TTLS, including not requiring client-side certificates.

# VPN

Virtual Private Networks (VPNs) secure data via insea networks such as the Internet. The goal is to provide the privacy provided by a circuit such as a TI, virtually. The nuts and bolts of VPNs involve secure authentication, cryptographic hashes using SHA-1 to provide integrity, and ciphers as AES to provide confidentiality.

> The cryptographic details of the VPN protocols discussed here are covered in depth in Chapter 4, Domain 3: Security Architecture and Engineering.

# SLIP and PPP

SLIP (Serial Line Protocol) is a Layer 2 protocol that provides IP connectivity via asynchronous connections as serial lines and modems. When SLIP was first introduced in 1988, it allowed routing packets via modem links for the first time (previously, modems were primarily used for non-terminal access). SLIP is a bare-bones protocol that provides no built-in confidentiality, integrity, or authentication. SLIP has largely faded from use, replaced with PPP.
PPP (Point-to-Point Protocol) is a Layer 2 protocol that has largely replaced PPP. SLIP is based on HDLC (discussed previously), and adds confidentiality, integrity, and authentication via point-to-point links. PPP supports synchronous links (such as T1) in asynchronous links such as modems.

# PPTP and L2TP

PPTP (Point-to-Point Tunneling Protocol) tunnels PPP via IP. A consortium of vendors, including Microsoft, 3COM, and others, developed it. PPTP uses GRE (Generic Routing Encapsulation) to pass PPP via IP and uses TCP for a control channel (using TCP port 1723).