
TCP specifically will make sure the data received by the destination is in the correct order, without duplicate data or missing data.

The primary transport layer protocols you’ll use in this book are TCP and the `User Datagram Protocol (UDP)`. As mentioned i[n “Sending Traffic by](#index_split_000.html#p32)

[Using Data Encapsulation” on page 10](#index_split_000.html#p32), this layer handles segments, or datagrams.

`**N O T E**`

`TCP` also overlaps a bit with OSI’s Layer 5, because `TCP` includes session-handling capabilities that would otherwise fall under the scope of OSI’s session layer. But, for our purposes, it’s okay to generalize the transport layer as representing OSI’s Layer 4.

Most of our network applications rely on the transport layer protocols to handle the error correction, flow control, retransmission, and transport acknowledgment of each segment. However, the TCP/IP model doesn’t require every transport layer protocol to fulfill each of those elements. `UDP` is one such example. If your application requires the use of `UDP` for maximal throughput, the onus is on you to implement some sort of error checking or session management, since `UDP` provides neither.

***The Internet Layer***

The `internet layer` is responsible for routing packets of data from the upper layers between the origin node and the destination node, often over multiple networks with heterogeneous physical media. It has the same functions as OSI’s Layer 3 network layer. (Some sources may refer to TCP/IP’s internet layer as the `network layer`.)

`Internet Protocol version 4 (IPv4)`, `Internet Protocol version 6 (IPv6)`, `Border Gateway Protocol (BGP)`, `Internet Control Message Protocol (ICMP)`, `Internet Group Management Protocol (IGMP)`, and the `Internet Protocol Security (IPsec)` suite, among others, provide host identification and routing to TCP/IP’s internet layer. We will cover these protocols in the next chapter, when we discuss **14** Chapter 1 host addressing and routing. For now, know that this layer plays an integral role in ensuring that the data we send reaches its destination, no matter the complexity between the origin and destination.

***The Link Layer***

The `link layer`, which corresponds to Layers 1 and 2 of the OSI reference model, is the interface between the core TCP/IP protocols and the physical media.

The link layer’s `Address Resolution Protocol (ARP)` translates a node’s IP address to the MAC address of its network interface. The link layer embeds the MAC address in each frame’s header before passing the frame on to the physical network. We’ll discuss MAC addresses and their routing significance in the next chapter.

Not all TCP/IP implementations include link layer protocols. Older readers may remember the joys of connecting to the internet over phone lines using analog modems. Analog modems made serial connections to ISPs. These serial connections didn’t include link layer support via the serial driver or modem. Instead, they required the use of link layer protocols, such as the `Serial Line Internet Protocol (SLIP)` or the `Point-to-Point Protocol (PPP)`, to fill the void. Those that do not implement a link layer typically rely on the underlying network hardware and device drivers to pick up the slack. The TCP/IP implementations over Ethernet, wireless, and fiber-optic networks we’ll use in this book rely on device drivers or network hardware to fulfill the link layer portion of their TCP/IP stack.

**What You’ve Learned**

In this chapter, you learned about common network topologies and how to combine those topologies to maximize their advantages and minimize their disadvantages. You also learned about the OSI and TCP/IP reference models, their layering, and data encapsulation. You should feel comfortable with the order of each layer and how data moves from one layer to the next.

Finally, you learned about each layer’s function and the role it plays in sending and receiving data between nodes on a network.

This chapter’s goal was to give you enough networking knowledge to make sense of the next chapter. However, it’s important that you explore these topics in greater depth, because comprehensive knowledge of networking principles and architectures can help you devise better algorithms.

I’ll suggest additional reading for each of the major topics covered in this chapter to get you started. I also recommend you revisit this chapter after working through some of the examples in this book.

The OSI reference model is available for reading online at `https://www.itu.int/rec/T-REC-X.200-199407-I/en/`. Two Requests for Comments (RFCs)— detailed publications meant to describe internet technologies—outline the TCP/IP reference model: RFC 1122 and RFC 1123 (`https://tools.ietf.org/html/rfc1122/` and `https://tools.ietf.org/html/rfc1123/`). RFC 1122 covers the lower An Overview of Networked Systems **15** three layers of the TCP/IP model, whereas RFC 1123 describes the application layer and support protocols, such as DNS. If you’d like a more comprehensive reference for the TCP/IP model, you’d be hard-pressed to do better than *The TCP/IP Guide* by Charles M. Kozierok (No Starch Press, 2005).

Network latency has plagued countless network applications and spawned an industry. Some CDN providers write prolifically on the topic of latency and interesting issues they’ve encountered while improving their offerings. CDN blogs that provide insightful posts include the Cloudflare Blog (`https://blog.cloudflare.com/`), the KeyCDN Blog (`https://www.keycdn.com/blog/`), and the Fastly Blog (`https://www.fastly.com/blog/`). If you’re purely interested in learning more about latency and its sources, consider “Latency (engineering)” on Wikipedia (`https://en.wikipedia.org/wiki/Latency_(engineering)`) and Cloudflare’s glossary (`https://www.cloudflare.com/learning/performance/glossary/what-is-latency/`) as starting points.

**16** Chapter 1

**2**

**R E S O U R C E L O C A T I O N A N D**

**T R A F F I C R O U T I N G**

To write effective network programs, you need to understand how to use human-

readable names to identify nodes on the internet, how those names are translated into addresses for network devices to use, and how traffic makes its way between nodes on the internet, even if they’re on opposite sides of the planet. This chapter covers those topics and more.

We’ll first have a look at how IP addresses identify hosts on a network.

Then we’ll discuss `routing`, or sending traffic between network hosts that aren’t directly connected, and cover some common routing protocols.

Finally, we’ll discuss `domain name resolution` (the process of translating human-readable names to IP addresses), potential privacy implications of DNS, and the solutions to overcome those privacy concerns.

You’ll need to understand these topics to provide comprehensive network services and locate the resources used by your services, such as third-

party application programming interfaces (APIs). This information should also help you debug inevitable network outages or performance issues your code may encounter. For example, say you provide a service that integrates the Google Maps API to provide interactive maps and navigation. Your service would need to properly locate the API endpoint and route traffic to it.

Or your service may need to store archives in an Amazon Simple Storage Service (S3) bucket via the Amazon S3 API. In each example, name resolution and routing play an integral role.

**The Internet Protocol**

The `Internet Protocol (IP)` is a set of rules that dictate the format of data sent over a network—specifically, the internet. `IP addresses` identify nodes on a network at the internet layer of the TCP/IP stack, and you use them to facilitate communication between nodes.
