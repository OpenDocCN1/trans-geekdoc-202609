![](bbox=[0.18, 0.1, 0.82, 0.42])

# Figure 14-32 UDP Server Listening for Requests

After a client has selected the source and destination ports, the same two ports are used in the headers of all datagrams in the transaction. For the data returning to the client from the server, the source and destination port numbers in the datagram header are reversed.

Figure 14-33 is an illustration of two hosts requesting services from the DNS and RADIUS authentication server. In the figure, Client 1 is sending a DNS request, and Client 2 is requesting RADIUS authentication services of the same server.

![](bbox=[0.22, 0.55, 0.82, 0.8])

# Figure 14-33 Clients Sending UDP Requests

In Figure 14-34, Client 1 is sending a DNS request using the well-known destination port 53, and Client 2 is requesting RADIUS authentication services using the registered destination port 1812.