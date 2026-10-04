![](bbox=[0.22, 0.1, 0.88, 0.24])

A packet is sent.

Figure 8-4 IP is Connectionless

# Best Effort (8.1.5)

IP does not require additional fields in the header to maintain an established connection. This process greatly reduces the overhead of IP. However, with no pre-established end-to-end connection, senders are unaware whether destination devices are present and functional when sending packets; they also are not aware of whether the destination receives a packet or whether a destination device is able to access and read a packet.

IP does not guarantee that all packets that are sent are, in fact, received. Figure 8-5 illustrates the unreliable, or best-effort delivery, characteristic of IP. As an unreliable network layer protocol, IP does not guarantee that all sent packets will be received. Other protocols manage the process of tracking packets and ensuring their delivery.

![](bbox=[0.22, 0.55, 0.88, 0.78])

Figure 8-5 Best-Effort Delivery