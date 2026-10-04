
There are many instances where it is more effective, or in line with specific policy restrictions, for a control plane to learn reachability and topology information from another control plane, rather than through the mechanisms outlined up to this point in this chapter. Some examples might be as follows:

• Two organizations need to interconnect their networks, but neither wants to allow the other to control the policies and operation of their control planes
• A large organization is made up of many business units, each of which is allowed to run its own internal network based on local conditions and application requirements.
• An organization needs some way to allow two control planes to interoperate while transitioning from one to the other.

The reasons for allowing one control plane to learn reachability information from another are almost boundless. Given the requirement, many network devices allow operators to redistribute information between control planes. Redistributing reachability raises two control plane–related problems: how to handle metrics and how to prevent routing loops.

### Note

Redistribution can be seen as exporting routes out of one protocol and into another. In fact, import/export and redistribution are often used to mean the same thing, either by different vendors, or even in different situations by the same vendor.

### Redistribution and Metrics

The relationship between link properties, policies, and metrics are defined by each control plane protocol independently of other protocols; in fact, a more descriptive, or otherwise more useful, metric system is what sometimes attracts operators to a specific control plane protocol. Figure 11-11 illustrates two sections of a network running two different control planes, each of which uses a different method to calculate link metrics.

![Image](graphics/11fig11.jpg)

**Figure 11-11** *Redistribution and Metrics*

Protocols X and Y, in this network, have been configured using two different systems for assigning metrics. In deploying protocol X, the administrator divided 1,000 by the link speed in gigabits. In deploying protocol Y, the administrator set up a “table of metrics,” based on a best guess at the highest and lowest speed links they might have for the next 10 to 15 years, and assigned metrics to different link speeds within this table. The result, as the illustration shows, is incompatible metrics:

• 10G links in protocol X have a metric of 100, while in protocol Y they have a metric of 20.
• 100G links in both protocol X and Y have a metric of 10.

Assuming the lower metric is preferred, if the metrics are added, the [B,C,F] link would be considered a more desirable path than the [B,D,G] link. If the bandwidth is considered, however, both links would be considered equally desirable.

If redistribution is configured between these two protocols, how should these metrics be handled? There are three common solutions to this problem.

**The administrator can assign a metric at each redistribution point,** which is carried as part of the internal protocol metric. For instance, the administrator might assign a metric of 5 to the destination E at router C when redistributing from protocol X into Y. This destination, E, is injected into protocol Y with a metric of 5 by router C. At router F, the metric to E would be 25 through C. At G, the cost to reach E would be 35, along the path [F,C]. The desirability of using any particular exit point for any specific destination is chosen by the operator when these manual metrics are assigned.

**The metric of the “other” protocol can be accepted as part of the internal protocol metric.** This does not work in the case where one protocol has a wider range of available metrics than the other. For instance, if protocol Y has a maximum metric of 63, the 10G metrics from protocol X will be “above maximum”; a situation that is not likely to be optimal. Assuming no such restriction, router C would inject a route to E with a cost of 100 into protocol Y. The cost to reach E at router F would be 110; the cost at G would be 130 through [F,C].

### Note

You might recognize a tradeoff between control plane state and optimal use of the network here, another instance of the complexity tradeoffs in real-world protocol design. Carrying the external metric in a separate field adds control plane state, but allows more optimal steering of traffic through the network. Assigning or consuming the external metric reduces control plane state, but at the cost of being able to optimize traffic flow.

**The external metric can be carried as a separate field,** so each network device can make a separate determination about the best path to each external destination. This third solution is the most widely used, as it provides the best ability to steer traffic between the two networks. In this solution, C injects reachability to E with an external cost of 100. At F, there are two metrics in the advertisement describing reachability to E; the internal metric to reach the redistribution (or exit) point is 20, and the metric to reach E within the external network is 100. At G, the internal metric to reach the exit point is 30, and the external metric is 100.

How would an implementation use both of these metrics? Should the protocol choose the closest exit point, or rather the lowest internal metric? This would optimize the local network usage, and potentially deoptimize the usage of network resources in the external network. Should the protocol choose the exit point closest to the external destination, or rather the lowest external metric? This would optimize network resources in the external network, potentially at the cost of deoptimizing the use of network resources in the local network. Or should the protocol try to combine these two metrics in some way, to optimize the use of resources in both networks as much as possible?

Some protocols choose to always optimize local or external resources, while others will provide operators with a configuration option. For instance, a protocol may allow external metrics to be carried as different *types* of metrics, where one type is considered larger than any internal metric (hence preferring the lowest internal metric first, and using the external metric as a tie breaker), and the other type is where the internal and external metrics are considered equivalent (hence adding the internal and external metrics to make a path decision).

### Redistribution and Routing Loops

In the discussion above, you might have noticed that destinations redistributed from one protocol to another always appear as if they are connected to the redistributing router. In essence, redistribution acts as a form of summarization (which means topology information is removed, rather than reachability information), as described earlier in this chapter. While this point isn’t crucial to redistribution metrics, it is important to consider in the ability of the control plane to choose the optimal path. In some specific cases, deoptimization can lead to a complete failure of the control plane to choose loop-free paths; Figure 11-12 illustrates.

![Image](graphics/11fig12.jpg)

**Figure 11-12** *Redistribution Routing Loop*

To build the routing loop in this network:

1. The route to host A is redistributed from protocol X to Y with a manually configured metric of 1.
2. Router E prefers the route through C with a total metric (internal and external) of 2.
3. Router D prefers the route through E with a total metric of 3.
4. Router D redistributes the route to host A into protocol X with the existing metric of 3.
5. Router B has two routes to A: one with a cost of 10 (directly) and one with a metric of 4 through D.
6. Router B chooses the path through D, creating a routing loop.
7. And so on (the loop will continue until each protocol reaches its maximum metric).
