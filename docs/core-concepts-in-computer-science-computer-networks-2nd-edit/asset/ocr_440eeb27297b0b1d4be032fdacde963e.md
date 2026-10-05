Networks may be classified based on the method of data used to convey the data, these include digital and analog networks.

![](bbox=[0.106, 0.116, 0.396, 0.273])

# CORE CONCEPT:
COMPUTER NETWORKS nBASED ON TRANSMISSION TECHNOLOGY

Computer networks are essential infrastructures that facilitate communication and data exchange among devices and systems. They rely on various transmission technologies to transmit information from one point to another efficiently and reliably.

The transmission means, is that sending a signal from one location to another. Transmission technologies refer to the physical layer protocol such as modulation, demodulation, line coding, error control etc. The transmission technology can be categorized broadly into two types:

+   1. Broadcast networks and
2. Point-to-point networks.

# Broadcast Network

Broadcast networks have a single communication channel that is shared by all the machines on the network. Short messages, called packets in certain contexts, sent by any machine are received by all the others.

An address field within the packet specifies for whom it is intended. Upon receiving a packet, a machine checks the address field. If the packet is intended for itself, it processes the packet; if the packet is intended for some other machine, it is just ignored.

Broadcast systems generally also allow the possibility of addressing a packet to all destinations by using a special code in the address field.

When a packet with this code is transmitted, it is received and processed by every machine on the network. This mode of operation is called broadcasting.

Some broadcast systems also support transmission to a subset of the machines, something known as multicasting. One possible scheme is to reserve one bit to indicate multicasting. The remaining (n-1) address bits hold a group number. Each machine can “subscribe” to any or all of the groups. When a packet is sent to a certain group, it is delivered to ail machines subscribing to that group.