arrive error free or in the correct order. That task is left to protocols on higher layers. IP will subdivide packets into fragments when a packet is too large for a network.

Hosts are distinguished by the IP addresses of their network interfaces. The address is expressed as four octets separated by a dot (.), for example, 216.12.146.140. Each octet may have a value between 0 and 255. However, 0 and 255 are not used for hosts. The latter is used for broadcast addresses, and the former’s meaning depends on the context in which it is used. Each address is subdivided into two parts: the network number and the host. The network number, assigned by an external organization, such as the Internet Corporation for Assigned Names and Numbers (ICANN), represents the organization’s network. The host represents the network interface within the network.

Originally, the part of the address that represented the network number depended on the network’s class. As shown in Table 4.1, a Class A network used the leftmost octet as the network number, Class B used the leftmost two octets, etc.

| Class | Range of First Octet | Number of Octets for Network Number | Number of Hosts in Network |
|---|---|---|---|
| A | 1 – 127 | 1 | 16,777,216 |
| B | 128 – 191 | 2 | 65,536 |
| C | 192 – 223 | 3 | 256 |
| D | 224 – 239 | Multicast |  |
| E | 240 – 255 | Reserved |  |

Table 4.1 – Network Classes

The part of the address that is not used as the network number is used to specify the host. For example, the address 216.12.146.140 represents a Class C network. Therefore, the network portion of the address is represented by the 216.12.146, and the unique host address within the network block is represented by 140.

127, which is the Class A network address block, is reserved for a computer’s loopback address. Usually the address 127.0.0.1 is used. The loopback address is used to provide a mechanism for self-diagnosis and troubleshooting at the machine level. This mechanism allows a network administrator to treat a local machine as if it were a remote machine and ping the network interface to establish whether or not it is operational.

The explosion of Internet utilization in the 1990s caused a shortage of unallocated