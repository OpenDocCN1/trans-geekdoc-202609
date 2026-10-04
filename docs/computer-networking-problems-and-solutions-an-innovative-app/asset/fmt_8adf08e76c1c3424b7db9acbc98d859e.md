
In [Chapter 9](#ch09.xhtml#ch09), “[Network Virtualization](#ch09.xhtml#ch09),” the case for building virtual topologies was laid out from the perspective of the data plane: primarily to provide traffic separation, reachability separation, and to provide “over the top” network services, particularly encryption and tunneled protocol support. There is an entirely separate case to be made for layering control planes, either with virtualized topologies, or without. Consider the security example set out previously in [Figure 19-8](#ch19.xhtml#ch19fig08); another way to solve the same problem might be to provision an overlay network, as shown in [Figure 19-9](#ch19.xhtml#ch19fig09).

![Image](graphics/19fig09.jpg)

**Figure 19-9** *An overlay as control plane information hiding*

In [Figure 19-9](#ch19.xhtml#ch19fig09), `A` needs to access `H` and `K`, but not `M`; `N` needs to access all three. Router `B` is a smaller device, perhaps a small home office router, which can support just a handful of routes. It is possible, of course, to filter routing information at `C` such that `B` has just the one or two routes it needs, but this may not be scalable from a network management perspective. Nor does this provide traffic separation, which is a requirement in many places where overlay networks are used. Meeting any traffic separation requirements would necessitate building packet filters at every device along the path, adding further to the network management load.

A better option, in many cases, is to create a virtual overlay network including just the devices that need to communicate. In this case, the dashed gray lines represent the virtual overlay network created to fulfill the requirements given. From an information hiding perspective, what is important to note is the following:

• `B` does not need to know about `D` or `G`, the links connecting them, nor the `2001:db8:3e8:102::/64` subnet; information about these topology elements and reachable destinations are hidden from the control plane at `B` by building a tunnel, or virtual topology, with one end at `B` and the other ends at `E` and `F`.

• The second control plane can run as a different process on `C`, `E`, and `F`; this second control plane also does not need to know about these topology elements or reachable destinations.

Some information about topology and reachability, then, is hidden from `B` entirely, and some processes on `C`, `E`, and `F`, without reducing the required reachability. To connect this back to the concept of failure domains, routers that do not know about specific topology elements and/or reachable destinations do not need to recalculate the set of loop-free paths through the network when those (hidden) elements change. Because of this, `B` can be said to be in a different failure domain than `D` and `G`. Virtualization, then, can often be treated as another form of information hiding.

### Caching

Caching begins with a simple observation: not all forwarding information is used all the time. Rather, particular flows pass along particular paths in a network, and particular pairs of devices (typically) only communicate for short periods of time. Storing forwarding information for short-lived flows, and in devices far off the path any particular flow might use, is a waste of resources. [Figure 19-10](#ch19.xhtml#ch19fig10) is used to illustrate.

![Image](graphics/19fig10.jpg)

**Figure 19-10** *Considering why caching works*

In [Figure 19-10](#ch19.xhtml#ch19fig10), the path from `A` to `2001:db8:3e8:100::/64` does not pass through `C`, `E`, or `F`; if `A` is the only device that ever originates paths toward this destination, it is a waste of memory and processing power for `C`, `E`, and `F` to calculate shortest paths to the `100::/64` destination. But how would `E` know no host attached to `101::/64` is going to send traffic to some device connected to `100::/64`? There is no way, from a control plane perspective, to know this.

Instead, `E` must rely on traffic as it passes through the network. For instance, `E` could calculate a route toward `100::/64` when some packet is transmitted from a locally attached host toward some destination on the `100::/64` subnet. This is a reactive control plane. Caching is not restricted to reactive control planes, however. It is possible for `E` to calculate a loop-free route to `100::/64`, but to not install this information into its local `FIB`. This is another form of `FIB` compression, which can be used when the size of the `RIB` is not limited, but the size of the `FIB` is (for instance, when there is a limited hardware forwarding table). `FIB` compression was once quite common in network devices but has generally fallen out of favor as the cost of memory has decreased and other techniques to store more forwarding information in smaller amounts of memory have been developed and deployed.

**Note**

There are also bad memories in the culture of network engineering around `RIB` to `FIB` caching schemes; in the late 1990s, many provider networks failed due to these schemes, so many network engineers avoid such schemes—and often rightly so. There are many interesting and unpredictable failure modes in `RIB` to `FIB` caching schemes, beyond those found in “normal” caching schemes.

The key question in any caching scheme is: how long should the cached information be held? There are at least two answers to this question:

• Remove a cache entry some specific time after it has been installed, or some specific time after its last use to forward a packet; this is timer based.

• Remove the oldest or most specific cache entries when the cache reaches some percentage of its capacity; this is capacity based.

Normally these are combined, with the first being the “normal” process for removing stale cache information, and the second used as a “safety valve” to prevent the cache from overflowing. Caches normally rely on the number of forwarding table entries *in use* being some small percentage of the reachable destinations. Generally, the rule of thumb is somewhere around 80/20—80% of the traffic will be directed at 20% of the destinations, or, in other situations, about 20% of the total reachable destinations will need to be stored at any given time.

There are a number of problems designers face when caching forwarding information in this way. [Figure 19-11](#ch19.xhtml#ch19fig11) is used to illustrate one interesting failure mode.

![Image](graphics/19fig11.jpg)

**Figure 19-11** *An interesting cache failure mode*

In [Figure 19-11](#ch19.xhtml#ch19fig11), `E` has 100 hosts attached; at the same time, `C` and `D` can support 70 entries in their forwarding table and will start removing items from cache when their forwarding table is 80% full (so when the cache reaches 56 entries, the caching algorithm begins removing the oldest entries to bring the cache under some number of total entries, say 50 for the purposes of this example). Assume caching is taking place at the individual destination IP address level, rather than at the subnet level (the reason for this will be explained in a following example). The situation that caching solutions normally assume is that `A` will communicate with a limited number of the 100 possible destinations at once. If `A` builds sessions with 20 of these destination devices for one minute, then another 20 the next minute, and so on, the cache can be “tuned” to carry information about any particular reachable destination for just a few seconds after its last use.
