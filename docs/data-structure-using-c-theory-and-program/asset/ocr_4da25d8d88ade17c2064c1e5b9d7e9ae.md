end is calculated by the relation Front={(Front+1) % SIZE}. After locating the position of the new element to be inserted, compare it with front. If (rear==front), the queue is full and cannot be inserted any more. when front==-1 and rear==-1, circular queue is empty.

# Algorithm Insert an element in circular queue

Steps

+   1. start
2. check overflow condition
   if(front==0 && rear==max-1) || (front==rear+1) then
   write“OVERFLOW” and then
   stop
3. read data to insert
4. if(front==-1)
   front=0
   rear=0
5. if(rear==max-1) then
   rear=0
   else
   rear=rear+1
6. cq[rear]=data
7. stop

# Algorithm Delete an element in circular queue

Steps

+   1. start
2. check underflow condition
   if(front==-1) then
   write“UNDERFLOW” and then
   stop
3. if(front==rear) // circular queue has only one element
   cq[front]=0
   front=1
   rear==-1
4. if(front==max-1)
   front=0
   else