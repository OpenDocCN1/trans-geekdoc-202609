
Graceful Restart (GR) and ISSU rely on the device being able to forward traffic in hardware while the control plane is restarting; the hardware must be able to hold a forwarding table, and forward packets, without the control plane feeding new routing information into the forwarding table. There is some amount of risk in forwarding without the control plane, as the network topology can change while the control plane is restarting, causing a loop until the control plane reconverges. This is another instance of a microloop occurring because of topology unsynchronized databases.

Each of these solutions has advantages and disadvantages—each one is applicable in some situations and not in others—but engineers should be aware of these tools and their application to the problem of building a resilient network.

### Dual and Multiplanar Cores

While they are rarely used, dual plane and multiplanar cores are sometimes deployed to ensure the highest levels of availability. [Figure 23-6](#ch23.xhtml#ch23fig06) illustrates these two types of cores.

![Image](graphics/23fig06.jpg)

**Figure 23-6** *Dual and Multiplanar Cores*

In [Figure 23-6](#ch23.xhtml#ch23fig06), each core is represented with a different kind of dashed line to make it easier to see both of the cores. In both of these core types, *everything* is different:

• Equipment from two different vendors, or at least two different hardware lines using two different protocol implementations, is used to prevent a single bug or kind of failure from impacting the entire network.

• Two different interior gateway protocols, such as Open Shortest Path First (OSPF) and Intermediate System to Intermediate System (IS-IS), are used, one for each core, so a problem in a single protocol cannot impact the entire network.

• Two different providers, one for each core, are contracted to supply the links between the sites.

By creating two completely separate cores, you can avoid the problems associated with monocultures, or a bug that allows a problem to propagate throughout the network.

The primary difference between these two core types is shunt links, which are represented as dash-dot in the multiplanar core illustration on the right in [Figure 23-6](#ch23.xhtml#ch23fig06), such as the curved link between C and D. These shunt links are set to a very high metric, so they are used to forward traffic only if there is no other path available. An exterior gateway protocol, such as the Border Gateway Protocol (BGP), is used to tie the entire network together; each site edge router, such as A, would have two routes to any given destination in the network. One would be learned through BGP over one core, and the second through BGP over the second core.

### Modularity and Resilience

MTTR can be broken down into two pieces:

• The time it takes for the network to resume forwarding traffic between all reachable destinations

• The time it takes to restore the network to its original design and operation

The first definition relates to machine-level information overload; the less information there is in the control plane, the faster the network is going to converge. The second relates to operator information overload; the more consistent configurations are, and the easier it is to understand what the network should look like, the faster operators are going to be able to track down and find any network problems. The relationship between MTTR and modularization can be charted as shown in [Figure 23-7](#ch23.xhtml#ch23fig07).

![Image](graphics/23fig07.jpg)

**Figure 23-7** *Modularization Tradeoff with MTTR*

Moving from a single flat failure domain into a more modularized design, the time it takes to find and repair problems in the network decreases rapidly, driving the MTTR down. However, there is a point at which additional modularity starts increasing MTTR, where breaking the network into smaller domains causes the network to become more complex. To understand this phenomenon, consider the case of a network where every network device, such as a router or switch, has become its own failure domain (think of a network configured completely with static routes and no dynamic routing protocol). It is easy to see there is no difference between this case and the case of a single large flat failure domain. How do you find the right point along the MTTR curve? The answer is always going to be, “it depends,” but it is important to develop some general rules.

*First and foremost*, the right size for any given failure domain is never going to be the entire network (unless the network is really and truly very small). Almost any size network can, and should, be broken into more than one failure domain.

*Second*, the right size for a given failure domain is always going to depend on advances in control plane protocols, advances in processing power, and other factors. There were long and hard arguments over the optimal size of an OSPF area within the network world for years. How many LSAs could a single router handle? How fast would SPF run across a database of a given size? After years of work optimizing the way OSPF runs, and increases in processing power in the average router, this argument has generally been overcome by events.

Over time, as technology improves, the optimal size for a single failure domain will increase. Over time, as networks increase in size, the optimal number of failure domains within a single network will tend to remain constant. These two trends tend to offset one another, so most networks end up with about the same number of failure domains throughout their life, even as they grow and expand to meet the ever-increasing demands of the business.

So how big is too big? Start with the basic rules: building modules around policy requirements and separating complexity from complexity. After you get the lines drawn around these two things, and you’ve added natural boundaries based on business units, geographic locations, and other factors, you have a solid starting point for determining where failure domain boundaries should go.

From this point, consider which services need to be more isolated than others, simply so they will have a better survivability rate, and look to measure the network’s performance to determine if there are any failure domains that are too large.

### Final Thoughts on Resilience

While redundancy is the “go-to tool” for engineers building resilience into a network, redundancy has as many negative aspects that must be managed as it does positive aspects. Resilience requires much more than redundant links and devices; it must include many other techniques that involve the entire network stack from the physical links, through the control plane, and into the application itself.

Resilience, as with security, must be built into the network, rather than bolted on at the very end.

### Further Reading

Papadimitriou, Dimitri. “Inference of Shared Risk Link Groups.” Internet-Draft. Internet Engineering Task Force, November 2001. [https://datatracker.ietf.org/doc/html/draft-many-inference-srlg-02](https://datatracker.ietf.org/doc/html/draft-many-inference-srlg-02).

Pillay-Esnault, Padma, and John Moy. *Graceful OSPF Restart*. Request for Comments 3623. RFC Editor, 2003. [https://rfc-editor.org/rfc/rfc3623.txt](https://rfc-editor.org/rfc/rfc3623.txt).

Rekhter, Yakov, and Rahul Aggarwal. *Graceful Restart Mechanism for BGP with MPLS*. Request for Comments 4781. RFC Editor, 2007. [https://rfc-editor.org/rfc/rfc4781.txt](https://rfc-editor.org/rfc/rfc4781.txt).

Rekhter, Yakov, John Scudder, Srihari S. Ramachandra, Enke Chen, and Rex Fernando. *Graceful Restart Mechanism for BGP*. Request for Comments 4724. RFC Editor, 2007. [https://rfc-editor.org/rfc/rfc4724.txt](https://rfc-editor.org/rfc/rfc4724.txt).

Torrell, Wendy, and Victor Avelar. “Mean Time Between Failure: Explanation and
