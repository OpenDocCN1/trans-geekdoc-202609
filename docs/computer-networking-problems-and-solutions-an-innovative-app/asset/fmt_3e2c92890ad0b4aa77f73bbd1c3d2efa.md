
• In the **distributed** model, the control plane software runs *primarily* on forwarding devices. This does not mean the control plane software is *embedded* in the forwarding device. In an appliance model, the software is treated as an embedded part of the appliance itself. In a disaggregated model, however, the software runs primarily on the forwarding device, but the software is clearly delineated from the forwarding hardware.

• In the **augmented** model, the control plane software runs *primarily* on forwarding devices. Like the distributed model, the control plane is not necessarily embedded in the forwarding device. In the augmented model, the local control plane processes interact with the routing table (Routing Information Base, or RIB). Off-box processes interact with the distributed control plane to influence the set of loop-free paths installed in the RIB.

• In the **hybrid** model, the centralized component of the control plane runs in parallel with the distributed control plane. From the distributed control plane process running on each device, the controller just appears to be another distributed control plane running in parallel (in effect). From the controller’s perspective, much the same is true; the distributed control plane is just another control plane running in parallel with the controller.

• In the **replace** model, there is no distributed control plane; the centralized control plane is the only source of loop-free paths for the local switching device. One key marker of implementations using this model is the controller speaks directly to the forwarding table (FIB) rather than the RIB.

Within this framework, it is important to ask which *part* of the control plane— or more specifically, which functionality—is placed in the distribution control plane and which is placed in the centralized control plane.

### Considering the Division of Labor

Which *part* of the control plane is centralized is *the* crucial question when considering SDNs and PNs. What are the *parts* of a control plane?

There are three “things” a control plane must provide to support applications and businesses: topology information, reachability information, and policy. Almost every control plane implemented since the beginning of network engineering time has assumed these three functions are part of a single “thing,” and hence they must all be done in a single protocol.

Just as data planes are layered by function and location, however, it makes more sense to consider the control plane as a set of functions that can be split into layers. What would these layers look like?

• Discovering topology and advertising reachability are inseparable in some protocols, such as the Routing Information Protocol (RIP) and the Enhanced Interior Gateway Routing Protocol (EIGRP). In other protocols, such as Intermediate System to Intermediate System (IS-IS), the Shortest Path Tree (SPT) is calculated based on the topology, and reachability is “hung off the tree” as leaf nodes. Conceptually, then, it is difficult to see how topology and reachability could be separated into layers; the interplay between the two pieces of information is direct and immediate.

• Policy, on the other hand, relies on the topology and reachability information, but otherwise does not interact with topology and reachability. In fact, control plane policy is generally the process of overriding the basic topology and reachability information calculated by the control plane.

There appears to be a natural “split,” with topology and reachability on one side of the divide, and policy on the other side of the divide. It is possible, then, to break the control plane into two “layers,” with the bottom layer providing topology and reachability information, and the upper layer providing modifications to the paths calculated by the lower layer in order to implement specific policies.

### BGP as an SDN

While the Border Gateway Protocol (BGP) was originally designed to interconnect networks operated by different companies—particularly transit service provider networks—providers with large-scale data centers realized it could be used to scale spine and leaf fabrics. [Figure 18-2](#ch18.xhtml#ch18fig02) is used for illustrating BGP as used in a data center.

![Image](graphics/18fig02.jpg)

**Figure 18-2** *BGP in a data center fabric*

[Figure 18-2](#ch18.xhtml#ch18fig02) shows a five-stage spine and leaf fabric using eBGP as a control plane; as there are no “cross links” in a spine and leaf, there is no iBGP between (using the row and column identifiers to label routers) routers 5a and 5b. Rows 1 and 5 are Top of Rack (ToR) devices, connected to servers hosting the applications using the fabric.

To provide the example, assume some flow should be pinned between 5b and 1d. It is always possible to manually configure each router in the network with static routes to pin this one flow to a specific path, but this creates a lot of opportunities for configuration mistakes.

**Note**

Of course, you could always automate the configuration. But automation does not really reduce the amount of complexity; it just relocates the complexity from the human-to-device interface into a three-layer structure, human- to-automation system, automation system to device. In other words, automating a complex configuration does not make the configuration less complex; it just makes the complexity less apparent. There is no doubt this can sometimes be a good thing, but there is also no doubt automating a bad process does not improve the process. Automation can solve many things, but network engineers need to be careful in thinking automated configurations will “solve all problems.”

Another option, particularly since BGP is already running on every router in the network, is to use BGP as an SDN. Toward this end, an iBGP controller, shown at the bottom of the diagram, is connected to every router in the fabric.

**Note**

Only a small number of the iBGP connections are shown so the illustration remains readable.

Once the iBGP sessions are in place, the controller can “read” the entire topology and use local policies to determine which path the flow should be pinned to, and also which flows need to avoid the path over which the pinned flow is passing. For instance, assume the flow should be pinned to the [5b,4a,3c,2b,1d] path. A lower-cost path toward the destination (behind 1d) through 4a can be injected at 5b, and again through 3c at 4a, and again through 2b at 3c, etc., until the best path at each router along the path is through the selected path. The easiest way to accomplish this in BGP would be to inject a route from the controller with a lower local preference— but there are many ways to express such a policy in BGP.

This is an example of an augmented model; the centralized part of the control plane interacts with the distributed control plane (eBGP) directly. This is a rather interesting version of a hybrid model implementation, however, in that the protocol used to push policy (the southbound interface) is the same as the protocol used to discover and distribute topology and reachability information.

### Fibbing

Link state protocols, unlike BGP, are focused on finding the *shortest* path to a given destination; while most implementations do support tags that can be carried in the protocol, these tags are rarely (actually never) used to modify traffic flow. The reason for this is fairly simple: the link state database must be synchronized among all routers. If two routers have a different view of the network topology, it is possible they will compute a looped path through the network.
