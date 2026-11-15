+   • A list, stack, or queue.
+   • Ordered by position.
+   • Each item has parent (except 1st).
+   • Each item has child (except last).
+   • The order and position together are meaningful (consider a step-by-step process).

![](bbox=[0.131, 0.282, 0.871, 0.365])

Figure 14.2  A connected list of objects.

# 14.7  BRANCHED STRUCTURES

Branched structures are hierarchical collections, namely trees and graphs, which are commonly based on linked structures. A tree is essentially a graph without loops.

Trees and graphs lend to modeling real-world systems that are more complex than linear systems. In systems engineering, consider the graph aspects of network topologies, or the tree-like hierarchies of operating systems processes and file systems. The indexing of trees and graphs can be mapped to various linear structures to facilitate processing.

Due to the branches in trees and graphs, access to an element from another element may be direct (the elements