![](bbox=[0.25, 0.09, 0.75, 0.2])

Figure 3.63: UDP scanning

This happens because open ports do not have to send an acknowledgement in response to a probe, and closed ports are not even required to send an error packet.

# UDP Packets

Source: https://nmap.org

When you send a packet to a closed UDP port, most of the hosts send an ICMP_PORT_UNREACH error. Thus, you can determine whether a port is open if UDP packets or ICMP errors are not guaranteed to arrive. Thus, UDP scanners of this type must implement retransmission of packets that appear lost. UDP scanners interpret lost traffic as open ports. In Zenmap, the -sU option is used to perform a UDP scan.

![](bbox=[0.23, 0.42, 0.77, 0.88])

Figure 3.64: UDP scanning using Zenmap