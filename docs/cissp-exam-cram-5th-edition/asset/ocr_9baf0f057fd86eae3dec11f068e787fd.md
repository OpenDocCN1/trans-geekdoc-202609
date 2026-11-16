exchange mechanism for IPsec before the adoption of IKE in 1998.

+   - Software IP Encryption (swIPe): swIPe was an early attempt to develop an open standard for VPNs. Although freely available, it was available only for SunOS and is not widely used.

# # Network Access Layer Controls

Several cryptographic solutions are available at the TCP/IP network access layer or Layer 2 of the OSI model:

+   - Point-to-Point Tunneling Protocol (PPTP): PPTP, which was developed by a group of vendors, consists of two components: transport, which maintains the virtual connection, and encryption, which ensures confidentiality. It can operate at a 40-bit or 128-bit key length.

+   - Layer 2 Tunneling Protocol (L2TP): L2TP was created by Cisco and Microsoft to replace L2F and PPTP. L2TP merged the capabilities of L2F and PPTP into one tunneling protocol. By itself, it provides no encryption, but it is deployed with IPsec as a VPN solution.

> > **Note**
> > L2F does not provide encryption or confidentiality by itself; it relies on the protocol being tunneled to provide privacy.

+   - WPA2 Enterprise: This Wi-Fi Alliance certification identifies equipment capable of establishing a secure channel of communication at TCP/IP Layer 1/OSI Layer 2 using EAP for authentication and AES-CTR-CBC-MAC for encryption. Cisco LEAP can be used with WPA and WPA2 networks.

> > **Note**
> > Extensible Authentication Protocol (EAP) is an authentication