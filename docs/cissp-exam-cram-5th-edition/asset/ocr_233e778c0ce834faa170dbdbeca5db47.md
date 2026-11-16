hashing functions and who captures the exchange can use a dictionary attack in an attempt to defeat the mechanism. CHAP was specifically created to defeat replay attacks because the challenge would vary with each client request, and reauthentication could be periodically demanded by the server.

# Extensible Authentication Protocol (EAP)

EAP makes PPP more robust by adding the capability to implement a variety of authentication mechanisms, including digital certificates, token cards, and MD5-Challenge-Response. EAP is used with 802.1X and implemented in amendments, such as 802.11i, WPA Enterprise, and WPA2 Enterprise.

When EAP is used by wireless devices to authenticate end users or devices, the client (supplicant) initiates the EAP request to the wireless access point (authenticator) that is responsible for keeping the network port closed until the authentication process completes successfully. The authenticator becomes a proxy, forwarding requests and replies between the supplicant and the authenticating server (RADIUS, TACACS+, and so on). During this protected series of frames, usually inside an encrypted tunnel, a pairwise master key (PMK) is developed between the supplicant and the authenticating server. If the authentication exchange is successful, the authenticating server delivers the PMK to the access point. The PMK is used to develop transient AES or TKIP encryption keys for the duration of the client’s session.

Table 5.15 summarizes some of the types of EAP.

# TABLE 5.15 EAP Types

| E | Se | Description |
|---|---|---|
| A | cu | |
| P | rit | |
| T | y | |
| y | St | |
| p | at | |
| e | us | |
| E | W | LEAP (Lightweight Extensible Authentication Protocol) is a |
| A | ea | Cisco-proprietary protocol released before 802.1X was finalized. |
| P | -k | LEAP has significant security flaws and should not be used. |