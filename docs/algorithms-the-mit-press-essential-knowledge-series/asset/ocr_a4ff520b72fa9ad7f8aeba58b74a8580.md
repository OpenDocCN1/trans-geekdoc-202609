![](bbox=[0.125, 0.093, 0.595, 0.276])

If we run the algorithm, we find that two nodes, pages
1 and 4, end up with zero pagerank:

| Round | Page 1 | Page 2 | Page 3 | Page 4 | Page 5 | Page 6 |
| --- | --- | --- | --- | --- | --- | --- |
| start | 0.17 | 0.17 | 0.17 | 0.17 | 0.17 | 0.17 |
| 1 | 0.08 | 0.22 | 0.14 | 0.00 | 0.42 | 0.14 |
| 2 | 0.00 | 0.25 | 0.25 | 0.00 | 0.29 | 0.21 |
| 3 | 0.00 | 0.22 | 0.22 | 0.00 | 0.33 | 0.22 |

What happened is even though there is no dan-\angling node, there is a set of nodes that act as a sink for the
rest of the graph. If you scrutinize the graph, you will see
that the nodes 2, 3, 5, and 6, taken together as a group,
have only incoming links. It is possible to go from node 1
or 4 to this group, but once we are are in, we can only move in-
side the group. We are not able to go outside. Our random
surfer will be trapped, not inside a single web page this