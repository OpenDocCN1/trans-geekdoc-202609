

Justin Pettit, Kanna Rajagopal, and J. R. Rivers. “Elephant Detection in the vSwitch with Performance Handling in the Underlay.” *Network Heresy*, May 16, 2014. [https://networkheresy.com/2014/05/16/elephant-detection-in-the-vswitch-with-performance-handling-in-the-underlay/](https://networkheresy.com/2014/05/16/elephant-detection-in-the-vswitch-with-performance-handling-in-the-underlay/).

Karp, Brad Nelson. “Geographic Routing for Wireless Networks.” Harvard University, 2000. [http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.115.5738&rep=rep1&type=pdf](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.115.5738&rep=rep1&type=pdf).

Kaur, Harminder, Harsukhpreet Singh, and Anurag Sharma. “Geographic Routing Protocol: A Review.” *International Journal of Grid and Distributed Computing* 9, no. 2 (2016): 254.

McPherson, Danny R., and Keyur Patel. *Experience with the BGP-4 Protocol*. Request for Comments 4277. RFC Editor, 2006. [https://rfc-editor.org/rfc/rfc4277.txt](https://rfc-editor.org/rfc/rfc4277.txt).

Psounis, K., A. Ghosh, B. Prabhakar, and G. Wang. “SIFT: A Simple Algorithm for Tracking Elephant Flows, and Taking Advantage of Power Laws.” In *Proceedings of the 43rd Allerton Conference on Communication, Control and Computing*, 2005. [https://web.stanford.edu/~balaji/papers/05sifta.pdf](https://web.stanford.edu/~balaji/papers/05sifta.pdf).

Teixeira, Renata. “Hot Potatoes Heat Up BGP Routing.” Presented at the RIPE, Amsterdam, October 2005. [https://meetings.ripe.net/ripe-51/presentations/pdf/ripe51-hot-potatoes.pdf](https://meetings.ripe.net/ripe-51/presentations/pdf/ripe51-hot-potatoes.pdf).

Weiler, Nathalie. “Honeypots for Distributed Denial of Service Attacks.” IEEE, 2002. [http://www.csl.mtu.edu/cs6461/www/Reading/Weiler02.pdf](http://www.csl.mtu.edu/cs6461/www/Reading/Weiler02.pdf).

White, Russ. “Elephant Flows, Fabrics, and I2RS.” *Rule 11 Reader*, October 3, 2016. [http://rule11.tech/i2rs-elephant-flows/](http://rule11.tech/i2rs-elephant-flows/).

### Review Questions

1. 本章提到了运营商可能为网络优化的四种广泛类别。思考本章中给出的用例示例，并解释其中每一个可能适合哪一种优化类别以及原因。找出另外三个用例（需要找到来源）并解释它们各自可能适合哪一种优化类别以及原因。是否存在不适合这四种广泛类别中的任何一种的用例？你会添加什么类别来涵盖所有用例？

2. 除了热土豆路由和冷土豆路由之外，还有“捣碎土豆路由”。捣碎土豆路由的定义是什么，它有什么用途？

3. 本章将大象流和老鼠流描述为大流量、持久性流量，以及短时小流量。列出会产生每种流量类型的三个应用。

4. 在 [Figure 17-3](#ch17.xhtml#ch17fig03) 中，必须在 C 和 G 两处配置报文分类以支持区分 A 和 H 之间流动的流量。为什么需要在这两个地方进行配置？过滤器会相同吗？如果不同，它们会如何不同？

## Chapter 18
### Centralized Control Planes

#### Learning Objectives

After reading this chapter, you should understand:

![Image](graphics/bull.jpg)An overview of the interfaces between components in a network device used in building the information needed to forward packets

![Image](graphics/bull.jpg)The four different control plane models

![Image](graphics/bull.jpg)Using BGP as a southbound interface for a centralized control plane

![Image](graphics/bull.jpg)Using fibbing to modify paths in a link state protocol

![Image](graphics/bull.jpg)The Interface to the Routing System as a southbound interface

![Image](graphics/bull.jpg)The Path Control Element Protocol

![Image](graphics/bull.jpg)OpenFlow’s origins and operation

![Image](graphics/bull.jpg)ACP Theorem and the subsidiarity principle

As much as it might seem otherwise, the information technology field is strongly driven by egos and fashion. What was “in” last year will be “out” this year, often with very little reason other than “this is new, and that is old.” Network engineering is no different in this regard. For instance, network designs have swung between an “ideal” of decentralized control planes to centralized control planes a number of times over their history. Which is truly better?

The best way to cut through these pendulum swings, and their attendant hype factor, is to be able to understand the underlying problems, the underlying solutions, and the tradeoffs between the various solutions (as well as whether the problem at hand even needs to be solved at all—a point far too many designers and architects tend to forget). Toward this end, this chapter will begin by explaining a taxonomy of centralized control planes, developed on the model of a forwarding device.

With this model in hand, several specific examples will be surveyed. Each of these systems will be placed into the framework of the problems a control plane needs to solve, and the tradeoffs against distributed control planes, examples of which were considered in the preceding two chapters, will be examined. These solutions all fit into the roughly defined categories of a Software-Defined Network (SDN) or Programmable Network (PN).

### Considering the Definition of Software Defined

SDN is often presented as an either/or proposition: either you build a network using distributed protocols, *or* you build a network with a centralized control plane. The nebulous nature of the term *SDN* contributes to this way of seeing *software defined*. Specifically, how is an implementation of Open Shortest Path First (OSPF), for instance, not *software defined*? The general idea seems to be this: in hardware-based networks the software is *embedded* in appliances; the software and hardware are purchased, configured, and managed as one “thing.” In software defined, the software is separate from the hardware. Hence, in the SDN model, the software is seen as separate from the appliance; in the distributed model, the software has traditionally been seen as part of (or embedded in) the hardware. This brings us to a second false either/or divide. In reality, *every* distributed control plane is implemented in software, and hence can *always* be separated from the hardware.

Given software can always be separated from hardware, how can SDN be differentiated from the “traditional” model? The primary idea revolves around separating some part of the functionality of the control plane from the individual forwarding devices, or rather, pulling some part of the functionality of the control plane into a “centralized” control plane. It is important to note the term *centralized control plane*, as it is used here, does not mean a single “god box” that controls the network. Rather, it simply means a control plane that, in some way, does not run entirely on the network devices.

#### A Taxonomy of Interfaces

The SDN and PN worlds, in many ways, have their own terminology; the most important are the *southbound interface* and the *northbound interface*:

• The *southbound interface* is the interface between the controller and the network devices.

• The *northbound interface* is the interface between the controller and applications (or business logic).

Within the realm of southbound interfaces, there are a number of different interaction points, or ways in which the controller interacts with the forwarding devices.

[Figure 18-1](#ch18.xhtml#ch18fig01) shows four different control plane models:

![Image](graphics/18fig01.jpg)

**Figure 18-1** *Centralized control plane models*

