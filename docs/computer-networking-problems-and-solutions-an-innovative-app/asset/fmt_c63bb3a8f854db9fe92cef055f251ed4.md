
In the standard configuration, as shown in [Figure 25-7](#ch25.xhtml#ch25fig07), adding stages does not really add more ports; instead you would scale out this kind of fabric. The scaling limit is the number of ports available on each device in the fabric, and the oversubscription rate is the difference between the amount of bandwidth offered by the ToR routers and the amount of bandwidth available from the ToR routers into the fabric.

One of the key points about spine and leaf fabrics is *they do not need a complex control plane to forward traffic correctly*. While most hyperscale networks do use a complex control plane, it is normally used to compensate for cross links, to provide information for an overlay virtual network, or to provide for some form of traffic engineering.

## Nonblocking versus Noncontending

What is the difference between *nonblocking* and *noncontending* networks? In a nonblocking network, there is no way for any packet to be blocked while traversing the network. Packet switched networks *cannot* be nonblocking. Consider, for instance, the network illustrated in [Figure 25-8](#ch25.xhtml#ch25fig08).

![Image](graphics/25fig08.jpg)

**Figure 25-8** *Nonblocking versus noncontending*

If every link in this network is the same bandwidth, then it is possible for B, C, D, and E to each send a stream the same size as their connected links to F, G, H, and K. Because the number of edge ports offered to servers, 4, is the same as the number of fabric side ports on each ToR, it is possible for each device connected to the fabric to fill its connection link into the fabric without anything being dropped. On the other hand, if B, C, D, and E each send a large stream toward A, the link from A to its connected ToR will need to switch four times more traffic than it has in available bandwidth. At this point, the fabric itself does not block any traffic, just the edge port facing the attached server. However, if F sends a full rate stream with A as the destination, there are now five full rate streams that the ToR at A needs to receive, and just four links on which to receive them. In this situation, one of the spine switches is going to need to block traffic (or, in this situation, throw enough traffic away to reduce the amount of traffic on the fabric to a level the available links can support).

In a circuit switched network, this problem would be solved on the inbound side through traffic scheduling, so the fabric itself does not block any traffic. In a packet switched network, however, it is still possible for multiple attached devices to send an overwhelming amount of traffic toward a single destination, causing the fabric itself to block traffic. There are two ways to resolve this kind of problem.

First, `QoS` controls can be placed on the network to control which traffic is forwarded and which is either dropped or at least queued for some amount of time. Second, the application can be designed to sense this sort of problem and slow down the rate at which it is transmitting. If these first two mechanisms sound familiar, it is because they are the same kinds of techniques used in any network to deal with congestion.

Two other helpful concepts in the fabric world are the type of tree. Skinny tree fabrics have the same link between every stage within the fabric (this does not include the ports provisioned for servers, however). Fat tree fabrics use a smaller number of higher-speed links in the center stage of the fabric, generally between the super spine and the spines, and lower-speed links between the spines and the ToR devices. In either case, the same oversubscription concepts apply; the primary difference between the two is optical, just in the amount of cabling and how the ports are configured on the various devices in the fabric.

### Traffic Engineering on a Spine and Leaf

Why would you ever need to deploy traffic engineering on a fabric designed with no oversubscription? [Figure 25-9](#ch25.xhtml#ch25fig09) is used to illustrate.

![Image](graphics/25fig09.jpg)

**Figure 25-9** *Traffic engineering in a fabric*

In [Figure 25-9](#ch25.xhtml#ch25fig09), assume A has some large flow destined to C, consuming just about all of A’s local link into the fabric, and is persistent; it will last for more than two or three seconds, potentially into the realm of days or months. These large, persistent flows are called elephant flows in the context of a data center fabric. Generally, elephant flows relate to large data transfers (such as those involved in moving a Hadoop job around on the fabric, or a database replication), and are not sensitive to jitter. Assume this flow is placed on the path `[V1, W2, X3, Y2, Z1]`. At some point during the duration of this elephant flow, B starts a short session with low bandwidth use requirements, in support of an delay or jitter sensitive application. Assume this flow is placed on the path `[V2, W2, X3, Y2, Z3]`.

Both of these flows are going to share the `[W2, X3]` and `[X3, Y2]` links. Given the nature of the two flows, the smaller flow, sometimes called a mouse flow, will not meet its jitter requirements even if there is plenty of bandwidth available on other paths on the fabric. To resolve this, the elephant flow needs to be pinned to a single path, and the path taken out of consideration for use by other flows passing through the network. This is the primary use case for traffic engineering in a noncontending data center fabric.

### A Larger-Scale Spine and Leaf

Many large (web- or hyper-) scale networks use a butterfly fabric, which is a variant of a Benes, and also a type of spine and leaf fabric. [Figure 25-10](#ch25.xhtml#ch25fig10) shows a small example.

![Image](graphics/25fig10.jpg)

**Figure 25-10** *A butterfly or Benes fabric*

In [Figure 25-10](#ch25.xhtml#ch25fig10), there are two fabrics, each of which might also be called a core, and a set of ToR devices. Each fabric is a full spine and leaf; each ToR connects to one point in each fabric. Depending on your perspective, this can be considered a five-stage fabric, ToR to ToR, or it can be considered a three-stage fabric with an additional set of access devices (though you would still never connect any devices or external access to the leaf nodes of the two fabrics in this network—all connectivity would be through one of the ToR routers or switches).

The primary advantage of such a design is the oversubscription rate and scaling can be adjusted within the limits of the fabric side ports of the ToR devices. To decrease the oversubscription rate, increase the number of cores. To increase the scale, increase the number of cores and ToR devices in parallel.

### Disaggregation in Networks

Disaggregation has caused a revolution in the way compute resources are built and used. Can these same concepts be applied to the network?

Networks have, “since forever,” been built out of appliances. A device is purchased from a vendor, racked, cabled, powered on, and configured through some sort of semiproprietary interface. Each device has a fairly unique feature set; in fact, the feature set of the software and hardware combined is the primary selling point, because the wide range of features (and nerd knobs) allows a single piece of gear to be used in a wide variety of networks, under a wide variety of conditions. This ability makes the appliance “future proof,” in the sense that no matter what problem you throw at the appliance, it is likely to have some feature that can be enabled to “solve” the problem (for some value of “solve”).

The result is an engineering world that

• Chases features whether or not they are needed to solve a particular problem right now, leading to overengineering in many cases.
