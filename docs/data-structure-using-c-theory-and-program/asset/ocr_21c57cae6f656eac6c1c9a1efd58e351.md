# Data Structure Using C

```
printf("n Enter your choice");
ch=getchar();
switch(ch)
{
case '1':
insert(node);
break;
case '2':
display(node);
break;
case '3':
break;
default:
printf("n Wrong Choice");
}
```

```
void create (struct node * next)
{
char ch;
int i=1;
printf("\n enter the value of %%d node", i);
scaf("%d",&node->info);
node->next=NULL;
i=i+1;
printf(" Press 'E' key to exit and 'Y' key to continue: ");
ch=getchar();
while(ch!='N')
{
node->next=(struct node*)malloc(sizeof (struct node));
if(node->next==NULL)
{
printf("\n out of memory space");
exit(0);
}
node=node->next;
```