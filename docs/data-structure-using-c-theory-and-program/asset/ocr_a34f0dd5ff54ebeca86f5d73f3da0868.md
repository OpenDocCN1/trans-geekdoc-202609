```
{
  struct node *temp,*temp1,*var;
  temp=head;
  while(temp!=NULL)
  {
    temp1=var;
    var=temp;
    temp=temp->next;
    var->next=temp1;
  }
  head=var;
}
```

```
void display()
{
  struct node *var;
  var=head;
  printf("\nlist of elments \n");
  while(var!=NULL)
  {
    printf("%d-> %s", var->data);
    var=var->next;
  }
  printf("NULL");
}
```

```
int main()
{
  int i,value;
  char ch='y';
  head=NULL;
  printf("\n 1.) Insert node");
  printf("\n 2.) display the list");
  printf("\n 3.) reverse the nodes");
  printf("\n 4.) exit");
  while(ch=='y')
}
```