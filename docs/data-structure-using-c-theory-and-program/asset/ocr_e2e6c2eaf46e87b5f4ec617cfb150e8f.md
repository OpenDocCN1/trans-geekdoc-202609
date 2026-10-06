# Chapter 3 Linked List

+   9. repeat steps 10 while curr->link!=first
10. curr->curr->link
11. ptr->link=first
12. first=ptr
13. curr->link=first
14. stop

```
void insertatbeg()
{
    struct node *ptr;
ptr=(struct node *) malloc (sizeof(struct node));
if(ptr==NULL)
{
    printf("OVERFLOW\n");
    return;
}
    printf("Input New Node Information");
    scanf("%0d",&ptr->info);
    curr=first;
    while(curr->link!=NULL)
    {
        curr=curr->link;
    }
    ptr->link=first;
    first=ptr;
    }
}
```

# b. (ii) Insertion of a Node (At End)

![](bbox=[0.283, 0.752, 0.723, 0.812])

![](bbox=[0.233, 0.831, 0.778, 0.93])