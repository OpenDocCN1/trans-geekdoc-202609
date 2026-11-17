+   - **Managed services**—Router management and security appliance management 24 × 7 × 365.
+   - **Service-level agreements (SLAs)**—Contractual commitments for monthly service offerings such as availability, packet loss, and response time to fix problems.

The WAN Domain represents the fifth layer of security for an overall IT infrastructure. WAN services can include dedicated Internet access and managed services for customers’ routers and firewalls. Management agreements for availability and response times to outages are common. Networks, routers, and equipment require continuous monitoring and management to keep WAN service available.

# WAN Domain Roles, Responsibilities, and Accountability

Here’s an overview of what should go on in the WAN Domain:

+   - **Roles and tasks**—The WAN Domain includes both physical components and the logical design of routers and communication equipment. It is the second most complex area to secure within an IT infrastructure. Your goal is to allow users the most access possible while making sure what goes in and out is safe. The roles and tasks required within the WAN Domain include managing and configuring the following:
+     - **WAN communication links**—These are the physical communication links provided as a digital or optical service terminated at your facility. Broadband connection speeds can range among the following:
+       - DS0 (64 Kbps) to DS1 (1.544 Mbps) to DS3 (45 Mbps) for digital service
+       - OC-3 (155 Mbps) to OC-12 (622 Mbps) to OC-48 (2,488 Mbps) for optical service
+       - 10/100/1000 Mbps Metro Ethernet LAN connectivity, depending on physical distance
+     - **IP network design**—This is the logical design of the IP network and addressing schema. This requires network engineering, design of alternate paths, and selection of IP routing protocol.
+     - **IP stateful firewall**—This is a security appliance that is used to filter IP packets and block unwanted IP, TCP, and UDP packet types from entering or leaving the network. Firewalls can be installed on workstations or routers or as stand-alone devices protecting LAN segments.
+     - **IP router configuration**—This is the actual router configuration information for the WAN backbone and edge routers used for IP connections to remote locations. The configuration must be based on the IP network design and addressing schema.
+     - **Virtual private networks (VPNs)**—A VPN is a dedicated encrypted tunnel from one endpoint to another. The VPN tunnel can be created between a remote workstation using the public Internet and a VPN router or a secure browser and a Secure Sockets Layer virtual private network (SSL-VPN) website.
+     - **Multiprotocol Label Switching (MPLS)**—MPLS is a WAN software feature that allows customers to maximize performance. MPLS labels IP packets for rapid transport through virtual tunnels between designated endpoints. This is a form of Layer 1/Layer 3 overlay network and bypasses the routing function’s path determination process once a long-lived flow is configured or dynamically determined.