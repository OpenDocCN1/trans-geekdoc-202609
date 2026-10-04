
Hence, the traffic on the network prevents `STP` from converging, and the lack of convergence increases the traffic load on the network itself—a positive feedback loop causing havoc throughout the network. These events are called broadcast storms, and are common enough in `STP`-based networks to cause wise network designers and operators to limit the scope of any `STP` domain. The existence of broadcast storms has also driven a number of modifications to the operation of `STP`, such as simply replacing the base protocol with a true link state control plane.

### The Routing Information Protocol

The Routing Information Protocol (`RIP`) was originally specified in `RFC1058`, *Routing Information Protocol,* published in 1998.^([2](#ch15.xhtml#ch15fn-2)) The protocol was updated in a series of more recent RFCs, including `RFC2435`, *RIP version 2*,^([3](#ch15.xhtml#ch15fn-3)) and `RFC2080`, *RIP Next Generation for IPv6*.^([4](#ch15.xhtml#ch15fn-4)) [Figure 15-7](#ch15.xhtml#ch15fig07) is used to explain `RIP` operation.

![Image](graphics/15fig07.jpg)

**Figure 15-7** *RIP Operation Example*

The operation of `RIP` is deceptively simple. In [Figure 15-7](#ch15.xhtml#ch15fig07):

1\. `A` discovers `2001:db8:3e8:100::/64` because it is configured on a directly attached interface.

2\. `A` adds this destination to its local routing table with a cost of 1.

3\. As `100::/64` is installed in the local routing table, `A` will advertise this reachable destination (*route*) to `B` and `C`.

4\. When `B` receives this route, it will add the cost of the inbound interface so that the path through `A` has a cost of 2, and examine its local table for any lower-cost routes to this destination. As `B` has no other path to `100::/64`, it will install the route in its routing table and advertise the route to `E`.

5\. When `C` receives this route, it will add the cost of the inbound interface so that the path through `A` has a cost of 2, and examine its local table for any lower-cost routes to this destination. As `C` has no other path to `100::/64`, it will install the route in its routing table and advertise the route to `D` and `E`.

6\. When `D` receives this route, it will add the cost of the inbound interface from `C` so that the path through `C` has a cost of 3, and examine its local table for any lower-cost routes to this destination. As `D` has no other path to `100::/64`, it will install the route into its routing table and advertise the route to `E`.

7\. `E` will now receive three copies of the same route; one through `C` with a cost of 3, one through `B` with a cost of 4, and one through `D` with a cost of 5. `E` will choose the path through `C` with a cost of 2, installing this path to `100::/64` into its local routing table.

8\. `E` will not advertise any path to `100::/64` toward `C`, because it is using `C` as its best path to reach this specific destination. Thus, `E` will *split horizon* its advertisement of `100::/64` toward `C`.

9\. While `E` will advertise its best path, through `C`, to both `D` and `B`, neither will choose the path through `E`, as they already have better paths available toward `100::/64`.

`RIP` advertises a set of destinations and costs one hop at a time through the network; hence it is considered a *distance vector* protocol. The process that `RIP` uses to find a set of loop-free paths through the network is considered a distributed form of the `Bellman-Ford` algorithm, but it is not obvious how the process that `RIP` is using is related to `Bellman-Ford`.

#### Tying Bellman-Ford to RIP

To see the connection, it is best to think of each hop in the network as a single row in the topology table; this is illustrated in [Figure 15-8](#ch15.xhtml#ch15fig08).

![Image](graphics/15fig08.jpg)

**Figure 15-8** *RIP and Bellman-Ford*

[Chapter 12](#ch12.xhtml#ch12), “[Unicast Loop-Free Paths (1)](#ch12.xhtml#ch12),” describes `Bellman-Ford` operating across a topology table, arranged as a set of columns and rows. Using the row numbers indicated in [Figure 15-8](#ch15.xhtml#ch15fig08), you can build a similar topology table for this network, as shown in [Table 15-1](#ch15.xhtml#ch15tab01).

**Table 15-1** *A Topology Table Built from the Network in [Figure 15-8](#ch15.xhtml#ch15fig08)*

| **Row** || **Source (s)** || **Destination (d)** || **Distance (cost)** |

| --- | --- | --- | --- |

| 1 || `100::/64` || `A` || 1 |

| 2 || `A` || `B` || 1 |

| 3 || `B` || `C` || 2 |

| 4 || `C` || `D` || 2 |

Assume each row of the table is run through the `Bellman-Ford` algorithm by a different node. For instance, `A` computes `Bellman-Ford` across the first row and passes the result on to `B`. Likewise, `B` computes `Bellman-Ford` across the relevant rows and passes the result on to `C`. `Bellman-Ford` would still be the algorithm used to compute the set of loop-free paths through the network; it would simply be distributed across the nodes in the network. This, in fact, is how `RIP` operates. Consider the following:

1\. `A` computes the first row in the table, setting the predecessor for `100::/64` to `A` and the cost to 1. `A` passes this result on to `B` for the second round of processing.

2\. `B` processes the second row in the table, setting the predecessor for `100::/64` to `B` and the cost to 2. `B` passes this result on to `C` for the third round of processing.

3\. `C` processes the second row in the table, setting the predecessor for `100::/64` to `C` and the cost to 2. `C` passes this result on to `D`.

The `Bellman-Ford` distributed processing is more difficult to see in more complex topologies, because there is more than one “result table” being passed around the network. These “result tables” will eventually merge at the source node, however. [Figure 15-9](#ch15.xhtml#ch15fig09) illustrates.

![Image](graphics/15fig09.jpg)

**Figure 15-9** *Distributed Bellman-Ford in Parallel*

In [Figure 15-9](#ch15.xhtml#ch15fig09), `A` would compute a provisional result table as the first “round” of the `Bellman-Ford` algorithm, passing the result on to both `B` and `E`. `B` would compute a provisional result based on local information, passing this on to `C`, and then `C` to `D`. In the same way, `E` would compute a provisional result table based on local information, passing this on to `F`, and then `F` to `D`. At `D`, the two provisional results are combined into a final table from `D`’s perspective. Of course, the provisional table is considered final for the device at each hop. From `E`’s perspective, the table it computes based on locally available information plus the advertisement from `A` is the *final* table of loop-free paths to reach `100::/64`.

The entire distributed process has the same effect as walking across every row in the topology table the same number of times as entries in the topology table itself, slowly sorting the predecessor and cost fields for each entry based on newly set predecessors in the previous round of computation.

#### Reacting to Topology Changes

How does `RIP` remove reachability information from the network in the case of a node or link failure? [Figure 15-10](#ch15.xhtml#ch15fig10) is used to explain.

![Image](graphics/15fig10.jpg)

**Figure 15-10** *Link Failure in a RIP Network*

There are two different possible reactions to the loss of the `[A,B]` link, depending on the version and configuration of `RIP` running in this network. The first possible reaction is to simply let the information about `100::/64` time out. Assuming the *invalid timer* (a form of hold timer) for any given route is 180 seconds (a common setting in `RIP` implementations):

• `B` would notice the failed link immediately, as it is directly connected, and remove `100::/64` from its local routing table.

• `B` would stop advertising reachability to `100::/64` toward `C`.

• `C` will remove reachability to this destination from its local routing table and stop advertising reachability toward `100::/64` to `D` 180 seconds after `B` stops advertising reachability to `100::/64`.

• `D` will remove reachability to this destination from its local routing table 180 seconds after `C` stops advertising reachability to `100::/64`.
