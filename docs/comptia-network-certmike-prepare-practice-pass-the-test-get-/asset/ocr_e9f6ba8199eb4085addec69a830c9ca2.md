# Split Tunnel vs. Full Tunnel

When a VPN client connects to a remote VPN server, it creates a new logical network connection. However, the client's original (unencrypted) connection to the Internet is still in place. VPN clients typically provide two options for use of these connections, as follows:

+   **Split Tunnel:** In a split tunnel, both of the network connections remain active, with all company traffic going through the VPN connection, while the system uses its original, unprotected connection for Internet access. This reduces the traffic passing through the VPN tunnel but presents a potential security hazard if the Internet connection is unprotected.
**Full tunnel:** In a full tunnel, only the VPN tunnel connection remains active, with all company traffic going to the remote network. The client therefore accesses the Internet through the remote network, providing it with the additional security monitoring and protection of the company infrastructure.

Remote Desktop Connection (RDC) (see Figure 19.1) is a graphical application that enables a client user to connect to a host at another location and control it

![](bbox=[0.118, 0.439, 0.563, 0.843])

FIGURE 19.1 The Remote Desktop Connection client interface