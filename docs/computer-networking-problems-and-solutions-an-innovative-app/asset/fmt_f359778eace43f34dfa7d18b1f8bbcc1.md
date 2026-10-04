
When you are moving an existing application to public cloud IaaS, a second problem comes in the form of storage. How is the application data living in a local data center moved into the public cloud so the application has access to the data in the new environment?

For network engineers, this type of challenge is not a new one. Moving large amounts of data from one point to another separated by distance is a problem of constraints. First, the amount of bandwidth between two geographically diverse points is typically limited to a fraction of the bandwidth available in a data center. Second, latency can make it difficult to use the entirety of the bandwidth available to execute the transfer.

In a local area network (LAN), circuits are very high bandwidth, commonly interconnecting hosts to the network at speeds of 10, 25, 40, 50, and even 100Gbps. In the LAN scenario, bandwidth generally is not a constraint when moving storage data around the network. Bottlenecks in the transfer process are more likely to be found in the disk or host bus subsystems.

However, when the storage transfer is happening over a wide area network (WAN) such as the public Internet, bandwidth often becomes a constraint, as the bottleneck moves from host data bus or disk itself back to the network. Circuits interconnecting private and public clouds are very often less than 10Gbps. In addition, the connection might be lossy when compared to a LAN, requiring retransmissions and reducing overall throughput. This is one element network engineers must consider when computing how long it will take to move a storage volume from the local data center to the public cloud.

In addition to bandwidth constraints, latency has historically been a potential constraint. Assuming the Transmission Control Protocol (TCP) is the transfer mechanism, the amount of time waiting for an acknowledgment across the WAN means it might be difficult to fill the available bandwidth. This is a well-known issue for high-bandwidth, high-delay networks—so-called long fat networks (LFNs).

However, the challenge of fully utilizing the available bandwidth of LFNs has been addressed with several tuning techniques and variants to the TCP protocol. For instance, BIC-TCP, TCP Westwood, TCP Reno (with several variants), TCP Hybla, and TCP Vegas are all algorithmic variants of the core TCP congestion control algorithm, modifying window size in relation to round trip time to maximize throughput. Also notable, CUBIC TCP has seen recent attention in the IETF.

The point to keep in mind is populating a remote storage volume with terabytes of data via a copy operation across the public Internet will take more time than a comparable copy performed locally. This introduces a decision point. Is the performance sufficient enough so the copy can be done via network transfer? Or should data be copied onto a local, portable media and then shipped to the remote public cloud?

In a situation like this, there is no magic available to make terabytes of data in one place appear in another instantly. As such, this problem is a good example of under-standing the practical limitations of the available technology and working with the business to determine the proper course of action.

### Data Gravity

Once data has been populated in the remote cloud storage, moving data back out of the cloud presents challenges. One issue is a practical one: cost. While public cloud providers are keenly interested in their customers checking data in, they don’t want those customers to leave. Thus, public cloud providers charge as much as three to five times the ingestion transfer costs to move data back out. This is commonly known as the data gravity problem.

Data gravity is not a networking concern, but rather a business problem that network engineers should be aware of. For network engineers focused on the technology challenge, moving large amounts of storage data out of a public cloud presents the same challenges as moving the data into the cloud in the first place. Limited bandwidth and latency introduce constraints that might increase transfer times unacceptable to the business.

### Selecting Among Multiple Paths to the Public Cloud

While some organizations will connect to public cloud services using cloud exchanges, most organizations will connect to the public cloud via the Internet. Internet circuit costs have come down in price, making multiple Internet connections at the network edge affordable. This offers network engineers an interesting network design option. Rather than a single Internet connection at the edge, multiple connections offer both resiliency and additional bandwidth.

The challenge is how, exactly, to leverage multiple Internet edge circuits? The straightforward and obvious answer is via a routing protocol. In the case of the Internet edge, the routing protocol is BGP. However, while BGP enables the use of multiple Internet connections, BGP’s best path algorithm is focused on connectivity and not quality of application experience. BGP can only distinguish the relative closeness of one path versus another, and not whether a longer path might be better quality.

Since BGP is insufficiently nuanced to make optimal routing decisions at a per-application level, a market niche known as Software-Defined WAN (SD-WAN) has taken recent hold in the industry. SD-WAN solutions are typically proprietary forwarding schemes concocted by vendors. SD-WAN forwarding schemes prioritize quality of experience (QoE) for specific applications, and make forwarding decisions based on the QoE policy defined by a network engineer.

In the case of accessing the public cloud, an SD-WAN forwarding scheme will determine the best Internet circuit to use to provide the best service to the cloud consumer. For example, an SD-WAN forwarder might (allegedly) determine Internet circuit A is best to access the Microsoft Office 365 SaaS cloud, while Internet circuit B is best for Amazon Web Services IaaS hosted workloads.

Although unique to the many SD-WAN vendors offering products in this space, making a forwarding decision about what is best might include the following decision points:

1. **Circuit lossiness.** Is a circuit dropping packets? If so, to what degree? Loss will be more acceptable to some traffic, such as large file transfers, where recovery ensures data integrity. Loss will be unacceptable to traffic such as real-time voice, where a conversation will be impacted.

2. **Circuit jitter.** Is a circuit delivering packets on predictable time intervals? Like loss, jitter—a variance in the time delta between packet deliveries—is acceptable or not, depending on the packet payload.

3. **Circuit load.** How busy is a given circuit? SD-WAN solutions can choose to send traffic over a less loaded circuit to improve QoE for the traffic.

SD-WAN products take the routing design and administration out of the hands of the network engineer or the routing protocol, moving those concerns to software. For connectivity to public cloud, this means the end user QoE is optimized constantly, without the network engineer having to make unusual tweaks to the routing system. This approach has the added benefit of being able to add and remove Internet edge circuits to the scheme at will with a minimum of engineering.

The downside of SD-WAN solutions is they are proprietary. While there have been some very early conversations in the networking industry about making SDWAN solutions interoperable, the market is too nascent and unstable to have seen progress in SD-WAN standardization. The market is focused instead on product consolidation and customer growth.

## Security in the Cloud

With security breaches a regular part of the news cycle, the conversation of properly securing the public cloud becomes poignantly interesting. For network engineers, there are several concerns worth discussing:

1. Protecting data over public transport
