# Chapter 6 • Network Services

Three types of IP address assignments are defined in the DHCP standards, as follows:

**Dynamic Allocation** The server leases an address from a pool for each specified duration called the lease time. When the lease expires, the client renews the address for another lease period or the server claims the address and returns it to the pool for reassignment.

**Automatic Allocation** The server assigns an address from a pool to each device manually, without a lease expiration or a renewal.

**Manual Allocation** In the manual process, also called reservations, the server assigns a specific address to each device permanently, without a lease or renewal. This method is typically used for servers and other systems that require permanent, unchanging IP address.

> EXAM TIP
The terms dynamic, automatic, and manual are used by the DHCP standards to define the types of address allocation, but not all DHCP implementations use these terms. The Network+ objectives use the term dynamic assignment, but they describe manual address allocations as reservations.

The assignment process occurs automatically when a device with a DHCP client starts, and proceeds as follows:

+   1. The DHCP client transmits a series of address request messages as broadcasts, using User Datagram Protocol (UDP) port 67.
2. Any DHCP servers on the local network with available leases that receive the broadcasts must reply with an offer of an IP address.
3. The DHCP client accepts one of the offered addresses by generating a request message containing the chosen server's IP address.
4. The chosen DHCP server replies to the request message with a positive or negative acknowledgment, indicating either its confirmation of the address or that the offered address is no longer available.
5. On receipt of a positive acknowledgement message, the client configures its TCP/IP settings with the offered address and options. If the client receives a negative acknowledgement, the entire name resolution process begins again.

The DHCP server keeps track of the addresses it assigns, so there is no chance of IP address duplication on the network. In dynamic allocation, when the IP address reaches 50 percent of its lease time, and when it reaches 87.5 percent, the client sends renewal requests to the DHCP server, which usually responds with a new lease for the same address. If the server does not receive renewal messages from the client, it reclaims the IP address assigned previously and returns it to the scope for reassignment.