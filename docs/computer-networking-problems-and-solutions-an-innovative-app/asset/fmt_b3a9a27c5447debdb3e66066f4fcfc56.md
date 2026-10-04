
In a situation where the `MTU` is mismatched between two interfaces on the same link, it is possible for a neighbor relationship to form but routing and other information to fail to be carried between the network devices. While many protocols have some mechanism to prevent information about the resulting unidirectional links from being used in calculating loop-free paths through the network, it is still useful to detect this situation so it can be explicitly reported and repaired. Several techniques are commonly used by control plane protocols to either explicitly detect this condition, or to at least prevent the initial stages of neighbor formation from taking place.

The control plane protocol can include the locally configured `MTU` in a field in the hello packets. Rather than just checking for the existence of a neighbor during the three-way handshake, each router can also check to make certain the `MTU` on both ends of the link match before adding a newly detected network device as a neighbor.

Another option is to pad the hello packets to the `MTU` of the local interface. If the padded, maximum-sized, hello packet is not received by some other device on the link, the initial stages of the neighbor relationship will not complete. The three-way handshake cannot be completed if both devices are not receiving one another’s hello packets.

Finally, the control plane protocol can rely on an underlying transport to regulate packet sizes so the communicating devices can receive them. This mechanism is primarily used in control planes designed to overlay some other control plane, particularly in the case of interdomain routing and network virtualization. Overlay control planes often rely on Path `MTU` (`PMTU`) discovery to provide an accurate `MTU` between two devices connected through multiple hops.

The `MTU` size itself can have a large impact on the performance of a control plane in terms of its speed of convergence. For instance, assume a protocol must send information describing 500,000 destinations over a multihop link with 500ms of delay, and each destination requires 512 bits to describe:
• If the `MTU` is less than 1,000 bits, the control plane will require 500,000 round trips to exchange the entire database of reachable destinations, or around 500,000 × 500ms, which is 250,000 seconds, or close to 70 hours.
• If the `MTU` is 1,500 octets, or 12,000 bits, the control plane will require around 21,000 round trips to describe the entire database of reachable destinations, or around 21,000 × 500ms, which is around 175 minutes.

The importance of compressing such a database, using some sort of windowing mechanism to reduce the number of full round trips required to exchange the reachability information and increasing the `MTU`, is readily apparent.

### Learning about Reachable Destinations

Neighbor discovery allows the control plane to learn about the topology of the network, but how is information about reachable destinations learned? In [Figure 11-7](#ch11.xhtml#ch11fig07), how does router D learn about hosts A, B, and C?

![Image](graphics/11fig07.jpg)

**Figure 11-7** *Discovering Reachability*

There are two broad classes of solutions to this problem—*reactive* and *proactive*—discussed in the following sections.

#### Learning Reactively

In [Figure 11-7](#ch11.xhtml#ch11fig07), assume host A has just been powered on, and the network is only using dynamic learning based on transmitted data traffic. How can router D learn about this newly attached host? One possibility is for A to simply start sending packets. For instance, if A is manually configured to send all packets toward destinations it does not know how to reach (essentially, anything that is *off segment*, a concept considered in [Chapter 6](#ch06.xhtml#ch06), “[Interlayer Discovery](#ch06.xhtml#ch06)”) to D, A has to send at least one packet for D to discover its existence. On learning of A, D can cache any relevant information for some time—generally for as long as A appears to be sending traffic. If A does not send traffic for some time, D can time the entry for A in its local cache out.

This process of discovering reachability based on actual traffic flow is *reactive discovery*. From a complexity perspective, reactive discovery trades optimal traffic flow against the information known about, and potentially carried, in the control plane.

**It will take some amount of time for reactive discovery mechanisms to operate**— that is, for D to learn about the existence of A once the host starts sending packets. For instance, if host F begins sending traffic toward A the moment A is powered on, traffic may be forwarded through the network to D, but D will not have the information required to forward the traffic onto the link, and hence to A. During the time between host A being powered on and D discovering its existence, packets will be dropped—a situation that will appear, to F, to be a network failure at the worst, and some additional jitter (or perhaps an unpredictable response across the network) at best.

**Cached entries will need to be timed out over time.** This will normally require balancing a number of factors, including how large the cache is, how much device information is cached, and how often the cache entry has been used in some past time period.

How long it will take to time out this cached information and any security risk of some other device using stale information is the foundation for an attack. For instance, if A moves its connection from D to E, the information D has learned about A will remain in D’s cache for some time. During this time, if another device connects to the network to D, it can impersonate A. The longer cached information is valid, the more possible it is to execute this type of attack.

#### Learning Proactively

Some reachability information can be learned proactively, which means the router does not need to wait for an attached host to start sending traffic to learn about it. This capability tends to be important in environments where hosts can be highly mobile; for instance, in a data center fabric where virtual machines may move between physical devices while keeping their address or other identifying information, or in networks that support wireless devices, such as mobile phones. There are four widely used ways to learn reachability information proactively, covered here:
• **A neighbor discovery protocol** can be run between the edge networking nodes (or devices) and connected hosts. The information learned from such a neighbor discovery protocol can then be used to inject reachability information in the control plane. While neighbor discovery protocols are widely deployed, the information learned through these protocols is not widely used to inject reachability information into the control plane.
• **Reachability information can be learned through device configuration.** Almost all network devices (such as routers) will have a reachable address configured or discovered on all host-facing interfaces. Network devices can then advertise these attached interfaces as reachable destinations. In this situation, the link (or wire), the network, or the subnet is the reachable destination, rather than individual hosts. This is the most common way for routers to learn network layer reachability information.
• **Hosts can register with an identity service.** In some systems, a service (whether centralized or distributed) keeps track of where hosts are attached, including such information as the first hop router through which traffic should be sent to reach them, name to address mapping, services each host is capable of providing, services each host is searching for and/or using, and other information. Identity services are common, although they are not often highly visible to network engineers. Such systems are very common in high mobility environments, such as consumer-facing wireless networks.
