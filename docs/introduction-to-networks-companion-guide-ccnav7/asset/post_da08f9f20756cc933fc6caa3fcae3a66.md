
and the router interface serving as the default gateway are both operational on the local network.

![](img/e71dc48d3ae3db3394e5857ab2acae75_487_0.png)

## Figure 13-7 Pinging the Default Gateway

For this test, the default gateway address is most often used because the router is normally always operational. If the default gateway address does not respond, a ping can be sent to the IP address of another host on the local network that is known to be operational.

If either the default gateway or another host responds, this confirms that the local host can successfully communicate over the local network. If the default gateway does not respond but another host does, this could indicate a problem with the router interface serving as the default gateway. One possibility is that the wrong default gateway address might have been configured on the host. Another possibility is that the router interface may be fully operational but might have security applied to it that prevents it from processing or responding to ping requests.

## Ping a Remote Host (13.2.4)

ping can be used to test the ability of a local host to communicate across an internetwork. The local host can ping an operational IPv4 host of a remote network, as shown in Figure 13-8. The router uses its IP routing table to forward the packets.

![](img/e71dc48d3ae3db3394e5857ab2acae75_488_0.png)

Figure 13-8 Testing Connectivity to a Remote LAN

If this ping is successful, the operation of a large piece of the internetwork can be verified. A successful ping across the internetwork confirms communication on the local network, the operation of the router serving as the default gateway, and the operation of all other routers that might be in the path between the local network and the network of the remote host.

In addition, the functionality of the remote host can be verified. If the remote host could not communicate outside its local network, it would not have responded.

Note

Many network administrators limit or prohibit the entry of ICMP messages into the corporate network; therefore, the lack of a ping response could be due to security restrictions.

## Traceroute—Test the Path (13.2.5)

ping is used to test connectivity between two hosts but does not provide information about the details of devices between the hosts. traceroute (tracert) is a utility that generates a list of hops that were successfully reached along the path. This list can provide important verification and troubleshooting information. If the data reaches the destination, then the trace lists the interface of every router in the path between the hosts. If the data fails at some hop along the way, the address of the last router that responded to the trace can provide an indication of where the problem or security restrictions are occurring.

## Round-Trip Time (RTT)

Using traceroute provides round-trip time for each hop along the path and indicates whether a hop fails to respond. The round-trip time is the time a packet takes to reach the remote host and for the response from the host to return. An asterisk (*) is used to indicate a lost packet or a packet that does not receive a reply. This information can be used to locate a problematic router in the path or may indicate that the router is configured not to reply. If the display shows high response times or data losses from a particular hop, this is an indication that the resources of the router or its connections may be stressed.

## IPv4 TTL and IPv6 Hop Limit

traceroute makes use of a function of the TTL field in IPv4 and the Hop Limit field in IPv6 in the Layer 3 headers, along with the ICMP Time Exceeded message.

The first sequence of messages sent from traceroute have a TTL field value of 1. This causes the TTL to time out the IPv4 packet at the first router. This router then responds with an ICMPv4 Time Exceeded message. traceroute now has the address of the first hop.

traceroute then progressively increments the TTL field (2, 3, 4, and so on) for each sequence of messages. This provides the trace with the address of each hop as the packets time out further down the path. The TTL field continues to be increased until the destination is reached, or it is incremented to a predefined maximum.

After the final destination is reached, the host responds with either an ICMP Port Unreachable message or an ICMP Echo Reply message instead of the ICMP Time Exceeded message.

![](img/e71dc48d3ae3db3394e5857ab2acae75_489_0.png)

Go to the online course to view an animation of how traceroute takes advantage of TTL.

![](img/e71dc48d3ae3db3394e5857ab2acae75_489_1.png)

## Packet Tracer—Verify IPv4 and IPv6 Addressing (13.2.6)

IPv4 and IPv6 can coexist on the same network. From the command prompt of a PC, there are some differences in the way commands are issued and in the way output is displayed.

![](img/e71dc48d3ae3db3394e5857ab2acae75_489_2.png)

## Packet Tracer—Use Ping and Traceroute to Test Network Connectivity (13.2.7)

There are connectivity issues in this activity. In addition to gathering and documenting information about the network, you will locate the problems and implement acceptable solutions to restore connectivity.

## Summary (13.3)

The following is a summary of the topics in the chapter and their corresponding online modules.

## ICMP Messages

The TCP/IP suite provides for error messages and informational messages when communicating with other IP devices. These messages are sent using ICMP. The purpose of these messages is to provide feedback about issues related to the processing of IP packets under certain conditions. The ICMP messages common to both ICMPv4 and ICMPv6 are Host Reachability, Destination Unreachable or Service Unreachable, and Time Exceeded. An ICMP Echo message tests the reachability of a host on an IP network. The local host sends an ICMP Echo Request to a host. If the host is available, the destination host responds with an Echo Reply. This is the basis of the ping utility. When a host or gateway receives a packet that it cannot deliver, it can use an ICMP Destination Unreachable message to notify the source. This message includes a code that indicates why the packet could not be delivered. A router uses an ICMPv4 Time Exceeded message to indicate that a packet cannot be forwarded because the Time-to-Live (TTL) field of the packet was decremented to 0. If a router receives a packet and decrements the TTL field to zero, it discards the packet and sends a Time Exceeded message to the source host. ICMPv6 also sends a Time Exceeded in this situation. ICMPv6 uses the IPv6 Hop Limit field to determine whether the packet has expired. Time Exceeded messages are used by the traceroute tool. The messages between an IPv6 router and an IPv6 device using dynamic address allocation include RS and RA. The messages between IPv6 devices include the redirect messages (similar to those in IPv4); NS and NA.

## Ping and Traceroute Testing

ping (used by IPv4 and IPv6) uses ICMP Echo Request and Echo Reply messages to test connectivity between hosts. To test connectivity to another host on a network, an Echo Request is sent to the host address, using the ping command. If the host at the specified address receives the Echo Request, it responds with an Echo Reply. As each Echo Reply is received, ping provides feedback on the time between when the request was sent and when the reply was received. After all the requests are sent, the ping utility provides a summary that includes the success rate and average round-trip time to the destination. ping can be used to test the internal configuration of IPv4 or IPv6 on the local host. You can ping the local loopback address 127.0.0.1 for IPv4 or ::1 for IPv6. You can also use ping to test the ability of a host to communicate on the local network, by pinging the IP address of the default gateway of the host. A successful ping to the default gateway indicates that the host and the router interface
