# Chapter 3 Linked List

```
struct node *insertatbeg(struct node *start)
{
  struct node *newnode, *ptr;
  int num;
  printf("\n Enter the Data\");
  scanf("%%d", &num);
  newnode=(struct node*)malloc(sizeof(struct node));
  newnode->data=num;
  ptr=start;
  while(ptr->next!=start)
    ptr=ptr->next;
  newnode->prev=ptr;
  ptr->next=newnode;
  newnode->next=start;
  start->prev=newnode;
  start=newnode;
  return start;
}
```

# b. Insertion at End

![](bbox=[0.213, 0.549, 0.783, 0.626])

Figure Before Insertion at End

![](bbox=[0.197, 0.677, 0.802, 0.806])

Figure After Insertion at End (Say=50)

# Algorithm

Steps

+   1. start