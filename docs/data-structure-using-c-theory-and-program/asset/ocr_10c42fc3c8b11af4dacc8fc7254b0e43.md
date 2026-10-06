```
exit(0);
}
create(node);
while (ch!='3')
{
  printf(\n 1. Search");
  printf(\
 2. Display");
  printf("\n 3. Exit");
  printf("\n Enter your choice");
  ch=getchar();
  switch(ch)
  {
    case '1':
      search(node);
      break;
    case '2':
      display(node);
      break;
    case '3':
      break;
    default:
      printf("\n Wrong Choice");
  }
}
void create (struct node * next)
{
  char ch;
  int i=1;
  printf("\n enter the value of %d node", i);
  scanf("%d",&node->info);
  node->next=NULL;
  i=i+1;
  printf(\n Press 'E' key to exit and Press 'Y' key to continue: ");
  ch=getchar (
  while (ch!='N')
```