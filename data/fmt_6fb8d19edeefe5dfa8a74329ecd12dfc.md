
## 7.7 生成树

生成树是图 `G` 的一个子集，它以可能的边数覆盖所有顶点。因此，生成树没有环，且它不是连通的。

通过这个定义，我们可以得出结论：每个连通的无向图 `G` 至少有一棵生成树。不连通图没有生成树，因为它无法跨越所有顶点。

### 图 G

![](img/3d5da05d64722faaa72fdc4daca105f9_334_0.png)

我们找到了一个完全图的生成树。一个完全无向图最多可以有 `$n^{n-2}$` 棵生成树，其中 `$n$` 是节点数。在给出的示例中，`$n$` 为 3，因此有 `$3^{3-2} = 3$` 棵可能的生成树。

### 生成树的般属性

我们现在理解了一个图可以有多棵生成树。以下是给定连通图 `G` 的生成树的几个属性：

- 连通图 `G` 可以有多棵生成树。
- 图 `G` 的所有可能的生成树具有相同数量的边和顶点。
- 生成树不包含任何环路（回路）。
- 从生成树中删除一条边将使图变得不连通，即生成树是最小连通的。
- 在生成树中添加一条边将创建一个电路或环路，即生成树是极大无环的。

### 生成树的数学属性

- 生成树有 `$n-1$` 条边，其中 `$n$` 是节点（顶点）的数量。
- 从完全图中删除最多 `$e-n+1$` 条边，我们可以构造出一棵生成树。
- 完全图最多有 `$n^{n-2}$` 棵生成树。因此，我们可以得出：生成树是连通图的子集，而不连通图没有生成树。

### 生成树的应用

生成树基本上用于找到连接图中所有节点的最小路径。生成树的常见应用包括：

- 民用网络规划
- 计算机网络路由协议
- 聚类分析

让我们通过一个小例子来理解。考虑将城市网络作为一个巨大的图，现在计划部署电话线，以便用最少的线路连接所有节点。这就是生成树大显用场。

## 7.8 最小生成树 MST

在加权图中，最小生成树是与图中所有其他生成树相比权重最小的生成树。在现实世界中，这种权重可以被测量为距离、拥堵、交通负载或分配给边的任意值。

### 最小生成树算法

我们在这里学习了两种最重要的生成树算法：

- 克鲁斯尔算法 `Kruskal’s Algorithm`
- 普里姆算法 `Prim’s Algorithm`

两者都是贪心算法。

## 7.9 克鲁斯尔算法

该算法创建一个树的森林。初始时森林由 `$n$` 棵单节点树组成且没有边。也就是说，在方法开始阶段，我们为图的所有节点取 `$n$` 棵不同的树。在每一步中，我们添加一条边，将两个树连接在一起。

1. 初始为图中的每个节点构建一棵独立的树。
2. 将边放在优先级队列中，我们按从小到大的顺序取边。我们可以使用堆作为优先级队列。
3. 直到我们添加了 `$n-1$` 条边为止。
   (a) 从队列中提取最便宜的边。
   (b) 如果它形成环，则拒绝它；否则，将其添加到森林中。
4. 每当我们插入一条边时，两棵树就会合并，因此最后将只有一棵。

在此方法中，我们首先从最小边开始逐个检查所有的边。为了决定是否将选定的边包含在生成树中，我们将检查该边的两个节点。如果两个节点属于同一棵树，则我们不会将该边包含在生成树中，因为这两个节点已经在同一棵树中连通了，添加这些边会导致环路。因此，只有当节点位于不同的树时，我们才会向生成树中插入边。

现在，我们将查看两个节点是否在同一棵树中。为此，我们需要一个并查 `UNION-FIND` 结构。

为了理解并查结构，我们需要查看一个集合的划分。

- (a) 集合中的每个元素属于划分中的一个集合。
- (b) 集合中没有元素属于超过一个子集。
- (c) 集合中的每个元素属于划分中的且仅一个集合。

集合的划分可以被看作等价类的集合。划分的每个子集包含一组等价元素。对于每个子集，我们指定一个元素作为该子集的代表。然而，子集中的每个元素都是等价的，并由代表元素表示。当我们向子集中添加元素时，我们让所有元素指向该代表元素。初始时，每个节点都是自己的代表。当初始的节点对被连接形成一棵树时，其中一个节点的代表指针将指向另一个，后者成为该树的代表。随着树的增长，其中一棵的代表指针被设置为另一棵的任意元素。令 `$x$` 表示一个对象，我们希望支持以下操作。

1. `MAKE-SET(x)` 创建一个新的集合，其唯一成员由 `$x$` 指。
2. `FIND-SET(x)` 返回包含 `$x$` 的集合的代表的指针。
3. `UNION(x, y)` 将包含 `$x$` 和 `$y$` 的动态集合（假设为 `$S_x$` 和 `$S_y$`）合并为一个新集合。该该结果集合的代表是 `$S_x \cup S_y$` 中的某个成员。由于我们需要集合中的集合是互斥的，我们从集合中“销毁” `$S_x$` 和 `$S_y$`。

```
MST-KRUSKAL(G, W)

1. A = ∅

2. 对于 G 中的每个顶点 v
   执行 MAKE-SET(v)

3. 按权重递增排序 E 中的边。

4. 按递增顺序遍历 E 中的每条边 (u,v)。
   如果 FIND-SET(u) ≠ FIND-SET(v)
   则 A = A U {u, v}
   UNION(u, v)

5. 返回 A。
```

### 考虑一个图

![](img/3d5da05d64722faaa72fdc4daca105f9_337_0)

| 边 | 权重 |
|---|---|
| (1,3) | 3 |
| (3,2) | 3 |
| (2,1) | 4 |
| (2,4) | 5 |
| (4,3) | 8 |
| (3,6) | 9 |
| (5,7) | 10 |
| (6,4) | 11 |
| (7,4) | 12 |
| (4,5) | 14 |

生成树算法：

![](img/3d5da05d64722faaa72fdc4daca105f9_337_1)
第 1 步：初始

![](img/3d5da05d64722faaa72fdc4daca105f9_337_2)
第 2 步：

![](img/3d5da05d64722faaa72fdc4daca105f9_338_0)
第 3 步：

![](img/3d5da05d64722faaa72fdc4daca105f9_338_1)
第 4 步：

![](img/3d5da05d64722faaa72fdc4daca105f9_338_2)
第 5 步：

第 6 步：

第 7 步：

第 8 步：

第 9 步：

第 10 步：

第 11 步：

生成树的边：
`{(1,3), (3,2), (2,4), (3,6), (5,7), (6,4)}`

权重：

`3+3+5+9+10+11 = 41`

使用 C 语言通过克鲁斯尔算法实现最小生成树的程序：

```c
#include<stdio.h>
#define MAX 20
struct edge
{
int u, v, weight;
struct edge *link;
}*front = NULL
int father [MAX] //存储每个节点的父节点
struct edge tree[MAX] //包含生成树的边
int n; //图中节点总数
int weight_tree = 0 //生成树的权重
int count = 0 //生成在树中的边数
void make_tree();
void insert_tree(int i, j, int weight);
void insert_priority_queue(int i, j, int weight);
struct edge *del_priority_queue();
main()
{
int i;
create_graph();
make_tree();
printf("包含在生成树中的边有：");
for(i=0;i<=count;i++)
{
  printf("%d-%d->", tree[i].u);
  printf("%d-%d->", tree[i].v);
}
printf("这条最小生成树的权重为:%d", weight_tree);
create_graph()
{
int i, weight, maxedge, origin, destination;
printf("输入节点数量:");
canf("%d", &n);
maxedge = n*(n-1)/2;
for(i=1;i<=maxedge;i++)
{
  printf("输入边 %d(0 0 退出):.", i);
  canf("%d %d", &origin, &destination);
}
```

# 第 7 章 图

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

## 7.10 Prim 算法

在该算法中，我们从任意节点开始，并根据连接到该节点的边确定生成树中的另一个节点。假设我们从节点‘N’开始，我们需要添加所有连接的边，并确定哪条边的权重最小。然后，我们将该边和节点加入生成树中。假设两个节点 N1 和 N2 已经在生成树中，且它们都连接到某条边。那么 Prim 算法将选择哪条边加入生成树。

Prim 算法的核心思想与用于在图中寻找最短路径的 Dijkstra 算法相似。Prim 算法具有集合 A 中的边构成一棵单一树的性质。我们从给定图 G = (V, E) 中的顶点 u 开始，定义初始顶点集合。在每次迭代中，我们选择一条权重最小的边 (u, v)，它连接集合 A 中的顶点 v 和 A 之外的顶点。然后将顶点 u 引入集合 A。重复此过程，直到形成生成树。在 Kruskal 算法中，关于最小生成树（MST）的一个重要事实同样是：我们总是选择一条连接顶点与集合 A 之外顶点的最小权重边。

```
MST-Prim (G, w, r)

1. 对于 V[G] 中的每个 u v
2. key[u] = ∞
3. π[u] = NIL
4. key[r] = 0
5. Q = V[G]
6. while Q ≠ 0
7. 执行 u = EXTRACT-MIN (Q)
8. 对于 Adj[u] 中的每个 v
9. 如果 v ∈ Q 且 w (u, v) < key [v]
10. 则 π[u] = u
11. key[v] = w(u, v)
```

### 解决方案

### 步骤 1：

假设起始顶点为 V1
好有一个端属于部分生成树的边
`{(V1, V2),(V1, V3)}`
根据最小生成树选择的边
`(V1,V3)`

![](img/3d5da05d64722faaa72fdc4daca105f9_344_0.png)

# 步骤 2：最小生成树中的顶点集合 (V1, V3)

好有一个端属于部分生成树的边
`{(V1, V2), (V2, V3),(V3, V4),(V3, V6)}`
根据最小生成树选择的边
`(V2, V3)`

![](img/3d5da05d64722faaa72fdc4daca105f9_344_1.png)

# 步骤 3：最小生成树中的顶点集合 (V1, V2, V3)

好有一个端属于部分生成树的边
`{(V3, V4), (V3, V6),(V2, V4),(V2, V5)}`
根据最小生成树选择的边
`(V2, V4)`

![](img/3d5da05d64722faaa72fdc4daca105f9_344_2.png)

# 步骤 4：最小生成树中的顶点集合 (V1, V2, V3, V4)

好有一个端属于部分生成树的边
`{(V3, V6), (V2, V5),(V4, V7)}`
根据最小生成树选择的边
`(V3, V6)`

![](img/3d5da05d64722faaa72fdc4daca105f9_344_3.png)

# 步骤 5：最小生成树中的顶点集合 (V1, V2, V3, V4, V6)

好有一个端属于部分生成树的边
`{(V2, V5), (V4, V7), (V5, V6)}`
根据最小生成树选择的边
`(V5, V6)`

# 步骤 6：最小生成树中的顶点集合 (V1, V2, V3, V4, V5, V6)

好有一个端属于部分生成树的边
`{(V4, V7), (V6, V7)}`
属于最小生成树的边
`{(V1, V3), (V2, V3), (V2, V4), (V3, V6), (V4, V7)}`
最小生成树的权重为 3+3+5+9
生成树的总代价为 4

# 程序：编写实现 Prim 算法生成树的程序。

```c
#include<stdio.h>
int a,b,v,n,i,j,ne=1;
int visited[10]={0};min,mincost=0,cost[10];
void main()
{
    printf("\n 输入节点数量:\n");
    scanf("%d",&n);
    printf("\n 输入邻接矩阵:\n");
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
```
