# Linked List

# 3.1 INTRODUCTION

An array is a very useful data structure provided in programming languages. However, it has some limitations.

+   1. Memory storage space is wasted, as the memory remains allocated to the array throughout the program execution even few nodes are stored. Because additional nodes are still reserved and their storage can't be used for any purpose.
2. The size of array can't be changed after its declaration i.e., its size has to be known at compilation time.

These limitations can be overcome by using linked list data structure. Linked list is the most commonly used data structure to store similar type of data in memory. The elements of a linked list are not stored in adjacent locations as in arrays. In, once memory space is allocated it cannot be extended. That is why this type of data structure is called static data structure. In linked list memory space allocated for the elements of the list can be extended at any time. That is why this type of data structure is called dynamic data structure.

A linked list is an ordered collection of finite homogeneous elements called nodes where the linear order is maintained by means of pointers. That is, each node is divided into two parts: the first part contains the information of the node and the second part contains the link to the next node.

| Information | Link to the next node |

**Figure:** structure of a node