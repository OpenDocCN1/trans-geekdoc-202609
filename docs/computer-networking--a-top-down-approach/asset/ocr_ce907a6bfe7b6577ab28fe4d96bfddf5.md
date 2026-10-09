# 5.5.3 Data and Control Plane Interaction: An Example

In order to solidify our understanding of the interaction between SDN-controlled switches and the SDN controller, let’s consider the example shown in Figure 5.16, in which Dijkstra’s algorithm (which we studied in Section 5.2) is used to determine shortest path routes. The SDN scenario in Figure 5.16 has two important differences from the earlier per-router-control scenario of Sections 5.2.1 and 5.3, where Dijkstra’s algorithm was implemented in each and every router and link-state updates were flooded among all network routers:

+   - Dijkstra’s algorithm is executed as a separate application, outside of the packet switches.

+   - Packet switches send link updates to the SDN controller and not to each other.

In this example, let’s assume that the link between switch s1 and s2 goes down; that shortest path routing is implemented; and consequently and that incoming and outgoing flow forwarding rules at s1, s3, and s4 are affected, but that s2’s

![](bbox=[0.35, 0.44, 0.79, 0.87])

![](bbox=[0.25, 0.88, 0.75, 0.9])