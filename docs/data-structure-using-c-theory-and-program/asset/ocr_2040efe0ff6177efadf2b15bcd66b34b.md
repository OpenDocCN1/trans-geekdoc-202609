All paths from a node n to any external node will have same number of black nodes. If a path from root to external node has all the black nodes, then it will be the longest possible path. Since, black height of root node is k, each path will have k black nodes. Therefore, the total nodes in shortest path will be k and total nodes in longest path will be 2k. Thus, we see that no path in a red-black tree can be more than twice another node is at most 2log_2(n+1).

![](bbox=[0.285, 0.225, 0.712, 0.355])

# 6.21 INSERTION A NODE IN A RED-BLACK TREE

The insertion operations start in the same way as we add a new node in the binary search tree. However, in a binary search tree, we always add the new node as a leaf, while in a red-black tree, leaf node contain no data. Instead of adding the new node as a leaf, we add a red interior node that has two black leaf nodes. Remember that the colour of the new node is red and its leaf nodes are coloured in black. Once a new node is added, it may violate some property of the red-black tree. So in order to restore its property, we check for certain cases and restore depending on the case that turns after insertion. Before learning these cases in detail, let us discuss important terms that will be used.

+   (i) Grandparent node (G) of a n refers to parent of n's parent (P).
(ii) Uncle node (U) of a n refers to sibling of n's parents (P).

When we insert a new node in a red-black tree, note the following points:

+   1. All leaves are always black. Property 3 holds true.
2. Property 4 (both children of every red node is black) is threatened only by adding a red node, repainting a black node, or a rotation.
3. Property 5 (all paths from any given node to its leaf nodes has equal number of black nodes) is threatened only by adding a black node, repainting a red node, or a rotation.

Case 1: The new node n is added as the root of the tree

In this case, n is repainting black, as the root of the tree is always black. Since n adds one black node to every path at once.

Case 2: The new node's parent P is black

In this case, both children of every red node are black, so property 4 is not invalidated. Property 5 is also not threatened. This is because the new node n