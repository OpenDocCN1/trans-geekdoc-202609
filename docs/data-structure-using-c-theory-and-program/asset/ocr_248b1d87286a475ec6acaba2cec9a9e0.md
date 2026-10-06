# Chapter 3 Linked List

125

+   2. Holds the address of the first node
3. Set node = start
4. Set temp = start
5. If node = NULL then
6. Write “UNDERFLOW” and
7. Exit
8. Repeat steps 9 and 10 while next [node] ≠ NULL
9. Set temp = node
10. Set node = next [node]
11. End of step 8 loop
12. Set next [temp] = NULL
13. Free the space associated with node
14. Stop

# Program: Delete a Node at the End of a Double Linked List

```
#include<stdio.h>
#include<stdlib.h>
struct dllnode
{
  int info;
  struct dllnode *prev;
  struct dllnode *next;
};
struct dllnode *start;
void create(struct dllnode *nvoid delete(struct dllnode *);
void display(struct dllnode *);
void main()
{
  struct dllnode *node;
  char ch='1';
  node=(struct dllnode*)malloc(sizeof(struct dllnode));
if(node==NULL)
{
  printf("\n out of memory");
  exit(0);
```