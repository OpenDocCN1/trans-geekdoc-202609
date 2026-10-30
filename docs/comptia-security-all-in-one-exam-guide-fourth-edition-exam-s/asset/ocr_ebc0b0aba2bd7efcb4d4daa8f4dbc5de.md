it is possible to tunnel across other networks at lower levels of the OSI model. The set of security services provided by IPsec occurs at the network layer of the OSI model, so higher-layer protocols, such as TCP, UDP, Internet Control Message Protocol (ICMP), Border Gateway Protocol (BGP), and the like, are not functionally altered by the implementation of IPsec services.

The IPsec protocol series has a sweeping array of services it is designed to provide, including but not limited to access control, connectionless integrity, traffic-flow confidentiality, rejection of replayed packets, data security (encryption), and data-origin authentication. IPsec has two defined methods—transport and tunneling—that provide different levels of security. IPsec also has three modes of connection: host-to-server, server-to-server, and host-to-host.

The transport method encrypts only the data portion of a packet, thus enabling an outsider to see source and destination IP addresses. The transport method protects the higher-level protocols associated with a packet and protects the data being transmitted but allows knowledge of the transmission itself. Protection of the data portion of a packet is referred to as *content protection*.

Tunneling provides encryption of source and destination IP addresses, as well as of the data itself. This provides the greatest security, but it can be done only between IPsec servers (or routers) because the final destination needs to be known for delivery. Protection of the header information is known as *context protection*.

![](bbox=[0.17, 0.64, 0.25, 0.73])

> **EXAM TIP** In transport mode (end-to-end), security of packet traffic is provided by the endpoint computers. In tunnel mode (portal-to-portal), security of packet traffic is provided between endpoint node machines in each network and not at the terminal host machines.

It is possible to use both methods at the same time, such as using transport within one's own network to reach an IPsec server, which then tunnels to the target server's network, connecting to an IPsec server there, and then using the transport method from the target network's IPsec server to the target host. IPsec uses the term security association as a means of describing a unidirectional combination of specific algorithm and key selection to provide a protected channel. If the traffic is bidirectional, two security associations are needed and can in fact be different.

# Basic Configurations

Four basic configurations can be applied to machine-to-machine connections using IPsec. The simplest is a host-to-host connection between two machines, as shown in Figure 3-3. In this case, the Internet is not a part of the security association (SA) between the machines. If bidirectional security is desired, two SAs are used. The SAs are effective from host to host.

The second case places two security devices in the stream, relieving the hosts of the calculation and encapsulation duties. These two gateways have an SA between them. The network is assumed to be secure from each machine to its gateway, and no IPsec is