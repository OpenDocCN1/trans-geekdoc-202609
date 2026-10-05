# LOAD BALANCING

Load balancing is a high availability technique in which there are multiple servers performing the same task and a mechanism that divides the incoming traffic among those servers. This prevents any server from being overwhelmed with requests.
One of the most common load balancing scenarios is that of a server hosting a busy website. There are multiple web servers clustered, each of which hosts a fully functional copy of the website. A load balancer functions as a gateway to the server farm. Incoming requests from clients on the Internet arrive at the load balancer, which distributes them among the servers.

This arrangement enables administrators to add servers to the cluster when the load increases or remove them for maintenance. Even if a server should fail, the load balancer can redistribute the traffic among the remaining servers, ensuring the continued availability of the website.

The load balancing mechanism can be a software or hardware product, and it can distribute the traffic in various ways. For example, some load balancers use a round-robin algorithm, which the device distributes the incoming requests by sending one to each server in turn. Others monitor the servers in the farm and send incoming requests to the server with the fewest active clients.

# MULTIPATHING

Multipathing—also known as multipath IO or MPIO—is a fault tolerance mechanism usually associated with storage area networks (SANs). SANs can provide a flexible and scalable storage infrastructure, but they also add points of failure. When a server is connected to its storage through a SAN, there are intervening cables, switches, and disk housings that could fail one day.

To provide fault tolerance and high availability, administrators often design the network with redundant paths between the server and the storage devices so that if one path should fail, the other continues operating. To implement multip multip infrastructure for a SAN, the server needs at least two network interface adapters, each of which is connected by a cable to a different switch. The switches are then connected to the drive array, which should also have redundant network interfaces.

With this arrangement, the server can tolerate the failure of a network adapter, a cable, or a switch. The more redundant components there are on the path from the server to its storage, the more tolerant of faults the SAN will be.

# NIC TEAMING

Network interface card (NIC) teaming—also called NIC bonding—is a technique for joining two network interface adapters together, either combine their bandwidth or to provide