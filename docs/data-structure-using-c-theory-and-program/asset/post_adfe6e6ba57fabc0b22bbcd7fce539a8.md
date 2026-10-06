
4. All leaves have the same depth, which is the tree's height.

5. There are lower and upper bounds on the number of keys a node can contain. These bounds are expressed in a fixed integer $t \ge 2$ called the minimum degree of the B-tree:

- (a) Every node other than the root must have at least $t-1$ keys. Every internal node other than the root has at least $t$ children. If the tree is not empty, the root must have at-least one key.
- (b) Every node can contain at most $2t-1$ keys. Therefore, an internal node can have at most $2t$ children. We say that a node is full if it contains $2t-1$ keys.

## 6.26 INSERTION IN B-TREE

The insertion of key in a B-tree requires first traversal in B-tree. Through traversal it will find that key to be inserted is already existing or not. Suppose key does not exist in tree then through traversal it will reach a leaf node. Now we have two cases for inserting the key.

- 1. Node is not full
- 2. Node is already full

If the leaf node in which the key is to be inserted is not full, then the insertion is done in the node. A node is said to be full if it contains a maximum of $(m-1)$ keys, given the order of the B-tree to be $m$. If the node were to be full, insert the key into the existing set of keys in the node, split the node at its median into two nodes at the same level, pushing the median and element up by one level. Note that the split nodes are only half full. Accommodate the median element in the parent node if it is not full. Otherwise repeat the procedure and this may even call for rearrangement of the keys in the root node or the formation of a new root itself.

**Example: Insert these numbers in a B-Tree of order 5.**

20, 80, 55, 116, 39, 76, 124, 103, 48, 200, 98, 175, 235, 28, 114, 132, 164

**Solution:**

Insert 20: |20|

Insert 80: |20|80|

Insert 55: after insertion of 55, the keys in the node will be sorted.

|20|55|80|

Insert 15: after insertion of 15, the keys in the node will be sorted.

|15|20|55|80|

Insert 116: | 15 | 20 | 55 | 80 | 116 |

After insertion of 116, node is full, it is split into two nodes, 55 is the median key so it will go in parent node but root node is split so it will become root.

![](img/3d5da05d64722faaa72fdc4daca105f9_295_0.png)

Insert 39:

![](img/3d5da05d64722faaa72fdc4daca105f9_295_1.png)

Insert 76:

![](img/3d5da05d64722faaa72fdc4daca105f9_295_2.png)

Insert 124:

![](img/3d5da05d64722faaa72fdc4daca105f9_295_3.png)

Insert 103: After insertion of 103, node is full; it is split into two nodes, 103 is the median key so it will go in parent node.

![](img/3d5da05d64722faaa72fdc4daca105f9_295_4.png)

Insert 48:

![](img/3d5da05d64722faaa72fdc4daca105f9_295_5.png)

Insert 200:

![](img/3d5da05d64722faaa72fdc4daca105f9_295_6.png)

Insert 98:

![](img/3d5da05d64722faaa72fdc4daca105f9_295_7.png)

Insert 175: After insertion of 175, node is full; it is split into two nodes, 124 is the median key so it will go in parent node

![](img/3d5da05d64722faaa72fdc4daca105f9_296_0.png)

Insert 235:

![](img/3d5da05d64722faaa72fdc4daca105f9_296_1.png)

Insert 28: After insertion of 28, node is full; it is split into two nodes, 28 is the median key so it will go in parent node.

![](img/3d5da05d64722faaa72fdc4daca105f9_296_2.png)

Insert 114:

![](img/3d5da05d64722faaa72fdc4daca105f9_296_3.png)

Insert 132:

![](img/3d5da05d64722faaa72fdc4daca105f9_296_4.png)

Insert 164: After insertion of 164, node is full; it is split into two nodes, 116 is the median key so it will go in parent node. Here root is already full, so it is split into two nodes, 103 is the median key so it will become the new root.

![](img/3d5da05d64722faaa72fdc4daca105f9_296_5.png)

## 6.27 DELETION IN B-TREE

Deletion of key also requires traversal in B-tree, after reaching a particular node, two cases may occur:

- 1. Node is leaf node
- 2. Node is non-leaf node

For the first case, suppose node has more than minimum number of keys then it can be easily deleted. If it has only minimum number of keys then the first key of the adjacent node will go to the parent node and nodes will be combined into one node. Suppose now parent has less than minimum number of keys then the process is repeated until it gets a node which has more than minimum number of keys.

For the second case, if the deleted predecessor and successor have minimum number of keys then the nodes of predecessor and successor will be combined. Thus, while removing a key from a leaf node, if the node contains more than minimum number of elements it can be easily deleted. However, if the leaf node contains just minimum number of elements, scout for an element from either the left sibling or right sibling for vacancy. If the left sibling has more than minimum number of keys, pull the largest key up into the parent node and move down the intervening element from the parent node to the leaf node. Otherwise, pull the smallest key up of the right sibling to the parent node and move down the intervening element to the leaf node.

If both siblings have only minimum number of entries, then create a new leaf node out of the two leaf nodes and the intervening element of the parent node, ensuring that the total number does not exceed the limit. If while borrowing the intervening element from the parent node, the number of keys in the parent node falls below the minimum number, then propagate the property upwards, ultimately resulting in a reduction of height of the B-tree.

![](img/3d5da05d64722faaa72fdc4daca105f9_297_0.png)

**Example: Let us take a B-Tree of order 5**

![](img/3d5da05d64722faaa72fdc4daca105f9_298_0.png)

Delete 175: here 175 are in leaf node, delete it from only leaf node.

![](img/3d5da05d64722faaa72fdc4daca105f9_298_1.png)

Delete 55: here 55 are not in leaf node. First it will be deleted from the node and the element of right side child will come in the node.

![](img/3d5da05d64722faaa72fdc4daca105f9_298_2.png)

Delete 39: first 39 will be deleted from leaf node then left side element in the parent node will come in leaf node and last element of the left side node of the parent node will come in parent node.

![](img/3d5da05d64722faaa72fdc4daca105f9_298_3.png)

## 6.28 APPLICATION OF B-TREE

The main application of a B-tree is the organisation of a huge collection of records into a file structure. The organisation should be in such a way that any record in it can be searched very efficiently i.e., insertion, deletion and modification operations can be carried out perfectly and efficiently.

## 6.29 B* TREES

The B-tree structure is the standard organisation for indexes in a database system. There are several variations of the B-tree, most well known being the B* tree and B+ tree. The B-tree guarantees at least 50% storage utilisation, that is any given time, the tree has nodes at least 50% full. The B+ tree is a slightly different data structure, which in addition to indexed access, also allows sequential data processing and stores all data in the lowest level of the tree.

One of the major drawbacks of the B-tree is the difficulty of traversing the keys sequentially. B+ tree retains the rapid random access property of the B-tree, while also allows rapid sequential access. In the B+ tree, all keys are maintained in leaves and are replicated in non-leaf nodes to define the paths for locating individual records. The leaves are linked together to provide a sequential path for traversing the keys.
