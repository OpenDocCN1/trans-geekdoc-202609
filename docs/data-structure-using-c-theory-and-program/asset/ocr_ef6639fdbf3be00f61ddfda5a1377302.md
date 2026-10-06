4. Find

5. Exit

5

# 3.7 DOUBLE LINKED LIST

In a single linked list one can move from the first node to any node in one direction from left-to-right. This is why, a single linked list is also called as one way linked list. On the other hand, a double linked list is a two way linked list because one can move in both direction (left-to-right or right-to-left). A two way linked list is a linear collection of data elements nodes, where each node is divided into three parts:

+   (a) A pointer field prev which contains the location of the preceding node in the list.

+   (b) An information field info which contains the data.

+   (c) A pointer field next which contains the location of the next node in the list.

| Prev | Info | Next |

Figure Double linked list

The pointer prev of the first node and next of the last node contain the value NULL i.e. they do not store the address of any other node. This indicates the beginning and end of the list respectively. The advantage of a double linked list over a single linked list is that traversal is possible in both directions. This makes it an ideal data structure for applications like database and word processors in which moving in both directions is necessary.

# 3.8 OPERATIONS IN A DOUBLE LINKED LIST

There are various operations possible on a Doubly Linked List.

+   1. Traversing a double linked list.

+   2. Insertion of a node

+   (a) Insert at Beginning

+   (b) Insert at End

+   (c) Insert at a particular location

+   3. Deletion of a node

+   (a) Delete at Beginning

+   (b) Delete at End

+   (c) Delete at a particular location