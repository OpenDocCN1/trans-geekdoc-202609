# Chapter 7 Graphs

```
if((origin == 0) && (destination ==0))
break;
printf("Enter weight for this edge:");\ncanf("%d", &weight);
if(origin > n || destination > n || origin<=0 || destination<=0)
{
    printf("Invalid Edge");
    i--;
}
else
{
    insert_priority_queue(origin, destination, weight);
}
(i < n-1)
{
    printf("Spanning tree is not possible");
    exit(1);
}

void make_tree()
{
    struct edge *temp;
    int node1, node2, root_n1, root_n2;
    while(count < n-1) //loop till n-1 edges included in the tree
    {
        temp = del_priority_queue();
        node1 = temp->u;
        node2 = temp->v;
        printf("n%d", node1);
        printf("n2 %d", node2);
        while(node1 > 0)
        {
            root_n1 = node1;
            node1 = father[node];
        }
        while(node2 > 0)
        {
```