+   A few factors to consider with the star topology include:
+   * **Reliability:** If the central device fails, the network fails.
+   * **Bandwidth speed:** While each device has its own dedicated connection to the hub, the overall throughput speed is dependent on the processing capacity of that central hub.
+   * **Scalability:** The central switch typically has a limited number of ports or connections that it can handle, possibly limiting expansion to accommodate future needs.
+   * **Collisions:** There is minimal risk of data collision as every node has its own dedicated connection.
+   * **Cost:** Quite low if only a few nodes are needed; however, costs can increase if the capacity limits of the central node are exceeded and upgrades are required.

> **Top tip!**
> Each topology (star, mesh, hybrid) serves different needs. Be sure to understand why each one is more suitable than another for specific situations. Learn the diagrams of the different topologies to visualize how nodes are connected, as that provides a crucial understanding of how the flow of data is impacted if a node fails.

# Mesh topology

In a mesh topology, every node has an immediate, direct connection to every other node. While most often depicted as a full mesh, partial meshes do also exist.
Meshes are suitable for large environments where reliability of individual pathways may be a concern. Critical infrastructure, such as military and aviation environments, is more inclined to use a mesh topology to help ensure robust resilience of the network against any point of failure.

![](bbox=[0.112, 0.496, 0.453, 0.781])

In a mesh topology, all nodes are interconnected to all other nodes

Wireless mesh systems, such as Meshtastic, have also started to gain popularity among tech hobbyists and as a means of providing connectivity in remote and disaster-prone areas.

+   Factors worth considering in a mesh environment include:
+   * **Reliability:** Highly reliable and robust against the failure of any individual node or communication path.
+   * **Bandwidth speed:** High, given that each node can communicate directly with its intended target node.
+   * **Scalability:** Adding new nodes is expensive as cabling and infrastructure must be run to all other nodes on the network.
+   * **Collisions:** Minimal risk of collisions due to the direct connections available.
+   * **Cost:** High due to all the additional cabling and networking infrastructure required for all the redundant connections.