
• When processing `B`’s link state information, note `B` claims to be connected to `A`. Examining `A`’s link state information, however, the `D` cannot find any information from `A` claiming to be connected to `B`. Because of this, `D` will not use the `[A,B]` link.

This check is normally done either before a link is moved to the `TENT` or before a link is moved from the `TENT` onto the `PATH`.

### Border Gateway Protocol

In January 1989 at the 12th Internet Engineering Task Force (`IETF`) meeting in Austin, Texas, Yakov Rekhter and Kirk Lougheed sat down at a table and in a short time a new exterior gateway routing protocol was born, the `BGP`. The initial `BGP` design was recorded on a napkin rumored to have been heavily spattered with ketchup. The design on the napkin was expanded to three handwritten sheets of paper from which the first interoperable `BGP` implementation was quickly developed.

`BGP` was originally designed to be an Exterior Gateway Protocol (`EGP`), which means it was intended to connect networks, or Autonomous Systems (`ASes`), rather than devices. If `BGP` is an `EGP`, this must mean that the other routing protocols, like `RIP`, `EIGRP`, `OSPF`, and `IS-IS`, must be Interior Gateway Protocols (`IGPs`)—a designation that “stuck.” Clearly defining interior and exterior gateways has proven useful in designing and operating large-scale networks. `BGP` is unique among the widely deployed protocols in its loop-free path calculation. There are three widely used distance vector protocols (`Spanning Tree`, `RIP`, and `EIGRP`). There are two widely used link state protocols (`OSPF` and `IS-IS`). And there are many more examples of these two types of protocols developed and deployed in what might be considered niche markets. `BGP`, however, is the only widely deployed path vector protocol.

What are the most important goals for an `EGP`? The first is obviously selecting loop-free paths, but this clearly does not mean the *shortest* path. The reason the shortest path is not as important in an `EGP` as it is in an `IGP` is that `EGPs` are used to connect entities, such as service providers, content providers, and corporate networks. Connecting networks at this level means focusing on *policy*, rather than efficiency—in complexity terms, increasing state through policy mechanisms while reducing overall network optimization in pure traffic-carrying terms.

`BGP` policy mechanisms will not be considered here in any depth; some basic policy concepts are considered in [Chapter 17](#ch17.xhtml#ch17), “Control Plane Policy.” This section focuses on transport, peering, advertisement, and the `BGP` decision process.

#### BGP Peering

`BGP` does not provide any sort of reliable transport. Instead, `BGP` relies on `TCP` to carry information between `BGP` peers. Using `TCP` ensures

• `MTU` detection is handled, even for connections crossing several hops (or routers).

• Flow control is taken care of by the underlying transport, so `BGP` does not need flow control directly (although most `BGP` implementations do interact with the `TCP` stack on the local host to improve throughput for `BGP` specifically).

• Two-way connectivity between peers is ensured by the three-way handshake implemented in `TCP`.

Even though `BGP` relies on an underlying `TCP` connection for many of the functions control planes must solve in building adjacencies, there are still a number of functions `TCP` cannot provide. Therefore, a fuller look at the `BGP` peering process is still in order; [Figure 16-12](#ch16.xhtml#ch16fig12) illustrates.

![Image](graphics/16fig12.jpg)

**Figure 16-12** *The BGP Peering Process*

In [Figure 16-12](#ch16.xhtml#ch16fig12):

1. The `BGP` peering session begins in the idle state.

2. `A` sends a `TCP` open on port 179; `B` responds to an ephemeral port on `A`. After the `TCP` three-way handshake is completed (the `TCP` session is successful), `BGP` moves the peering state to connect. If the peering session is being formed across some type of state-based filtering, such as a firewall, it is important that the `TCP` open be transmitted from the “inside” of the filtering device.

3. If the `TCP` connection fails, the `BGP` peering state is moved to active.

4. `A` sends a `BGP` open to `B` and moves `B` to the opensent state. At this point, `A` is waiting on `B` to send a keepalive. If `B` does not send a keepalive within a specific period, `A` will move the session back to the idle state. The open message contains a number of parameters, such as which address families the two `BGP` speakers support and the hold timer. This is called capabilities negotiation. The lowest (minimum) hold timer of the two advertised is selected as the hold timer for the peering session.

5. When `B` sends `A` a keepalive, `A` moves `B` to the openconfirm state.

6. At this point, `A` will send `B` a keepalive to verify the connection. When `A` and `B` receive one another’s keepalives, the peering session will move to the established state.

7. The two `BGP` speakers exchange routes, so their tables are up to date. `A` and `B` only exchange their best paths, unless some form of `BGP` multipath is supported and configured on the two speakers.

8. To notify `A` it has finished sending its entire local table, `B` sends `A` an End of Table (`EOT`) or End of RIB (`EOR`) signal.

There are two kinds of `BGP` peering relationships: `BGP` peers within the same Autonomous System (`AS`, which generally means the set of routers within a single administrative domain, though this is a rather loose definition) are called internal `BGP` (`iBGP`) peers, and `BGP` peers between autonomous systems are called external (or exterior) `BGP` (`eBGP`) peers. While the two kinds of `BGP` peering relationships are built the same way, they have different advertisement rules.

#### The BGP Best Path Decision Process

As `BGP` is designed to interconnect autonomous systems, the best path algorithm is focused primarily on policy, rather than loop free-ness. In fact, if you examine any standard explanation of the `BGP` best path process, whether or not a particular path is loop free is not included in the decision process at all. How, then, does `BGP` determine a particular peer is advertising a loop-free route? [Figure 16-13](#ch16.xhtml#ch16fig13) illustrates.

![Image](graphics/16fig13.jpg)

**Figure 16-13** *BGP and Loop-Free Paths*

In [Figure 16-13](#ch16.xhtml#ch16fig13), each router is in a separate `AS`, so every pair of `BGP` speakers will form an `eBGP` peering session. `A`, which is connected to `2001:db8:3e8:100::/64`, advertises this route toward `B` and `C`. `BGP` route advertisements carry a number of *attributes*, one of which is the `AS Path` (others will be discussed later in describing the best path selection process). Before `A` advertises `100::/64` to `B`, it adds its `AS` number into the `AS Path` attribute. `B` receives the route and advertises it to `D`; before advertising the route to `D`, it adds `AS65001` to the `AS Path`. The `AS Path` then, tracing from `A` through `C`, looks something like this at every hop:

• As received by `B`: `[AS65000]`

• As received by `C`: `[AS65000, AS65001]`

• As received by `D`: `[AS65000, AS65001, AS65003]`

When `D` received the route from `B`, it will advertise it back to `C` (there is no split horizon in `BGP`). Assume `C`, in turn, advertises the route back to `A` for some reason (it would not in this situation, because the path through `A` would be a better path to the destination, but just to illustrate loop prevention), `A` will examine the `AS Path` and discover its local `AS` is in the `AS Path`. This is clearly a loop, so `A` simply ignores the route. Since this route is ignored, it is never placed in the `BGP` topology table; hence only loop-free routes are compared using the `BGP` best path process.

The `BGP` best path process consists of 13 steps in most implementations (the first step is not always implemented, as it is a local decision on the part of the `BGP` speaker):

1. The route with the highest weight is chosen. Some implementations do not implement a route weight.
