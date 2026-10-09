congestion occurs in the first place and at the cost of congestion (in terms of resources not fully utilized and poor performance received by the end systems). We’ll not (yet) focus on how to react to, or avoid, congestion but rather focus on the simpler issue of understanding what happens as hosts increase their transmission rate and the network becomes congested.

# Scenario 1: Two Senders, a Router with Infinite Buffers

We begin by considering perhaps the simplest congestion scenario possible: Two hosts (A and B) each have a connection that shares a single hop between source and destination, as shown in Figure 3.43.

Let’s assume that the application in Host A is sending data into the connection (for example, passing data to the transport-level protocol via a socket) at an average rate of $\lambda_{\text{in}}$ bytes/sec. These data are original in the sense that each unit of data is sent into the socket only once. The underlying transport-level protocol is a simple one. Data is encapsulated and sent; no error recovery (e.g., retransmission), flow control, or congestion control is performed. Ignoring the additional overhead due to adding transport- and lower-layer header information, the rate at which Host A offers traffic to the router in this first scenario is thus $\lambda_{\text{in}}$ bytes/sec. Host B operates in a similar manner, and we assume for simplicity that it too is sending at a rate of $\lambda_{\text{in}}$ bytes/sec. Packets from Hosts A and B pass through a router and over a shared outgoing link of capacity $R$. The router has buffers that allow it to store incoming packets when the packet-arrival rate exceeds the outgoing link’s capacity. In this first scenario, we assume that the router has an infinite amount of buffer space.

Figure 3.44 plots the performance of Host A’s connection under this first scenario. The left graph plots the **per-connection throughput** (number of bytes per

![](bbox=[0.1, 0.61, 0.9, 0.85])

**Figure 3.43** ♦ Congestion scenario 1: Two connections sharing a single hop with infinite buffers