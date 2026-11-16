HTTP over TLS.

+   Secure Socket Tunneling Protocol (SSTP): SSTP is a form of VPN tunnel that was released in 2008 and provides a mechanism to transport PPP or L2TP traffic through an SSLv3 connection. SSTP requires a digital certificate on the server side and establishes an SSL tunnel that encrypts all traffic over TCP port 443. Because it uses the same port used by HTTPS, it can be used through corporate firewalls.

+   Wireless Transport Layer Security (WTLS): WTLS is a security protocol developed for cellular technology. In an attempt to minimize upper-layer support code, the cellular industry developed its own Wireless Application Protocol (WAP) stack. WTLS encrypts the communication between the cellular wireless client and the ISP tower that the cell phone is connecting to. At the tower, the WTLS packet is decrypted, and then it is re-encrypted with standard TLS and routed on to the Internet. This means that customer data exists unencrypted for a moment. This is a security vulnerability that has become known as the gap in WAP. The cellular industry has since released WAPv2, which incorporates industry-standard TLS so that decryption is no longer necessary.

# Internet Layer Controls

Internet Protocol Security (IPsec) resides at the Internet layer and is a well-known cryptographic solution. IPsec is an end-to-end security technology that allows two devices to communicate securely. IPsec was developed to address the shortcomings of IPv4. Although it is an add-on for IPv4, it was created for and is built into IPv6. IPsec can be used to protect just the data or the data and the original IP header. This level of protection can provide integrity and/or encryption. (IPsec is covered in more detail later in this chapter.)

Two less frequently used cryptographic solutions are found at the Internet layer:

+   Simple Key-Management for Internet Protocol (SKIP): SKIP, which was developed by the IETF, is rarely used and requires no prior communication; it is similar to SSL. SKIP was evaluated as a key