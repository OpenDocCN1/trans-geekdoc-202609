
The more flexible a network design is, the more the network engineering staff will be able to make the business size and the network capacity track closely. This can reduce waste and lost opportunity.

## Translating Business Requirements into Technical

Understanding the business side and translating business requirements into technical solutions are two different things. What tools does the network designer have to apply these business problems to network design? Modularity is the primary tool; just as nature often places a choke point between complex systems, network designers use choke points to separate complexity from complexity in network designs. [Figure 22-3](#ch22.xhtml#ch22fig03) illustrates this concept.

![Image](graphics/22fig03.jpg)

**Figure 22-3** *Modularity*

The idea behind modularity is to split up a single problem into multiple pieces, solving each piece separately, and then using a set of connectors to allow information to flow edge to edge in the overall system. This concept is used almost everywhere in network engineering; you might recognize at least the following:

• Layering protocols into functional and topological units; in Day’s RINA model, there are two protocols, each with two functions, layered on top of one another. There are a pair of such protocols across each link, between each pair of hosts, and between each pair of applications.

• Building layers of virtual topologies on top of a single physical topology. Complexity is controlled by carrying a subset of the topology and reachability information in each virtual topology, and restricting policy to the destinations attached to the virtual topology.

• Breaking up a network into flooding domains in a link state protocol, and patching the network back together with L1/L2 intermediate systems, or Area Border Routers. The flooding domain boundary represents the boundary at which the topology information is summarized, and reachability information may potentially be.

Information hiding and modularity are closely related concepts. Any time information is being hidden, modules are being created. Just considering network design, modularizing a network can offer a number of solutions for business problems. Some specific examples:

• Choke points provide a point at which information can be hidden to control the scope and speed of state in the control plane. This, in turn, allows the network to scale.

• Choke points provide a point at which packets must move, providing a convenient place to implement packet forwarding policy, such as Quality of Service marking, security-focused filtering, etc.

• If modules can be sorted into “classes,” with each class having repeatable designs and configurations within the module, then building at least some parts of the network can be simplified into deploying the right module for a particular purpose. For instance, if modules 1 and 3 in [Figure 22-3](#ch22.xhtml#ch22fig03) are both campus networks of a similar size and scope, then they can be built in the same way, saving design and deployment effort. Repeatable modules also help make the network scale more closely with the business, as modules can be added or removed as complete units as needed.

• Modules can be sorted into “generations,” with newer designs replacing modules using older modules over time. This can help reduce the impact of the forklift upgrade problem, and hence allow the network to be more flexible in the face of business changes.

With all the positive points around modularization, are there negatives? In all areas of network design, it is important to remember:

**If you have not found the tradeoff, you have not looked hard enough.**

Although you have probably read this statement several times in this book, it applies to so many areas of network design and operation, it is well worth repeating. Several rules of thumb might be helpful.

*The first is the size of the modules*. If you make the modules too large, you are (probably) reducing the repeatability, not giving yourself enough places to hide information (which harms scaling), and not giving yourself enough places to insert policy into the network. If you make the modules too small, you reduce the effectiveness of the information hiding process. Finding the proper size is much like finding porridge that is just the right temperature—there is no clear-cut answer (or, perhaps a better answer, how many balloons fit in a bag?).

*The second is the optimization tradeoff*. Each time you hide information, you (more than likely) lose some form of optimization in the network. This is a fundamental rule, built into network and protocol design just because of the shape of reality.

*The third is using network complexity as your guide in determining where to place module boundaries*. In general, the best rule here is to separate complexity from complexity. For instance, if you have a large-scale spine and leaf data center fabric connected to a large partial mesh network core, it is probably best to put them into two different modules.

## What Is a Good Network Design?

Finally, with this background, it is possible to return to the original question this chapter began by asking: what is a good network design? The first point should be obvious: it should fulfill the business requirements laid out previously. This means the network should provide the connectivity needed to run the business at the lowest practical cost, and it should be easily adaptable to the size and scope of the business. Flexibility inherently implies scale, as well.

A second point is this: good network designs degrade gracefully, rather than falling over a cliff. [Figure 22-4](#ch22.xhtml#ch22fig04) illustrates.

![Image](graphics/22fig04.jpg)

**Figure 22-4** *Network degradation styles*

Any system that performs well under one set of conditions and fails to adapt to any change under less than optimal conditions is fragile; it has either ossified, or it was initially poorly designed. Another term sometimes applied to these sorts of systems is Robust Yet Fragile, which means these systems are apparently robust, and yet truly fragile under the right conditions.

A third point is this: good network designs allow operational staff to quickly find and repair failures. In other words, good network design interacts with the Mean Time to Repair (`MTTR`).

### Hierarchical Design

The rules of thumb on how to break up a network into modules are a good start, but they do not give you an entire picture. While they do give you a good set of ideas around what the goals of modularization should be, they do not provide a framework grounded in an intentional, systemic view of the network. Hierarchy is one design pattern that can be overlaid on top of modularization, or rather one pattern of modularization, and is often used to build large-scale networks. The essential points of modularization are as follows:

• Break up the functionality of the network into distinct pieces.

• Build modules around each piece, or purpose.

• Connect these modules through a set of special-purpose “interconnection” modules in a roughly hub-and-spoke topology.

[Figure 22-5](#ch22.xhtml#ch22fig05) is used to consider the basic three-layer hierarchical design model, which is often used in medium-scale networks.

![Image](graphics/22fig05.jpg)

**Figure 22-5** *A three-tier hierarchical design*
