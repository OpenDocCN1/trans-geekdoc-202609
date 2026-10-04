
Looking at the routing (or topology) table at A, then, will give you apparently wrong information about how the traffic is forwarded through the network to reach either of these destinations. While routing is still correct, using the routing table to see how traffic will be forwarded through the network— either for troubleshooting, design, or security—is of limited value. This kind of situation can arise with any routing protocol; forwarding is performed hop by hop through the network, with each device making an independent decision about where to send each individual packet.

### Spanning Tree Protocol

The `Spanning Tree Protocol` (`STP`) was originally designed by Radia Perlman, and first described in 1985 in *An Algorithm for Distributed Computation of a Spanning Tree in an Extended LAN*.^([1](#ch15.xhtml#ch15fn-1)) `STP` is unique in the list of control planes considered here because it was originally designed to support switching rather than routing. In other words, `STP` was designed to support forwarding on packets without a Time to Live (`TTL`), and without a per hop header swap by the switching device. Packets switched based on the `STP` are carried through the network without change.

#### Building a Loop-Free Tree

The process of building a loop-free tree is as follows:

1\. Each device places all ports in blocked mode so that no port will forward any traffic, and begins advertising Bridge Protocol Data Units (`BPDUs`) out each port. This `BPDU` contains

a. The ID of the advertising device, which is a priority combined with a local interface Media Access Control (`MAC`) address.

b. The ID of the candidate root bridge. This is the bridge with the lowest ID the local device knows about. If every device on the network starts at the same moment, then each device would advertise itself as the candidate root bridge until it learned of other bridges with a lower bridge ID.

2\. On receiving a `BPDU` on an interface, the root bridge ID contained in the `BPDU` is compared with the locally stored lowest root bridge ID. If the root bridge ID contained in the `BPDU` is lower, then the locally stored root bridge ID is replaced with the newly discovered bridge with a lower ID.

3\. After a few rounds of advertisements, every bridge should have discovered the bridge with the lowest bridge ID in the network and declared this bridge to be the root bridge.

a. This should occur while all the ports on all the devices are still in a blocked state (not forwarding traffic).

b. To make certain this does happen while all the ports are still blocked, a timer is set long enough to allow the root bridge to be elected.

4\. Once the root bridge is elected, the shortest path to the root bridge is determined.

a. Each `BPDU` also contains a metric to reach the root bridge. This metric may be a hop count, but the cost of each hop can vary based on administrative variables as well, such as the bandwidth of the link.

b. Each device determines the port through which it has the lowest cost path to the root bridge; this is marked as the root port.

c. If there is more than one path to the root bridge with the same cost, a tie breaker is used; this is normally the port identifier.

5\. For any link on which two bridges are connected

a. The bridge with the lowest cost path to the root bridge is elected to forward traffic off the link toward the root bridge.

b. The port connecting the elected forwarder to the link is marked as the designated port.

6\. Ports marked as either root or designated ports are allowed to forward traffic.

The result of this process is a single tree over which every destination in the network is reachable. [Figure 15-3](#ch15.xhtml#ch15fig03) is used to show how `STP` works in an actual topology.

![Image](graphics/15fig03.jpg)

**Figure 15-3** *Spanning Tree Protocol Operation*

Assume all the devices in [Figure 15-3](#ch15.xhtml#ch15fig03) were turned on at the same moment. There are a number of variations possible in timing, but the process of building a set of loop-free paths through the network would look, from F’s perspective, something like this:

1\. Elect the root bridge:

a. F advertises a `BPDU` to E and D with an ID and a candidate root bridge of `32768.0200.0000.6666`.

b. D (assuming D has not received any `BPDUs`) advertises a `BDPU` with an ID and a candidate root bridge of `28672.0200.0000.4444`.

c. E (assuming E has not received any `BPDUs`) advertises a `BPDU` with an ID and a candidate root bridge of `32768.0200.0000.5555`.

d. At this point, F will elect D as the root bridge, and start advertising `BPDUs` with its local ID and the candidate root bridge set to D’s ID.

e. At some point, D and E will both receive `BPDUs` from C, which has a lower bridge ID (`24576.0200.0000.3333`). On receiving this `BPDU`, they will both set their candidate root bridge ID to C’s ID and send new `BPDUs` to F.

f. On receiving these new `BPDUs`, F will note the new candidate root bridge ID is lower than its previous candidate root bridge ID, and it will then elect C as the root bridge.

g. After several rounds of `BDPUs`, all the bridges in the network will elect C as the root bridge.

2\. Mark the root ports by finding the shortest path to the root:

a. Assume each link is a cost of 1.

b. D will receive a `BDPU` from C with a local ID and root bridge ID of `24576.0200.0000.3333` and a cost of 0.

c. D will add the cost of reaching C, a single hop, advertising it can reach the root bridge with a cost of 1 to F.

d. E will receive a `BDPU` from C with a local ID and root bridge ID of `24576.0200.0000.3333` and a cost of 0.

e. E will add the cost of reaching C, a single hop, advertising it can reach the root bridge with a cost of 1 to F.

f. F now has two advertisements toward the root bridge with equal cost; it must break the tie between these two available paths. To do so, F examines the bridge ID of the advertising bridges. D’s bridge ID is lower than E’s, so F will mark its port toward D as its root port.

3\. Marking the designated ports on each link:

a. F’s only other port is toward E. Should this port be blocked?

b. To determine this, F compares its local bridge ID with E’s bridge ID. The priorities are the same, so the local port addresses must be compared to make the decision. F’s local ID ends in `6666`, while E’s ends in `5555`, so E’s is lower.

c. F does *not* mark the interface toward E as a designated port; instead, it marks this port as *blocked*.

d. E does the same comparison and marks its port toward F as a designated port.

e. D compares its cost toward the root with F’s cost toward the root.

f. D’s cost is lower, so it will mark its port toward D as a designated port.

[Figure 15-4](#ch15.xhtml#ch15fig04) illustrates the blocked, designated, and root ports once these calculations are completed.

![Image](graphics/15fig04.jpg)

**Figure 15-4** *The Result of the Spanning Tree Process*

The ports in [Figure 15-4](#ch15.xhtml#ch15fig04) are marked with `bp` for blocked port, `rp` for root port, and `dp` for designated port. The result of the process is a tree that can reach any segment in the network, and hence the hosts connected to any segment in the network. One interesting point about `STP` is the result is a *single* tree across the entire topology, anchored at the root bridge. If some host connected to E sends a packet to a host connected to B or F, the packet must travel through C, the root bridge, because one of the two ports on the `[F,E]` and `[E,B]` links is blocked. This is not the most efficient use of bandwidth, but it does prevent looping packets during normal forwarding.
