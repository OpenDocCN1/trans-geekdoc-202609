# Syn Flood

Standard network communications requires a three-way handshake for every connection between a client and server, as illustrated in Figure 12-8.

![](bbox=[0.1, 0.24, 0.55, 0.33])

FIGURE 12-8 Three-way Handshake.

The client sends a packet with the SYN (Synchronize) flag switched on. The server first allocates resources for the connection, then responds with the SYN and ACK (Acknowledgement) flags switched on. The client then completes the connection by responding with a packet with the ACK flag turned on.

A SYN flood works by the client sending a literal flood of SYN packets requesting a connection, but never responding to them. The server allocates resources for each of these connections, and eventually exhausts those resources. A properly configured stateful packet inspection (SPI) firewall will prevent this.

# Smurf and Fraggle

A Smurf attack uses a combo of IP spoofing and ICMP to saturate a target network with traffic. Smurf consists of three elements: source site, bounce site, and target site. The attacker (source site) sends a modified ping to the broadcast address of a large network (bounce site). The modified packet contains a source address of the target site; everyone at the bounce site replies to the target site.

A fraggle attack is a variation of a Smurf attack where an attacker sends a large amount of UDP traffic to ports 7 (echo) and 19 (chargen) to a broadcast address, spoofing the intended victim’s source IP address. Configuring the gateway router/firewall to disallow incoming broadcast messages will prevent this.

# DHCP Starvation

If enough requests are flooded onto the network, the attacker can completely exhaust the address space allocated by the DHCP servers for an indefinite period of time. There are tools such as Gobbler that will do this for you. Preventing incoming DHCP requests, from outside the network, will prevent this.

# Application Layer DoS

Application layer denial of service is, as the name suggests, a denial of service that targets some network service that operates at the application layer, for example, targeting a database.

# HTTP Post DoS

An HTTP post DoS attack sends a legitimate HTTP post message. Part of the post message is the ‘content-length’. This indicates the size of the message to follow. In this attack, the attacker then sends the actual message body at an extremely slow rate. The web server is then “hung” waiting for that message to complete. For more robust servers, the attacker will need to use multiple HTTP Post DoS attacks simultaneously.