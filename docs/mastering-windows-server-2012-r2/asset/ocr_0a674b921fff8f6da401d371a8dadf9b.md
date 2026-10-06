# UNDERSTANDING THE TUNNELING PROTOCOLS

FIGURE 21.2
Gateway-to-gateway VPN

![](bbox=[0.313, 0.098, 0.879, 0.273])

# # Understanding the Tunneling Protocols

When configuring a VPN, security is always a consideration. Data can't be sent across the Internet in clear without the risk of someone using a sniffer to capture it. To combat this risk, VPNs use tunneling protocols.

Currently, there are three primary tunneling protocols for use in Windows VPNs: Layer 2 Tunneling Protocol (L2TP), Secure Socket Tunneling Protocol (SSTP), and Internet Key Exchange version 2 (IKE2). The Point-to-Point Tunneling Protocol (PPTP) has been used in the past but has known vulnerabilities and is being used less as administrators become more concerned about security.

Both the VPN server and the VPN client must be configured to use the same tunneling protocol.

# ## Layer 2 Tunneling Protocol

Layer 2 Tunneling Protocol is a popular tunneling protocol used with VPNs. It commonly encrypts traffic via IPsec (which is explained later in this chapter), and you'll see it expressed as L2TP/IPsec.

When used with IPsec, L2TP encrypts the data, providing confidentiality, and signs the data, providing integrity. IPsec has a weakness that prevents it from being used all the time—IPsec can't travel through a Network Address Translation (NAT).

NAT is commonly used to translate private IP addresses to public IP addresses and back to private. However, because of the way IPsec packets are put together, NAT effectively breaks IPsec packets. If you need to go through a NAT server, you simply can't use L2TP/IPsec.

In the past, if you had to go through a NAT server to connect to a Microsoft VPN server, you'd need use Point-to-Point Tunneling Protocol. PPTP has security concerns, so you'll rarely see it used today. However, if you need to go through a NAT server, you have another choice today—Secure Socket Tunneling Protocol.

# ## Secure Socket Tunneling Protocol

Secure Socket Tunneling Protocol (SSTP) is a newer tunneling protocol that was introduced with Windows Server 2008 and is fully supported in Windows Server 2012 R2. It uses Secure Sockets Layer (SSL) over port 443 to secure VPN traffic.