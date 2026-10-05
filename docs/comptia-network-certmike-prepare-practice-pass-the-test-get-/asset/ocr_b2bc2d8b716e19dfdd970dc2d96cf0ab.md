# Preshared Keys (PSKs)

A preshared key (PSK) is an alphanumeric text string most commonly used for encrypting wireless network traffic protected by the Wi-Fi Protected Access (WPA) and WPA2 security protocols. Protocols use PSKs for symmetrical encryption, in which the same key encrypts and decrypts data. This is in contrast to systems that use public key cryptography, which uses public and private keys.

WPA and WPA2, in their PSK modes, also use the same preshared key for all of the network users connecting to the wireless access point, which may compromise the security of the entire system by sharing the PSK with unauthorized people. For more information on WPA and WPA2, see "Encryption Standards" in Chapter 12, "Wireless Standards."

# Enterprise Authentication

Because the use of a single shared key for all of the network users is inherently insecure, even the smallest SOHO networks use some form of enterprise-based authentication that does not rely on PSK encryption. There are several alternatives to PSK, including the enterprise version of WPA/WPA2 and EAP, as discussed in the following sections.

# WPA/WPA2 Enterprise

In addition to its PSK mode, WPA and WPA2 have an Enterprise mode, which does not rely on shared keys. WPA/WPA2 Enterprise uses the 802.1X authentication protocol with a separate authentication server, usually running Remote Authentication Dial-In User Service (RADIUS).

# EAP

Extensible Authentication Protocol (EAP) is not really a protocol at all, but rather a framework for a protocol. EAP extends the 802.1X framework to support a variety of authentication mechanisms that can protect a network with different levels of hardening, including swipe cards, fingerprints, and other forms of biometrics, as well as passwords. There are many protocols that use the EAP framework, including Protected Extensible Authentication Protocol (PEAP), which encapsulates EAP within an encrypted TLS tunnel, and Extensible Authentication Protocol – Transport Layer Security (EAP-TLS), used on wireless networks.

# Geofencing

Geofencing is a technique for limiting access to a network, system, or service based on the geographic location of the client, as specified by global positioning system (GPS) or radio-frequency identification (RFID) chips. There are several ways in which networks can use this technology. Users within a specified virtual boundary can be permitted access to the