
Computer networks use a series of hierarchically arranged addresses to solve these problems; [Figure 2-5](#ch02.xhtml#ch02fig05) illustrates.

![Image](graphics/02fig05.jpg)

**Figure 2-5** *Addressing Multiple Levels of Entities in a Network*

In [Figure 2-5](#ch02.xhtml#ch02fig05), there are four levels of addressing shown:
• At the physical link level, there are interface addresses that allow two devices to address a particular device individually.
• At the host level, there are host addresses that allow two hosts to address a particular host directly.
• At the process level, there are `port numbers` that, combined with the host address, allow two processes to address a particular process on a particular device.
• At the conversation level, the set of source port, destination port, source address, and destination address can be combined to uniquely identify a particular conversation, or flow.

This diagram and explanation appear very clean. In real life, things are much messier. In the most widely deployed addressing scheme, the Internet Protocol (`IP`), there are no `host-level addresses`. Instead, there are logical and physical addresses on a per interface basis.

**Note**
`IP` and `IP` addressing will be considered in more detail in [Chapter 5](#ch05.xhtml#ch05), “[Higher Layer Data Transports](#ch05.xhtml#ch05).”

Multiplexing and multiplexing identifiers (addresses) are stacked hierarchically on top of one another in a network.

**Note**
Mechanisms that associate one kind of address with another between some layers will be considered more fully in [Chapter 6](#ch06.xhtml#ch06), “[Interlayer Discovery](#ch06.xhtml#ch06).”

There are some situations, however, in which you want to send traffic to more than one host at a time; for these situations, there are multicast and anycast. These two special kinds of addressing will be considered in the following sections.

### On Physical Links, Broadcasts, and Failure Domains

The clear-cut model illustrated in [Figure 2-5](#ch02.xhtml#ch02fig05) is made more complex when you consider the concept of broadcast domains and physical connectivity. Some media types (notably Ethernet, which is covered in more detail in [Chapter 4](#ch04.xhtml#ch04), “[Lower Layer Transports](#ch04.xhtml#ch04)”) are designed so every device connected to the same physical link receives every packet transmitted onto the physical media—hosts just ignore packets not addressed to one of the addresses associated with the physical interface connected to the physical wire. In modern networks, however, physical Ethernet wiring rarely allows every device to receive every other device’s packets; instead, there is a switch in the middle of the network that blocks packets not destined to a particular device from being transmitted on the physical wire connected to that host.

In these protocols, however, there are explicit addresses set aside for packets that `should be` transmitted to every host that would normally receive every packet if the switch was not there, or that every host should receive and process (normally, this is some form of the all 1s or all 0s version of the address). These are called broadcasts. Any device that will receive, and process, a broadcast sent by a device is said to be part of the device’s broadcast domain. The concept of a broadcast domain has traditionally been closely associated with a failure domain, because network failures impacting one device on a broadcast domain often impact every device on the broadcast domain (see [Chapter 23](#ch23.xhtml#ch23), “[Redundant and Resilient](#ch23.xhtml#ch23),” for more information on failure domains).

Do not be surprised if you find all of this rather confusing, because it is, in fact, rather confusing. The basic concepts of broadcasts and broadcast domains still exist, and are still important in understanding the operation of a network, but the meaning of the term can change, or even not apply, in some situations. Be careful when considering any situation to make certain you really understand how and where such broadcast domains really are, and how specific technologies impact the relationship between physical connectivity, addressing, and broadcast domains.

#### Multicast

**Note**
This short explanation cannot really do justice to the entire scope of solutions available to build multicast trees; see the “Further Reading” section at the end of the chapter for more material to consider in this area.

If you have a network like the one shown in [Figure 2-6](#ch02.xhtml#ch02fig06), and you need A to distribute the same content to G, H, M, and N, how would you go about doing this?

You could either generate four copies of the traffic, sending one stream to each of the receivers using normal `unicast` forwarding, or you could somehow send the traffic to a single address that the network knows to replicate so all four hosts receive a copy. This latter option is called multicast, which means using a single address to transmit traffic to multiple receivers. The key problem to solve in multicast is to forward and replicate traffic as it passes through the network so each receiver who is interested in the stream will receive a copy.

**Note**
The set of devices interested in receiving a stream of packets from a multicast source is called a multicast group. This can be a bit confusing because the address used to describe the multicast stream is also called a multicast group in some situations. The two uses are `practically` interchangeable in that the set of devices interested in receiving a particular set of multicast packets will join the multicast group, which, in effect, means listening to a particular multicast address.

**Note**
In cases where the multicast traffic is bidirectional, this problem is much more difficult to solve. For instance, assume there is a requirement to build a multicast group with every host in the network shown in [Figure 2-6](#ch02.xhtml#ch02fig06) except N, and further that any multicast transmitted to the multicast group’s address be delivered to every host within the multicast group.

![Image](graphics/02fig06.jpg)

**Figure 2-6** *A Multicast Example*

The key problem for multicast to solve can be broken into two problems:
• How do you discover which devices would like to receive a copy of traffic transmitted to the multicast group?
• How do you determine which devices in the network should replicate the traffic, and on which interfaces they should send copies?

One possible solution is to use local requests to build a tree through which the multicast traffic should be forwarded through the network. An example of such a system is `Sparse Mode` in Protocol Independent Multicast (`PIM`). In this this process, each device sends a `join` message for the multicast streams it is interested in; these joins are passed upstream in the network until the sender (the host sending packets through the multicast stream) is reached. [Figure 2-7](#ch02.xhtml#ch02fig07) is used to illustrate this process.

![Image](graphics/02fig07.jpg)

**Figure 2-7** *Sparse mode multicast*

In [Figure 2-7](#ch02.xhtml#ch02fig07):
1. A is sending some traffic to a multicast group (address); call it `Z`.
2. N would like to receive a copy of Z, so it sends a request (a join) to its upstream router, D, for a copy of this traffic.
3. D does not have a source for this traffic, so it sends a request to the routers it is connected to for a copy of this traffic; in this case, the only router D sends the request to is B.

At each hop, the router receiving the request will place the interface on which it received the request into its `Outbound Interface List (OIL)`, and begin forwarding traffic received in the given multicast group received on any other interface. In this way, a path from the receiver to the originator of the traffic can be built; this is called a `reverse path tree`.
