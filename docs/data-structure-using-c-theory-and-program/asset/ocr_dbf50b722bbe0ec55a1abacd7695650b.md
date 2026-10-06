286

Data Structure Using C

![](bbox=[0.218, 0.093, 0.781, 0.233])

As we can see in the figure, the leaves have been connected to from linked list of keys in sequential order. The B+ Tree has two parts the first part is the index set that constitutes interior nodes and the second part is the sequential set that constitutes leaves.

# B+ Tree Structure

B+ Tree consists of two parts:

# Index Set

+   (i) Provide indexes for fast access of data.
(ii) Consist of internal nodes that store only key & sub tree pointers.

# Sequence Set

+   (i) Consists of leaf nodes that contain data pointers.
(ii) Provides efficient sequential access of data (using doubly linked list).

# Searching key in a B+ Tree

+   (i) Start from the root
(ii) If an internal node is reached
(iii) Search KEY among the keys in that node
(iv) Linear search of binary search
(v) If KEY \le smallest key, follow the leftmost child pointer down
(vi) If KEY > largest key, follow the rightmost child pointer down
(vii) If Ki \le KEY Kj, follow the child pointer between Ki and Kj
(viii) If a leaf is reached
(ix) Search KEY among the keys stored in that leaf
(x) linear search or binary search
(xi) If found, return the corresponding record; otherwise report not found.