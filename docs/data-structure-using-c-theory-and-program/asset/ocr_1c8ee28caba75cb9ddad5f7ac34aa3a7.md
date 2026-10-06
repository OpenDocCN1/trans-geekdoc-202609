# Chapter 6 Trees

+   (i) Data: left link: it contains the info value.
(ii) Left link: it contains address of the left sub-tree.
(iii) Right link: it contains address of the right sub-tree.

When a node has no children, the corresponding pointer fields are NULL. Here, first member data is for information field of node, second member is for left child of node which points to the structure itself; and it contains the address of left child. If node has no left child then it should be NULL. Third member is for right child of node which also points to the address of right child. If node has no right child then it should be NULL. This type of representation is dynamic block of memory. They are allocated only on demand.

| Left | Info | Right |

![](bbox=[0.138, 0.34, 0.835, 0.56])

# Declare structure of tree node

```
Struct node
{
  Int info;
  Struct node *left;
  Struct node *righ;
};
```

# 6.8 TRAVERSING A BINARY TREE

Traversing a binary tree is the process of visiting each node in the tree exactly once in a systematic way. Unlike linear data structures in which the elements are traversed sequentially, tree is a non-linear data structure in which the elements can be traversed in many different ways. There are different algorithms for tree traversals. These algorithms differ in the order in which the nodes are visited.