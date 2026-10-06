# 6.25 B TREE

In Multi-Way search tree, so many nodes have left tree but no right-tree. Similarly they have right sub-tree but no left sub-tree. Insertion of key also increases the height of tree. As we know the access time in tree is totally dependent on the height of tree. Our aim is to minimise the access time which can be tough balanced tree. So we have a need to take all the leaf nodes at same level and leaf nodes should not contain the empty sub-tree. So for an order where k<=n-1. For balancing the tree each node should contain n/2 keys. The B-tree of order n be defined as:

+   1. Each node has at least n/2 and maximum n non empty children.
2. All leaf nodes will be at same level.
3. All leaf nodes can contain maximum n-1 keys.
4. All non-leaf nodes can contain m-1 keys where m is the number of children
5. Keys in non-leaf node will divide the left and right tree where value of left sub-tree keys will be less and value of right sub-tree keys will be more than that particular key.

A balanced-order, multi-way search tree in which no root node contains at least [(n-1)/2 keys is called a B-tree of order n. A B-tree of order n is also called an n(n-1) tree or an (n-1) tree. Each node in the tree has a maximum of n-1 keys and children thus, a 4-5 tree is a B-tree of order 5, as is a 5-4 tree. In particular, a 2-3 (or 3-2) tree is the most elementary binary B-tree with one or two keys per node and two or three sons per node.

In discussing, the word "order" is used differently by different authors. It is common to find the order of a B-tree defined by the minimum number of keys in a non-root node i.e., (n-1)/2 and the degree of a B-tree to mean the maximum number of keys in a node i.e., n-1. A B-tree is a rooted tree having the following properties:

+   1. Every node has x the following fields:
(a) n [x] the number of keys currently stored in order x.
(b) The n [x] keys themselves stored in decreasing order, so that key1[x] ≤ key2[x] ≤ ...key n[x][x]
(c) Leaf[x], a Boolean value is TRUE if x is a leaf and FALSE if x is an internal node.

+   2. Each internal node x[x] separate the range of keys stored in each tree: if Ki is any key stored in the sub tree with root Ci[x] then, K1 ≤ key1[x] ≤ k2[x] ≤ ... to its children. Leaf nodes have no children, so Ci fields are fined.

+   3. The Keys key[x] separate the range of keys stored in each sub tree with root Ci[x] then, K1 ≤ key1[x] ≤ k2[x] ≤ ........ key n[x] ≤ key n[+1] + 1.