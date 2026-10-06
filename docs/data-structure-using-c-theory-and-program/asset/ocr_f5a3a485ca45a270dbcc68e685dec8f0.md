```
{
int info;
struct node *next;
};
struct node *start;
void insert (struct node *);
void create (struct node*);
void display (struct node*);
void main ()
{
char ch='1';
struct node *next;
node=(struct node*)malloc(sizeof(struct node));
if(node==NULL)
{
printf("\n out of memory space\");
exit(0);
}
printf("\n Creation of a Linked List\n");
create (node);
while (ch!='3')
{
printf("\n 1. Insert at Beg\");
printf("\n 2. Display\");
printf("\n 3. Exit\");
printf("\n Enter your choice\");
ch=getchar();
witch(ch)
{
case '1':
insert(node);
node=start;
start=NULL;
break;
case '2':
display (node);
```