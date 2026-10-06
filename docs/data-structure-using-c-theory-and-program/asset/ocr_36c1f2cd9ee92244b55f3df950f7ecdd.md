# Chapter 3 Linked List

```
node->next=NULL;
i=i+1;
printf(\
 Press 'E' key to exit and Press 'Y' key to continue");
ch=getchar ()
}
nvoid sort (struct node *next)
{
struct node *index1, *index2;
int temp;
for(index1=node; index1->next!=NULL;index1=index1->next)
{
for(index2=index1->next;index2!=NULL;index2=index2->next)
{
if(index1->info>index2->info)
{
temp=index1->info;
index1->info=index2->info;
index2->info=temp;
}
}
}
void display (struct node *next)
{
while(node!=NULL)
{
printf("%%d", node->info);
node=node->next;
}
}
```

# Output

Enter the value node: 30
Press 'E' key to exit and Press 'Y' key to continue: Y
ter the value node: 40
Press 'E' key to exit and Press 'Y' key to continue: Y