digital certificate over its life cycle. In addition, although all recent client PC operating systems can implement IPsec, configuring them to use it usually involves manual configuration labor. Although the labor cost per client and server is modest, the total cost of transport mode installation labor can be daunting in a firm that has many clients and servers.

# IPsec IN TRANSPORT MODE AND FIREWALLS

Although IPsec transport mode provides high security to dialogues, it reduces the effectiveness of another security countermeasure, the border firewall. The border firewall should investigate each packet passing through it, looking for indications of unacceptable content. For encrypted IP packets, however, firewalls are useless because they cannot read a packet’s plaintext content to filter it. If the source host sends an attack packet to a destination host via IPsec transport mode, the firewall cannot stop the attack packet.

# IPsec Tunnel Mode

Figure 3-29 shows that IPsec tunnel mode only protects traffic between two IPsec gateways at different sites.30 These gateways send traffic securely through the Internet between themselves. Tunnel mode creates a site-to-site VPN.

# PROTECTION IS PROVIDED BY IPsec GATEWAYS

The source IPsec gateway receives original (unencrypted) IP packets from its site hosts, encrypts them, and sends them to the other IPsec gateway. The receiving IPsec gateway decrypts IP packets and sends them in the clear to the destination host.

# LESS EXPENSIVE THAN TRANSPORT MODE

The major advantage of tunnel mode operation is cost. All of the cryptographic work is done on the IPsec gateway servers. Clients and servers merely transmit and receive their packets in the clear. The company does not need to make any changes to their clients and servers, as it must do in transport mode. Not needing to create and manage digital certificates for all of its clients and servers makes tunnel mode much less expensive than transport mode.

# FIREWALL-FRIENDLY PROTECTION

In addition, IPsec tunnel mode is firewall-friendly. Packets are only encrypted between the two IPsec gateways, so after a packet arrives, it can be filtered by a firewall placed after the IPsec gateway at each site.

# NO PROTECTION WITHIN THE TWO SITES

The disadvantage of tunnel mode is that it gives absolutely no protection at all to IP packets when they are traveling within the site networks at the two sites. This leaves packets open to attack within site networks. However, transmission within site networks generally is safer than transmission over the Internet, so the loss of protection within sites is often considered a good trade-off for the lower cost of IPsec tunnel mode operation and for IPsec’s firewall friendliness.

30 Many people are taught that the name tunnel mode means that IPsec creates a secure tunnel through the nonsecure Internet or a nonsecure wireless LAN. This is good if it helps you remember what IPsec does, but that is not really why the name tunnel mode came about. In network standards, tunneling simply means placing a message inside another message. In IPsec tunnel mode, the entire original packet is encapsulated in the data field of a new packet that is sent between the two IPsec gateways. In other words, the original packet is tunneled in a new packet. In transport mode, by contrast, protections extend to parts of the original packet, but there is no placing the original packet inside another packet, that is, no tunneling.