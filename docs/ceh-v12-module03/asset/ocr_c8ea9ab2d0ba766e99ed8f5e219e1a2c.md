# Stealth Scan (Half-Open Scan)

The stealth scan involves resetting the TCP connection between the client and the server abruptly before completion of the three-way handshake signals, hence making the connection half-open. A stealth scan sends a single frame to a TCP port without any TCP handshaking or additional packet transfers. This type of scan sends a single frame with the expectation of a single response. The half-open scan partially opens a connection but stops halfway through. The stealth scan is also called a “SYN scan,” because it only sends the SYN packet. This prevents the service from notifying the incoming connection. TCP SYN or half-open scanning is a stealth method of port scanning.

The stealth scan also implements the three-way handshake methodology. In the last stage, it examines the packets entering the interface and terminates the connection before triggering a new initialization to identify remote ports. The stealth scan process is described below.

+   - The client sends a single SYN packet to the server on the appropriate port.
+   - If the port is open, the server subsequently responds with a SYN/ACK packet.
+   - If the server responds with an RST packet, then the remote port is in the "closed" state.
+   - The client sends the RST packet to close the initiation before a connection can be established.

![](bbox=[0.27, 0.465, 0.735, 0.585])

Figure 3.36: Port is open

![](bbox=[0.265, 0.632, 0.745, 0.752])

Figure 3.37: Port is closed

Attackers use stealth scanning techniques to bypass firewall rules and logging mechanisms, and they hide themselves as usual under network traffic. In Zenmap, the -sS option is used to perform a stealth scan/TCP half-open scan.