# # Hybrid topology

The hybrid topology combines a mix of two or more other topologies. It makes maximum use of the advantages of each approach while minimizing the downsides. Hybrid approaches are suitable for large enterprises and telecommunications networks. In the illustration, a mesh approach is used for the interconnection of different base stations to provide reliability and durability between base stations, and then each base station manages a star topology for the individual devices connected to it.

![](bbox=[0.11, 0.16, 0.45, 0.44])

The hybrid topology is a mix of the mesh and star topologies; key points in the network are interlinked like a mesh, and then each of those points is the central point for its own star of connected nodes

Factors to consider for a hybrid approach include:

+   - **Reliability**: Generally quite high; if a node fails, it only affects the clients immediately connected to it, but not other parts of the network.
+   - **Transmission speed**: This is dependent on the exact configuration and mix of topologies deployed; bottlenecks can be an issue if it is not carefully designed.
+   - **Scalability**: Typically highly scalable and adaptable to changing needs and circumstances; a small addition to a network could start as a spoke on a star, and then later be upgraded to a full node in a mesh if needed.
+   - **Collisions**: Again, this is dependent on the configuration and mix of topologies.
+   - **Cost**: Likely to be higher to get started but generally more efficient over the long run.

# ## A2.2.2 The function of servers (HL)

> > **Top tip!**
> > It is very common for one physical computer acting as a server to have many server-based applications running on it simultaneously. The one computer could have a web server on port 80 and 443; an FTP server on 20 and 21; an SSH server running on port 22; and a DNS server on 53. In this section, “server” relates more to the separate server software applications rather than separate physical devices.

+   - **Server**: a computer or device on a network that manages and provides various network resources on behalf of other computers (clients) on the network.
+   - **Domain name**: a human-readable name assigned to a specific IP address on the internet, e.g. www.example.com.

A server is a computer that provides a service to other computers or devices on a network. Typically, these are dedicated machines housed in a specialized room, centrally located on the network with backup power supplies and other systems.

This section looks at some of the common application servers frequently seen on networks. We will look at each from a perspective of their function, scalability, reliability and security.

# ## Domain name server (DNS)

The domain name server provides a translation service that converts human-readable domain names into the IP addresses that are required for routing purposes. For example, at the time of writing, hachettelearning.com translates to 78.136.36.226.

The client device sends the DNS request to its configured DNS server. This can either be specified manually in the operating system settings, or it can be provided via DHCP when the