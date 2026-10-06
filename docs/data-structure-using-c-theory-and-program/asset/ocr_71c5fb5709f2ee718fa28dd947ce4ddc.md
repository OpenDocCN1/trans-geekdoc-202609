# Chapter 6 Trees

```
parent->right=link;
parent->rightchild=temp;
```

# Deletion from a Threaded Binary Tree

There are three possibilities while performing deletion operation in threaded binary tree.

# Case 1: Node to be deleted is root node

If the node to be deleted is the root of the tree then the tree will become empty after its deletion so left pointer of head will be a thread pointing to it.

```
head->left=thread;
head->leftptr=head;
```

If the node to be deleted a left leaf node then the left pointer of parent will become a thread pointing to its in-order predecessor. Initially, its in-order predecessor was its left child but its in-order successor will be that node which was predecessor of its left child.

```
parent->left=thread;
parent->leftptr=loc->leftptr;
```

If the node to be deleted is a right leaf node the right pointer of parent will become a thread pointing to its in-order successor. Initially, its in-order successor was its right child but its in-order successor will be that node which was successor of its right child.

```
paren->right=thread;
paren->rightptr=loc->rightptr;
```

# Case 2: Node to be deleted has one child.

Delete the node as binary search tree. Find the in-order successor and in-order predecessor of the node to be deleted.

```
successor=inordersucessor(loc);
predecessor=inorderpredecessor(loc);
```

If the node has right sub-tree then put the predecessor of the node in the left pointer of its successor.

```
if(loc->right==link)
predecessor->leftptr=predecessor;
```

If node has left sub-tree then put the successor of the node in the right pointer of its predecessor.

```
if(loc->left==link)
predecessor-rightptr=successor;
```