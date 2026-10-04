# Devices on a Remote Network (3.7.5)

What are the roles of the network layer address and the data link layer address when a device is communicating with a device on a remote network? In the example shown in Figure 3-33, a client computer, PC1, is communicating with a server, named Web Server, on a different IP network.

# Role of the Network Layer Addresses (3.7.6)

When the sender of a packet is on a different network from the receiver, the source and destination IP addresses represent hosts on different networks. This is indicated by the network portion of the IP address of the destination host.

+   - **Source IPv4 address**: The IPv4 address of the sending device, the client computer PC1: 192.168.1.110
- **Destination IPv4 address**: The IPv4 address of the receiving device, the server Web Server: 172.16.1.99

Notice in Figure 3-34 that the network portion of the source IPv4 address and destination IPv4 address are on different networks.

![](bbox=[0.24, 0.5, 0.95, 0.85])

Figure 3-34 Network Layer Addresses on Different Networks