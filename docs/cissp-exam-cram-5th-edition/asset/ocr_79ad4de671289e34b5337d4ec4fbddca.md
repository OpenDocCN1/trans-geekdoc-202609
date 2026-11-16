# Data in Transit

Any time data is being processed or moved from one location to another, it requires proper controls. The basic problem is that many protocols and applications send information via plaintext. Services such as email, the Web, and FTP were not designed with security in mind, and with them, information is sent with few security controls and no encryption. Examples of insecure protocols include the following:

+   - **File Transfer Protocol (FTP)**: Plaintext username and password
+   - **Telnet**: Plaintext username and password
+   - **Hypertext Transfer Protocol (HTTP)**: Plaintext data
+   - **Simple Mail Transfer Protocol (SMTP)**: Plaintext data

Data in transit that is not protected by some form of encryption faces many dangers, including the following:

+   - Eavesdropping
+   - Sniffing
+   - Hijacking
+   - Data alteration

Today, many people connect to corporate networks from many different locations. Employees may connect via free Wi-Fi from coffee shops, restaurants, airports, or even hotels.

One way to protect this type of data in transit is by means of a virtual private network (VPN). A VPN is used to connect devices through the public Internet. Three protocols are used to provide a tunneling mechanism in support of VPNs: Point-to-Point Tunneling Protocol (PPTP), Layer 2 Tunneling Protocol (L2TP), and IP Security (IPsec). When an appropriate protocol is defined, the VPN traffic is encrypted. Microsoft supplies Microsoft Point-to-Point Encryption (MPPE), with PPTP, native to the Microsoft operating systems. L2TP offers no encryption, and it is therefore usually used with IPsec in ESP mode to protect data in transit and provide both confidentiality and authentication. IPsec can provide both tunneling and