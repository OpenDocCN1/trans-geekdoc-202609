# Chapter 6 Trees

# 6.18 INSERTION IN AN AVL TREE

We can insert a new node in an AVL tree by finding its appropriate position similar to that of the binary search tree. But insertion of a new node involves certain overheads the tree may become unbalanced due to the increase in its height.

+   1. If the data item with key 'k' is inserted into empty AVL tree, then the node with key 'k' is set to the root node. In this case, the tree node is height balanced.

+   2. If tree contains only single node, i.e., root node, then the insertion of the node with key 'k' depends upon its value. If the value of 'k' is less than the value of the root then it is inserted to the left of the root otherwise right of the root. In this case the tree is height Balanced.

+   3. On inserting the node with key 'k' the height of the right sub-tree of the root has increased.

+   4. If on inserting a node with key 'k' the height of the left sub-tree of the root is increased i.e.,

+   (a) The height of right sub-tree of the left sub-tree of the root node is increased.

+   (b) The height of the left sub-tree of the root node is increased.

Example: insertion of the following keys in an AVL tree

55 66 77 15 11 33 25 44 88 99

Solution:

Insert 55:

![](bbox=[0.233, 0.587, 0.313, 0.634])

Insert 66:

![](bbox=[0.623, 0.005587, 0.753, 0.664])

Insert 77:

RR Rotation

![](bbox=[0.233, 0.696, 0.403, 0.796])

Insert 15:

![](bbox=[0.233, 0.844, 0.433, 0.944])