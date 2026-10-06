# Chapter 3 Linked List

```
scanf("%d", &node->info)
node->next=NULL;
i=i1;
printf("n Press 'E' key to exit and Press 'Y' key to continue");
ch=getch();
}
}
void merge (struct node node1*, struct node node2*, struct node node3*) {
{
node3->info=node1->info;
node3->next=NULL;
node1=node1->next;
while(node1!=NULL)
{
node3->next=(struct node*)malloc(sizeof(struct node));
if(node3->next==NULL)
{
printf("\n out of memory space");
exit(0);
}
node3=node3->next;
node3->info=node1->info;
node1=node1->next;
node3->next=NULL;
}
while(node2!=NULL)
{
node3->next=(struct node*)malloc(sizeof(struct node));
if(node3->next==NULL)
{
printf("\n out of memory space");
exit(0);
}
node3=node3->next;
node3->info=node2->info;
node2=node2->next;
```