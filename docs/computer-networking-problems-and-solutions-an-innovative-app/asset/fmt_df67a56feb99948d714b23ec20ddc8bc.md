
## Installing the new forwarding information into the relevant local tables
In [Figure 14-1](#ch14.xhtml#ch14fig01), B and C must install the newly computed loop-free paths to destinations beyond E into their local forwarding tables, so traffic can be switched along the new path.

The following sections will focus on the first two of the four steps described in the preceding list, beginning with some thoughts on detecting topology changes. Some examples of protocols specializing in detecting topology changes will be considered. The distribution of topology and reachability information will take up the final half of this chapter. As this problem is, essentially, a distributed database problem, it will be addressed from that perspective.

## Detecting Topology Changes

The first step in reacting to a change in the network topology is to detect the change. Returning to [Figure 14-1](#ch14.xhtml#ch14fig01), how should the two devices connected to the link, C and E, detect the link has failed? The solution to this problem is not as simple as it might first appear for two reasons: information overload and false positives.

Information overload occurs when the control plane receives so much information it simply cannot distribute information about topology changes, and/or compute and install alternate paths into the relevant tables at each device, fast enough to keep the state of the network consistent. In the case of quick, persistently occurring changes, such as a link disconnecting and connecting every few milliseconds, the control plane can be overwhelmed with information, causing the control plane itself to consume enough network resources to cause the network to fail. It is also possible for a series of failures to trigger a positive feedback loop, in which case the control plane “folds in” on itself, either reacting very slowly or failing altogether. The solution to information overload is to hide the true state of the topology from the control plane until the rate of change is within the bounds the control plane can support.

False positives are the second sort of problem; if a link drops one packet out of every 100, and the single packet dropped each time just happens to be a control plane packet used to monitor the link’s state, the link will appear to go down and come back up (flap) quite frequently—even though other traffic is being forwarded across the link without problem.

There are two broad classes of solutions to the event detection problem:

• Implementations can send packets periodically to determine the state of a link, device, or system. This is `polling`.
• Implementations can trigger a reaction to a change in the state of a link or device off some physical or logical state within the system. This is `event driven`.

There are, as always, different tradeoffs with these two solutions, and subcategories of each one.

### Polling to Detect Failures

Polling can be performed `remotely`, or `out of band`; or `locally`, or `in band`; [Figure 14-2](#ch14.xhtml#ch14fig02) illustrates.

![Image](graphics/14fig02.jpg)

**Figure 14-2** *In Band and Out of Band Polling*

In [Figure 14-2](#ch14.xhtml#ch14fig02), A and B are sending a `hello`, or some other form of polling packet, periodically across the same link they are connected through, and the same link across which they are forwarding traffic. This is `in band polling`, which has the advantage of tracking the state of the link over which traffic is being forwarded, reachability information is being carried, etc. On the other hand, D is polling A and B for some information about the state of the `[A,B]` link from another location in the network. For instance, D could be checking the state of the two interfaces on the `[A,B]` link on a periodic basis, or perhaps sending a packet along the `[C,A,B,C]` path on a periodic basis, etc. The advantage here is information about the state of a large number of links can be centralized, making network management and troubleshooting easier. Both kinds of polling are often used in real-world network deployments.

Polling mechanisms often use two separate timers to operate:

• A timer to determine how often the poll is transmitted; this is often called the `polling interval` in the case of out of band polling, and is often called the `hello timer` in the case of in band polling
• A timer to determine how long to wait before declaring a link or device down, or to raise some sort of alarm; this is often called a `dead interval` or `dead timer` in the case of in band polling

The objective of in and out of band polling is often different. Out of band polling to discover changes in network state is often (but not always—specifically in the case of a centralized control plane) used to monitor the network state, and allows for centralized reactions to changes in state. In band polling is most often used (as you might expect) to detect changes in state locally, to drive the reaction of distributed control planes.

### Event-Driven Failure Detection

Event-driven failure detection relies on some local, measurable event to determine the status of a particular link or device. [Figure 14-3](#ch14.xhtml#ch14fig03) illustrates.

![Image](graphics/14fig03.jpg)

**Figure 14-3** *Event-Driven Detection Example*

**Note**

This is just an example; not all router implementations follow this model.

In [Figure 14-3](#ch14.xhtml#ch14fig03), which shows one possible implementation of the architecture elements between the physical interface and the routing protocol, there are four steps:

1. The link between the two physical interface (`phy`) chips located at either end of the link fails. Physical interface chips are normally optical to electrical hand-offs. Most physical interface chips also perform some level of decoding on the inbound information, converting the individual bits on the wire to packets (deserialization), and packets into bits (serialization). Information is encoded by the physical interface onto a carrier, which is supplied by the two physical chips connected to the physical media. If the link fails, or one of the two interfaces is disconnected for any reason, the physical interface chip on the other end of the link will see the carrier drop in near real time—usually based on the speed of light and the length of the physical media. This condition is called `loss of carrier`.
2. The physical interface chip will, on detecting `loss of carrier`, send a notification toward the routing table (`RIB`) on the local device. This notification normally starts life as an interrupt, which is then translated into some form of Application Programming Interface (`API`) call into the `RIB` code, which results in the routes reachable through the interface, and any next hop information through the interface, being marked stale or being removed from the routing table. This signal may, or may not, pass through the Forwarding Information Base (`FIB`) along the way, depending on the implementation.
3. The `RIB` will notify the routing protocol about the routes it just removed from the local table based on the interface down event.
4. The routing protocol can then remove any neighbors reachable through the indicated interfaces (or rather through the connected routes).

There is no point in [Figure 14-3](#ch14.xhtml#ch14fig03) in which there is a periodic process checking the state of anything, nor are there any packets moving across the wire. The entire process is based on the physical interface chip losing carrier on the connected media; hence this process is event driven.

It is often the case that event-driven and polled status are combined. For instance, in [Figure 14-3](#ch14.xhtml#ch14fig03), if there were a management station polling the status of the interface in the local `RIB` on a periodic basis, the process from the physical interface chipset to the `RIB` would be event driven, while the process from the `RIB` to the management station would be driven by polling.
