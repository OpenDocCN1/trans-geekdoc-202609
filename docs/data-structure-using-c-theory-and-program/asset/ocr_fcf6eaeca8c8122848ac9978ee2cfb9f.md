# Drawback of queues: One major drawback of representing a queue using array is a fixed amount of storage remains allocated even when the structure is actually using small amount or possibly no storage at all.

# 2. Queue using linked list
To represent queue using linked list each node is divided into two parts

+   (i) Info: which holds the data element
(ii) Next: which holds the address of the next node

Apart from that we need two more variables
(i) Front: which holds the address of the first node
(ii) Rear: which holds the address of the last node

Under the linked list representation of queue two pointers named as front and rear are used. However a special attention is required when the last element is removed from a queue, in that case rear must also set to NULL.

![](bbox=[0.138, 0.393, 0.842, 0.443])

Front
Rear

The structure of a node will be as
struct node
{
int info;
struct node *next;
}
struct node *front, *rear;

# Program: write a program to implement a queue using linked list

```
#include<stdio.h>
#include<stdlib.h>
void insert();
void delete();
void display();
struct node
{
int info;
struct node *link;
}*rear=NULL,*front=NULL;
void main()
{
```