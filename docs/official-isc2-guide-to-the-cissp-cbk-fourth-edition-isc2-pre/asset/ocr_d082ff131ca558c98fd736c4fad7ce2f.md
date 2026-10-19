network.

In a traditional IP network, each router performs an IP lookup ("routing"), determines a next-hop based on its routing table, and forwards the packet to that next-hop. Every router does the same, each making its own independent routing decisions, until the final destination is reached. MPLS does "label switching" instead. The first device does a routing lookup, just like before, but instead of finding a next-hop, it finds the final destination router. And it finds a pre-determined path from "here" to that final router. The router applies a "label" (or "shim") based on this information. Future routers use the label to route the traffic without needing to perform any additional IP lookups. At the final destination router, the label is removed, and the packet is delivered via normal IP routing.

# So What Is the Advantage of Label Switching?

Originally, it was intended to reduce IP routing lookups. When Classless Inter-Domain Routing (CIDR) was introduced, it had unintended consequences. CIDR introduced the concept of "longest prefix matching" for IP routing. Longest prefix match lookups have historically been very difficult to do. The classic software algorithm for routing lookups was called a PATRICIA trie, which required many memory accesses just to route a single packet. Exact matches were comparatively much easier to implement in hardware. Most early hardware routing "cheated" by doing the first lookup in software, then did hardware-based exact matching for future packets in the "flow". Label switching (or "tag switching") lookups use exact matching. The idea was to have only the first router do an IP lookup, then all future routes in the network could do exact match "switching" based on a label. This would reduce load on the core routers, where high-performance was the most difficult to achieve, and distribute the routing lookups across lower speed edge routers.

Modern Application Specific Integrated Circuits (ASICs) have eliminated this issue... mostly. Today, commodity ASICs can do many tens of millions of IP routing lookups per second, relatively cheaply and easily. However, they still make up a significant portion of the cost of a router. Exact matching is still much cheaper and easier to implement. A layer 2 only Ethernet switch that does exact matching may be a quarter of the cost and 4x the capacity of a similar device with layer 3 capabilities.

# So Why Do Security Professionals Still Care about MPLS?

Three reasons:

+   1. Implementing Traffic-Engineering — The ability to control where and how traffic is routed on your network, to manage capacity, prioritize different