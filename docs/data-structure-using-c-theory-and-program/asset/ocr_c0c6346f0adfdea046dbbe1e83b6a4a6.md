5. Repeat steps 6 and 7

6. Process info [node] // apply process to info [node]

7. Set node = next [node] // move pointer to next node

8. Stop

# Program: Create a Single Linked List and Display all Nodes

```
#include<stdio.h>
#include<stdlib.h>
struct node
{
int info;
struct node *next;
};
void create (struct node*);
void display (struct node*);
void main ()
{
struct node *next;
node=(struct node*)malloc(sizeof(struct node));
if(node==NULL)
{
printf("\n out of memory space\");
exit(0);
}
create();
dplay();
}
void create (struct node * next)
{
char ch;
int i=1;
printf("\nenter the value of %d node\", i);
scanf("%d", &node->info);
ode->next=NULL;
i=i+1;
printf(\
 Press 'E' key to exit and Press 'Y' key to continue: \");
ch=getchar());
```