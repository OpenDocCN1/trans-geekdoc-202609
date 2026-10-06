```
if(front==-1)
{
    front=rear=0;
}
else
{
    if(rear==max-1)
    {
        rear=0;
    }
    else
    {
        rear++;
    }
    printf("\nenter:\n");
scanf("%d",&x);
q[rear]=x;
printf("%d successfully inserted\n",x);
return;
}
void dequeue()
{
    int y;
    if(front==-1)
    {
        printf("q is underflow\n");return;
    }
    y=q[front];
    if(front==rear)
    {
        front=rear=-1;
    }
else
{
    if(front==max-1)
```