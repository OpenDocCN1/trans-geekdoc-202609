# 3.2 REPRESENTATION OF LINKED LIST IN MEMORY

There are two ways to represent a linked list in memory:

+   1. Static representation using array.

+   2. Dynamic representation using free pool of storage

# 1. Static Representation

In static representation of a single linked list, two arrays are maintained: one array for information and other for links. Two parallel arrays of equal size are allocated which be sufficient to store the entire linked list. The static representation of the linked list is shown in figure:

| | Info | Next |
|---|---|---|n| 0 | 13 | 08 |
| 1 | | |
| 2 | 06 | 05 |
| 3 | 19 | 03 |
| 4 | | |
| 5 | 82 | X |
| 6 | | |
| 7 | | |
| 8 | 14 | 02 |
| 9 | | |
| . | | |
| . | | |
| . | | |
| 99 | | |
| Memory | ↑ | |
| Location | ↑ | |

Figure Static Representation of a Single Linked List using Arrays

# 2. Dynamic Representation

The efficient way of representing a linked list is using free pool of storage. In this method, there is a memory, which is nothing but a collection of free memory spaces, and a memory manager (a program). During the creation of linked list, whenever a node is required, the request is placed to the memory manager; memory manager will search the memory for the block requested and if found a desired block to the caller. Again, whenever a node is no more in use; it returns the unused node to the memory. Such a memory management is known as dynamic memory management.

In this section, we will study the following:

+   1. Single Linked List.

+   2. Circular Linked List.

+   3. Double Linked List.

+   4. Circular Double Linked List.