
6. Describe a situation where an overflow in a cache used to hold forwarding information can cause the control plane to forward packets until the cache is either timed out or otherwise cleared.

7. Read the explanation of a gray failure (from the paper noted in the “Further Reading” section). How do you think gray failures might relate to the discovery of neighbor status and checking for two-way connectivity?

8. Assume you could tag routes as they are being redistributed, and then filter based on those tags at all other redistribution points. Can you explain how this kind of tagging could be used to prevent redistribution routing loops?

9. It seems it would be possible to build a table that converts metrics from one protocol to another automatically during the redistribution process, and yet very few (almost no) routing protocols are designed with this kind of capability. What would be the problem with such a system?

10. One protocol, the Enhanced Interior Gateway Routing Protocol (`EIGRP`), does allow a routing process to set the external metrics directly from the external routing process. Can you figure out the circumstances when this is possible, and explain why?

## Chapter 12
### Unicast Loop-Free Paths (1)

**Learning Objectives**

After reading this chapter, you should be able to understand:

![Image](graphics/bull.jpg)The relationship between calculating a set of shortest paths and calculating a set of loop-free paths

![Image](graphics/bull.jpg)The concept of a Loop-Free Alternate and remote Loop-Free Alternate paths

![Image](graphics/bull.jpg)The difference between a minimum spanning tree and a Shortest Path Tree, and how they are calculated

![Image](graphics/bull.jpg)The waterfall or continental divide and P/Q models of preventing routing loops

![Image](graphics/bull.jpg)The concept of a greedy algorithm in finding loop-free paths

![Image](graphics/bull.jpg)The Bellman-Ford algorithm for finding loop-free paths

![Image](graphics/bull.jpg)The horizon point and split horizon

![Image](graphics/bull.jpg)How to find loop-free paths in the Diffusing Update Algorithm (`DUAL`)

Network engineers typically think of the control plane as doing a wide variety of things, from calculating the shortest path through the network to distributing policy used to forward packets. The idea of the *shortest path*, however, sneaks in the concept of the optimal path. Likewise, the idea of policy also sneaks in the concept of optimization of network resources. While both policy and the shortest path are important, neither one of these is at the root of what the control plane does. The job of the control plane is to find a set of loop-free paths through a network first; optimization is a nice add-on, but optimization can only be “done” in the context of finding a set of loop-free paths.

The question this chapter will answer, then, is

**How does a control plane calculate loop-free paths through a network?**

This chapter will begin by examining the relationship between the shortest, or lowest metric, path and loop-free paths. The next topic considered is Loop-Free Alternate (`LFA`) paths, which are not the best paths but still loop free. Such paths are useful in designing control planes that quickly switch from the best path to an alternate loop-free path in the case of failures or changes in the network topology. Two specific mechanisms used for finding a set of loop-free paths are then discussed; two more are discussed in [Chapter 13](#ch13.xhtml#ch13), “[Unicast Loop-Free Paths (2)](#ch13.xhtml#ch13).”

### Which Path Is Loop Free?

The relationship between the *shortest path*, generally in terms of metrics, and *loop-free paths* is fairly simple: *the shortest path is always loop free*. The reason for this relationship can be expressed most simply in terms of geometry (or more specifically *graph theory*, which is a specialized field of study within discrete mathematics). [Figure 12-1](#ch12.xhtml#ch12fig01) is used to explain why.

![Image](graphics/12fig01.jpg)

**Figure 12-1** *Available Paths Through a Network*

What are the paths available from A, B, C, and D toward the destination?

• From A: \[B,H\]; \[C,E,H\]; \[D,F,G,H\]

• From B: \[H\]; \[A,C,E,H\]; \[A,D,F,G,H\]

• From D: \[F,G,H\]; \[A,C,E,H\]; \[A,B,H\]

If every device in the network must choose the path it will use toward the destination independently (without reference to the path chosen by any other device), it is possible to form persistent loops. For instance, A could choose the path \[D,F,G,H\], and D could choose the path \[A,C,E,H\]. Device A will then forward traffic toward the destination to D, and D will then forward traffic toward the destination to A. There must be some rule other than *choose a path* implemented by the algorithm used to calculate a path on each device, such as *choose the shortest (or lowest cost) path*. But why does choosing the shortest (or lowest cost) path prevent the loop? [Figure 12-2](#ch12.xhtml#ch12fig02) illustrates.

![Image](graphics/12fig02.jpg)

**Figure 12-2** *Longer Paths Contain Shorter Ones*

[Figure 12-2](#ch12.xhtml#ch12fig02) assumes A chooses the path \[D,F,G,H\] to the destination, and D chooses the path through A to the destination. What D cannot know, because it is calculating a path to the destination without any knowledge of what A has calculated, is that A is using the path through D itself to reach the destination. How can the control plane avoid such a loop? By observing that the cost of a path along a loop must always contain the cost of the loop as well as the loop-free element of the path. In this case, the path through A, from the perspective of D, must include the cost from D to the destination. Hence the cost through A, from the perspective of D, will always be greater than the lowest available cost from D. This leads to the following observation:

**The lowest cost (or shortest) path cannot contain a path that passes through the calculating node**; or rather, **the shortest path is always loop free**.

There are two important points about this observation.

*First,* this observation does *not* say paths with higher costs are *definitely* loops, only that the lowest cost path *must not* be a loop. It is possible to expand the rule to discover a wider set of loop-free paths beyond the lowest cost path; these are called Loop-Free Alternates.

*Second*, this observation holds only if every node in the network has the same view of the network topology. Nodes can have different views of the network topology for a number of reasons; for instance:

• The network topology has changed, and all the nodes have not yet been notified of the change; hence microloops.

• Some information about the network topology has been removed from the topology database through summarization or aggregation.

• The metrics have been configured so the lowest cost path is inconsistent from different perspectives.

Control planes used in real networks are carefully crafted to either work around or minimize the impact of different devices having different views of the network topology, potentially causing a looped path. For instance:

• Control planes are carefully tuned to minimize the time differential between learning of a topology change and modifying forwarding (or to drop traffic during topology changes, rather than forwarding it).

• When summarizing topology or aggregating reachability, care is taken to preserve cost information.

• Network design “best common practices” encourage the use of symmetric metrics, and many implementations make it difficult or impossible to configure links with truly dangerous metrics, such as a zero link cost.

It often takes a great deal of design work to find, and work around or prevent, the unintended subversion of the shortest path rule in real-world control plane protocols.

**Why Not Use a Node List?**
