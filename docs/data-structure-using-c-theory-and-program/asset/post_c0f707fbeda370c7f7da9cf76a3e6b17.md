
# Chapter 7 Graphs

```c
if((origin == 0) && (destination == 0))
    break;
printf("Enter weight for this edge:");\nscanf("%d", &weight);
if(origin > n || destination > n || origin<=0 || destination<=0)
{
    printf("Invalid Edge");
    i--;
}
else
{
    insert_priority_queue(origin, destination, weight);
}
if(i < n-1) 
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
            root_n2 = node2;
            node2 = father[node];
        }
        printf("rootn1 = %d", root_n1);
        printf("rootn2 = %d", root_n2);
        if(root_n1!=root_n2)
        {
            insert_tree(temp->u, temp->v, temp->weight);
            weight_tree = weight_tree + temp->weight;
            father[root_n2] = root_n1;
        }
    }
}

void insert_tree(int i, int j, int weight)
{
    printf("This edge inserted in the spanning tree");
    count++;
    tree[count].u=i;
    tree[count].v=j;
    tree[count].weight=weight;
}
void insert_priority_queue(int i, int j, int weight)
{
    struct edge *temp, *q;
    temp = (struct edge*) malloc(sizeof(struct edge));
    temp->u=i;
    temp->v=j;
    temp->weight=weight;
    if(front==NULL || temp->weight < front->weight)
    {
        temp->link = front;
        front = temp;
    }
    else
        q=front;
        while(q->link!=NULL && q->link->weight<=temp->weight)
            q=q->link;
        temp->link = q->link;
        q->link = temp;
        if(q->link == NULL)    //edge to be added at the end
            temp->link = NULL;
    }
}
```

```c
struct edge *del_priority_queue()
{
    struct edge *temp;
    temp = front;
    printf("Edge processed is %d-%d %d\n", temp->u, temp->v, temp->weight);
    front = front->link;
    return temp;
}
```

# 7.10 PRIM'S ALGORITHM

In this, we start with any node and the other node in spanning tree on the basis of edge connecting to that node. Suppose, we start the node ‘N’ then we have a need to add all the connecting edges and which edge has minimum weight. Then, we will add that edge and node to the spanning tree. Suppose, if two nodes N1 and N2 are in spanning tree and both have edge connecting to an edge. Which minimum Prim's algorithm will be added in spanning tree.

The main idea of Prim's algorithm is similar to that of Dijkstra's algorithm for finding shortest path in a given graph. Prim's algorithm has the property that the edges in the set A from a single tree. We begin with vertex u in a given graph G = (V, E), defining the initial set of vertices. In each iteration, we choose a minimum weight edge (u, v) connecting a vertex v in the set A to outside set A. Then vertex u brought into A. This process is repeated until a spanning tree is formed. Kruskal's algorithm, here too, the important fact about MSTs is we always choose the smallest - weight edge joining a vertex to the one outside the set A.

MST-Prim (G, w, r)

1. for each u v in V[G]
2. key[u] = ∞
3. π[u] = NIL
4. key[r] = 0
5. Q = V[G]
6. while Q ≠ 0
7. do u = EXTRACT-MIN (Q)
8. for each v Adj[u]
9. if v ∈ Q and w (u, v) < key [v]
10. then π[u] = u
11. key[v] = w(u, v)

# Solution

# Step 1:

Suppose the starting vertex is V1
Edges, which have exactly one end belonging to the partial spanning tree
{(V1, V2),(V1, V3)}
The edge chosen based on the minimal spanning tree
(V1,V3)

![](img/3d5da05d64722faaa72fdc4daca105f9_344_0.png)

# Step 2: set of vertices in the minimal spanning tree (V1, V3)

Edges, which have exactly one end belonging to the partial spanning tree
{(V1, V2), (V2, V3),(V3, V4),(V3, V6)}
The edge chosen based on the minimal spanning tree
(V2, V3)

![](img/3d5da05d64722faaa72fdc4daca105f9_344_1.png)

# Step 3: set of vertices in the minimal spanning tree (V1, V2, V3)

Edges, which have exactly one end belonging to the partial minimal spanning tree
{(V3, V4), (V3, V6),(V2, V4),(V2, V5)}
The edge chosen based on the minimal spanning tree
(V2, V4)

![](img/3d5da05d64722faaa72fdc4daca105f9_344_2.png)

# Step 4: set of vertices in the minimal spanning tree (V1, V2, V3, V4)

Edges, which have exactly one end belonging to the partial spanning tree
{(V3, V6), (V2, V5),(V4, V7)}
The edge chosen based on the minimal spanning tree
(V3, V6)

![](img/3d5da05d64722faaa72fdc4daca105f9_344_3.png)

# Step 5: set of vertices in the minimal spanning tree (V1, V2, V3, V4, V6)

Edges, which have exactly one end belonging to the partial spanning tree
{(V2, V5), (V4, V7), (V5, V6)}
The edge chosen based on the minimal spanning tree
(V5, V6)

# Step 6: set of vertices in the minimal spanning tree (V1, V2, V3, V4, V5, V6)

Edges, which have exactly one end belonging to the partial spanning tree
{(V4, V7), (V6, V7)}
The edge chosen based on the minimal spanning tree
(V5, V7)
The edge that belong to minimum spanning tree
{(V1, V3), (V2, V3), (V2, V4), (V3, V6), (V4, V7), (V6, V7)}
Weight of minimum spanning tree 3+3+5+9+10
The total cost of a spanning tree is 4

# Program: Write a Program to Implement Spanning Tree for Prim's Algorithm.

```c
#include<stdio.h>
int a,b,v,n,i,j,ne=1;
int visited[10]={0};min,mincost=0,cost[10];
void main()
{
    printf("\n Enter the number of nodes:\n");
    scanf("%d",&n);
    printf("\n Enter adjacency matrix:\n");
    for(i=1;i<=n;i++)
        for(j=1;j<=n;j++)
        {
            scanf("%d",&cost[i][j]);
            if(cost[i][j]==0)
                cost[i][j]=99;
        }
    visited[1]=1;
    printf("\n");
}
```
![](img/3d5da05d64722faaa72fdc4daca105f9_345_0)

```c
while(ne<n)
{
    for(i=1,min=99;i<=n;i++)
        for(j=1;j<=n;j++)
            if(cost[i][j]<min)
                if(visited[i]!=0)
                {
                    min=cost[i][j];
                    a=i;
                    b=j;
                }
    if(visited[u]==0 || visited[v]==0)
    {
        printf("\n Edge %d:(%d,%d) cost:%d\n",ne++,a,b,min);
        mincost+=min;
        visited[b]=1;
    }
    cost[a][b]=99;
}
printf("\n Minimum cost=%d\n",mincost);
```

# Output
Enter the number of nodes:3
Enter adjacency matrix:
0 2 1
2 0 2
1 2 0
Edge 1:(1,3) cost:1
Edge 2:(1,2) cost:2
Minimum cost=3

# 7.11 SHORTEST PATH (DIJKSTRA’S ALGORITHM)

A path from source vertex s is shortest path t if there is path from s to t with lower weights. In a shortest paths problem, we are given weighted directed graph G = (V, E) with real valued weights. The weight of path p is the sum of the weights of its constituent edges.
w(p) = \sum_{i=1}^{k} w(V_{i}, V_{i+1})
We define the shortest path from u to v δ(u,v) = min w(p): u→v

# Dijkstra's algorithm

Dijkstra's algorithm, named after Edsger Dijkstra, is a greedy algorithm that solves the source shortest path problem for directed graph G=(V,E) with non-negative edge weights. Dijkstra's algorithm maintains a set S of vertices whose final path weights from source have already been determined. Then, for all v-S we have d[v] = ∞. The algorithm repeatedly selects the vertex u-S with the minimum weight, insert u S, and relaxes all edges leaving u. We maintain a priority queue Q that contains all the vertices V-S, keyed by their d values.

1. INITIALIZE - SINGLE SOURCE (G, s)
2. S = ∅
3. Q = V[G]
4. While Q ≠ 0
5. du = EXTRACT-MIN (Q)
6. S = S ∪ {u}
7. for each vertex Adj[u]
8. do RELAX (u, v, w)

![](img/3d5da05d64722faaa72fdc4daca105f9_347_0.png)

The procedure is as:

- Initially make source permanent and make it the current working node. All other nodes are temporary.
- Examine all the temporary neighbours of the current working node and after checking the condition for minimum weight, relabel the required nodes.
- From all the temporary nodes, find out the node which has minimum value of distance, make this node permanent and now is our current working node.
- Repeat steps 2 and 3 until destination node is made permanent. Suppose the source node is V1

V1 is the current working node.

| Node | Destination | Precedence | Status |
| V1 | 0 | 0 | Permanent |
| V2 | ∞ | 0 | Temporary |
| V3 | ∞ | 0 | Temporary |
| V4 | ∞ | 0 | Temporary |
| V5 | ∞ | 0 | Temporary |
| V6 | ∞ | 0 | Temporary |
| V7 | ∞ | 0 | Temporary |
| V8 | ∞ | 0 | Temporary |

![](img/3d5da05d64722faaa72fdc4daca105f9_348_0.png)

Now we will check the adjacent nodes of V1, which are temporary also.
Here,V2,V3,V4 are adjacent to V1 and are temporary.
V2.distance > V1.distance + distance (V1,V2) ∞ > 0 + 8 relabel V2
V3.distance > V1.distance + distance (V1,V3) ∞ > 0 + 2 relabel V3
V4.distance > V1.distance + distance (V1,V4) ∞ > 0 + 7 relabel V4
Now we will change the precedence and distance of V2, V3, V4

| Node | Destination | Precedence | Status |
| V1 | 0 | 0 | Permanent |
| V2 | 8 | V1 | Temporary |
| V3 | 2 | V1 | Temporary |
| V4 | 7 | V1 | Temporary |
