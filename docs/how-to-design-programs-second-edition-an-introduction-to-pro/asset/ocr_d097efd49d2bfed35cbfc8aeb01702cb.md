# 31.2 A Problem with Generative Recursion

Let’s revisit the problem of “traveling” along a path in a graph:

**Sample Problem** Design an algorithm that checks whether two nodes are connected in a *simple graph*. In such a graph, each node has exactly one, directional connection to another, and possibly itself.

Chapter 29 covers the variant where the algorithm has to discover the path. This sample problem is simpler than that because this section focuses on the design of an accumulator version of the algorithm.

Consider the sample graph in figure 179. There are six nodes, A through F, and six connections. A path from A to E must contain B and C. There is no path, though, from A to F or from any other node besides itself.

![](bbox=[0.253, 0.464, 0.571, 0.523])

```
(define a-sg
 '((A B)
   (B C)
   (C E)
   (D E)
   (E B)
   (F F)))
```

Figure 179: A simple graph

The right part of figure 179 shows how to represent this graph with nested lists. Each node is represented by a list of two symbols. The first symbol is the label of the node; the second one is the single node that is reachable from the first one. Here are the relevant data definitions:

+   ; A SimpleGraph is a [List-of Connection]
+   ; A Connection is a list of two items:
+   ;   (list Node Node)
+   ; A Node is a Symbol.

They are straightforward translations of our informal descriptions.

We already know that the problem calls for generative recursion, and it is