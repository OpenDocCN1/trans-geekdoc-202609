# Half-Duplex and Full-Duplex Communication (6.2.5)

Understanding duplex communication is important when discussing LAN topologies because it refers to the direction of data transmission between two devices. There are two common modes of duplex: half-duplex and full-duplex.

# Half-Duplex Communication

In half-duplex communication, two devices can transmit and receive on the medium but cannot do so simultaneously. WLANs and legacy bus topologies with Ethernet hubs use the half-duplex mode. Half-duplex allows only one device to send or receive at a time on the shared medium. In Figure 6-13, the server and hub are operating in half-duplex.

![](bbox=[0.25, 0.36, 0.77, 0.47])

Figure 6-13 Half-Duplex Communication

# Full-Duplex Communication

With full-duplex communication, both devices can simultaneously transmit and receive on the shared medium. The data link layer assumes that the medium is available for transmission for both nodes at any time. Ethernet switches operate in full-duplex mode by default, but they can operate in half-duplex if connecting to a device such as an Ethernet hub. Figure 6-14 shows an example of full-duplex communication.

![](bbox=[0.25, 0.7, 0.77, 0.8])

Figure 6-14 Full-Duplex Communication

In summary, half-duplex restricts the exchange of data to one direction at a time. Full-duplex allows the sending and receiving of data to happen simultaneously.