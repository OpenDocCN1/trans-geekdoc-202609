![](bbox=[0.18, 0.12, 0.88, 0.44])

# FIGURE 5.2 TBPS overlay structure on Chord# and its forwarding path.

2^l-th skipped node on the right side. These pointers are maintained as a routing table of the node. For example, the node with ID 1 has a pointer to 3 at levels 1 and 5 at level 2, as shown in the figure. This pointer set is called a “finger table.” The structure of the finger table is constructed by using the periodic message exchange between the neighbor nodes on each level.

A message toward a key is forwarded using upper-level pointers. By using this structure, any key can reach the corresponding node at most log₂ N hops, where N is the total number of nodes. Moreover, Chord# can maintain the same level of performance even when there are a small number of nodes, as long as the routing tables are updated sufficiently. Refer article [14] for more details about Chord#.

In ST, each subscriber or publisher joins a structured overlay network based on its key, which includes a string for the topic name. One broker can have multiple keys to contain multiple publishers or subscribers of different topics. To distinguish subscribers with the same topic name, a unique suffix (ID) is added to the topic name on each key. There is a subscriber segment and a publisher segment on each topic. The subscriber segment must exist on the right side of the publisher segment on Chord#, because it only has right-side pointers on upper levels. This structure enables publishers to detect the existence of subscribers using the neighbor link at level 0, thereby reducing the amount of redundant traffic from publishers when there are no subscribers [10].

In this TBPS overlay structure, the following theorem holds, as it uses Chord# as the base structure.

# Theorem 1

The maximum number of hops required to deliver a message for a topic and the number of connections each node need to accept are log₂ M, where M is the number of publishers and subscribers for a topic.