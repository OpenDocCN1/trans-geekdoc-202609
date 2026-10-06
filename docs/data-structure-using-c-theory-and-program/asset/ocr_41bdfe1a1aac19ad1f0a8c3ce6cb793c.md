# Chapter 3 Linked List

```
while(curr->link!=first)
{
ptr=curr;
curr=curr->link;
}
ptr->link=first;
free(ptr);
{
```

# Program: Implement Circular Linked List

```
#include<stdio.h>
#include<stdlib.h>
typef struct Node
{
int data;
struct Node *next;
}node;
void insert(node *pointer, int data)
{
node *start = pointer;
while(pointer->next!=start)
{
pointer = pointer -> next;
}
pointer->next = (node *)malloc(sizeof(node));
pointer = pointer->next;
pointer->data = data;
pointer->next = start;
{
```

```
int find(node *pointer, int key)
{
node *start = pointer;
pointer = pointer -> next;
while(pointer!=start)
{
if(pointer->data == key
```