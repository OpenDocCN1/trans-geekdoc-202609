# Example: Let us take a B-Tree of order 5

![](bbox=[0.233, 0.117, 0.756, 0.226])

Delete 175: here 175 are in leaf node, delete it from only leaf node.

![](bbox=[0.253, 0.263, 0.745, 0.372])

Delete 55: here 55 are not in leaf node. First it will be deleted from the node and the element of right side child will come in the node

![](bbox=[0.253, 0.43, 0.746, 0.539])

Delete 39: first 39 will be deleted from leaf node then left side element in the parent node will come in leaf node and last element of the left side node of the parent node will come in parent node.

![](bbox=[0.253, 0.616, 0.746, 0.725])

# 6.28 APPLICATION OF B-TREE

The main application of a B-tree is the organisation of a huge collection of records into a file structure. The organisation should be in such a way that any record in it be searched very efficiently i.e., insertion, deletion and modification operations can be carried out perfectly and efficiently.

# 6.29 B* TREES

The B-tree structure is the standard organisation for indexes in a database system. There are several variations of the B-tree, most well known being