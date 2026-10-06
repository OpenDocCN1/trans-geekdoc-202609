# Data Structure C

+   2. if avail=NULL then
3. print message “OVERFLOW” and then
4. stop
5. ptr←avail
6. avail←leftptr
7. avail←rightptr
8. read info
9. ptr←leftptr (first)
10. rightptr←ptr
11. leftptr←ptr
12. rightptr←first
13. leftptr←ptr
14. stop

```
struct node *insertatend(struct node *start)
{
struct node *ptr, *newnode;
int num;
printf("\nEnter the Data");
scanf("%d", &num);
newnode=(struct node *)malloc(sizeof(struct node));
newnode->data=num;
ptr=start;
while(ptr->next!=start)
ptr=ptr->next;
ptr->next=newnode;
newnode->prev=ptr;
newnode->next=start;
start->prev=newnode;
return start;
}
```

# 2. Delete Operation

+   a. Deletion at Beg

![](bbox=[0.205, 0.866, 0.782, 0.936])