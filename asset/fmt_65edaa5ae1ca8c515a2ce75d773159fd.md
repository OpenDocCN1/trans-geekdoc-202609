
Module 1 in Figure 22-5 is the network core. The primary—really the only— function assigned to the core module is to forward traffic as quickly as possible between distribution layer modules. There should be `no` control plane policy in this core; there should only be forwarding policy aimed at differentiated forwarding rules for `Quality of Service` and virtualization. This module will tend to be one of the more complex in terms of transports and equipment, and is also “unique” because there is just one core, so offsetting simplification in other areas allows the core to remain maintainable.

Modules 2 through 5 are considered the distribution layer. This layer is primarily responsible for carrying traffic within a region and all control plane policy. Each of the four modules in this layer should be as similar as possible; the physical configuration, at least, should be completely repeatable within a generation of each module across the entire network. Standardizing the hardware configuration across all of the modules in the distribution layer simplifies one part of the problem, allowing the complexity in this layer to reside in control plane policy, which is normally a complex problem.

Modules 6 through 13 reside in the access layer. Modules in the access layer are primarily responsible for providing connections into the network. Because of this, there will likely be many kinds of modules in the access layer. For instance, there may be one kind of module for supporting campus environments, another for supporting data center fabrics, and another for supporting Internet and extranet access. Traffic classification and security access should be focused in this layer of the network. Physical and logical configurations should be as repeatable as possible between modules of the same kind within the access layer.

An alternate form of hierarchy is the two-layer hierarchy, often used in smaller networks, illustrated in Figure 22-6.

![Image](img/22fig06.jpg)

**Figure 22-6** *A two-layer hierarchy*

The two-layer hierarchy appears to be a three-layer hierarchy with the access layer removed—but there are other subtle changes involved, as well. The aggregation layer, modules 2 through 5, are primarily responsible for providing connectivity into the network, as well as packet filtering and classification. Security functions also tend to be focused in the aggregation layer. As with the three-layer hierarchy, these modules should be physically and logically repeatable where possible.

The core, as in the three-layer model, is focused on forwarding traffic at high speed. The missing piece seems to be control plane policy; in the core/aggregation model, control plane policy is implemented along the edge between the core and aggregation modules.

Figure 22-7 shows an example of a recursively layered hierarchy, often used in very large-scale networks.

![Image](img/22fig07.jpg)

**Figure 22-7** *A recursive hierarchy*

Figure 22-7 illustrates what appears to be a simpler core/aggregation hierarchy. Looking more closely at module 2 in the aggregation layer, however, exposes an internal core/aggregation hierarchy, as well. The layer functions are the same; the core within module 2 (6) is focused on forwarding traffic quickly between the different aggregation modules (7 through 9) within module 2; the aggregation modules within module 2 are focused on providing connection, security, and classification; and control plane policy is imposed at the core/aggregation edge. This may appear to be a slightly modified version of a three-layer hierarchy, but there are several important differences:

• Regional policy is handled regionally, providing more flexibility in this area. Of course, this also means the modules are less likely to be logically repeatable, so there is more complexity in this kind of design.

• It is possible to build layers within layers more than once; module 6 may contain core and aggregation modules, as well. Because of this, the recursive layering architecture is a very powerful paradigm for building and understanding network topologies.

### Common Topologies

Another basic pattern in network design is the network topology. While it might seem there would be an infinite number of possible topologies, there are a few basic kinds that this infinite variety will fit into. Control planes tend to converge on any particular topology type based on the basic components—rings, meshes, and triangles. This section will consider a few basic topology types and some of their characteristics.

#### Ring Topologies

Ring topologies are among the simplest to design and understand. They are also the least expensive option, especially when long haul links are involved, so they tend to predominate in wide area networks.

##### Scaling Characteristics

Ring topologies have been scaled to large sizes; the additional cost to add a node is minimal. Generally, one new router (or switch), moving one circuit, and adding another new circuit is all that is needed. With careful planning, the addition of a new node into the ring can be accomplished without any real impact to overall network operations. Figure 22-8 depicts adding a node to a ring.

![Image](img/22fig08.jpg)

**Figure 22-8** *Adding a node to a ring*

Adding new nodes to the ring increases the total hop count through the ring (from 4 to 5 in this case), and it does spread the available bandwidth across more devices. However, every device on the ring still has just two neighbors; this constant neighbor count is much of the secret behind the scaling properties of ring networks.

As ring size increases, it becomes difficult to manage `Quality of Service` and optimal traffic flows. Figure 22-9 illustrates.

![Image](img/22fig09.jpg)

**Figure 22-9** *Traffic engineering in a ring topology*

In Figure 22-9, assume F has a voice over Internet Protocol (`VoIP`) stream connected to H, while G has some large file transfer (perhaps a complete backup). One of these streams requires very small amounts of bandwidth, low delay, and small amounts of jitter; the other requires large amounts of bandwidth but can tolerate a lot of delay and jitter. These two streams, however, share the `[D,E]` link. One option may be to force traffic along the “back side” of the ring to avoid the problem of having two kinds of traffic on the same link, but this would require tunneling one of the two streams using something like `Multiprotocol Label Switching` (`MPLS`). Another option may be to use a well-designed `Quality of Service` (`QoS`) mechanism to ensure the two streams can coexist. Either of these two solutions, however, adds complexity into the control plane and forwarding process. In terms of complexity, then, the ring topology requires just two neighbors per device, but it can require a lot more traffic engineering work to support all the requirements that applications place on the network.

##### Resilience Characteristics

Rings can withstand a single failure anyplace in the ring; any two failures will cause the ring to split. However, a single failure can make the kinds of traffic engineering problems considered in the preceding section much more difficult to manage; a single failure essentially turns a ring into a bus, with just one path between each pair of connected devices. The “middle segment,” in this case, will be a bandwidth choke point in a very negative way.

##### Convergence Characteristics

环形拓扑中的收敛为真正理解所有曾经设计或部署过的其他网络拓扑的收敛奠定了基础。在你理解了环形拓扑中路由收敛的原理后，就很容易将这些相同的原理应用到快速理解你可能遇到的任何其他拓扑的收敛。

换句话说，留心！

在考虑任何控制平面协议——路由或交换——在特定拓扑上如何运行时需要记住的关键点是，要以“首要指令”为思路思考：*切勿让数据包循环！* 这种对数据包循环的厌恶解释了环形拓扑的收敛特性。请考虑 Figure 22-10 中的环。

![Image](img/22fig10.jpg)

**Figure 22-10** *Convergence in a ring topology*

虽然通常认为路由会使用网络中的*每一条*链路，但协议会为每个目的地址构建一棵生成树。对于给定的目的地址，特定的链路会被从路径中阻断，以防止转发到目的地址的数据包在网络中循环。在 Figure 22-10 所示的两个环中，路由协议不会向 `2001:db8:3e8:100::/64` 转发数据包的链路已标出。

对于通往 `100::/64` 的四跳环：

• B 与 C 之间的链路似乎是单向指向 B。

• C 与 D 之间的链路似乎是单向指向 D。
