```
}
void create()
{
    front = rear = -1;
}
void insert(int data)
{
    if (rear >= MAX - 1)
    {
        printf("nQueue overflow no more elements can be inserted");
    }
    if ((front == -1) && (rear == -1))
    {
        front++;
        rear++;
        pri_que[rear] = data;
        return;
    }
    else
    {
        check(data);
        rear++;
    }
}
void check(int data)
{
    int i,j;
    for (i = 0; i <= rear; i++)
    {
        if (data >= pri_que[i])
        {
            for (j = rear + 1; j > i; j--)
            {
                pri_que[j] = pri_que[j - 1];
            }
            pri_que[i] = data;
            return;
        }
    }
}
```