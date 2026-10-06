
# Chapter 7 Graphs

Step 2: Remove the front element A from the queue by incrementing front = front + 1 and display it. Then push all the neighbouring vertices of A to the queue by incrementing rear = rear + 1.

| 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|--|
| | B | C | D | |

Front = 1 Rear = 3

# Traversed node = A

Step 3: Remove the front element B from the queue by incrementing front = front + 1 and display it. Then push all the neighbouring vertices of B to the queue by incrementing rear = rear + 1.

| 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|--|
| | C | D | E | |

Front = 2 Rear = 4

# Traversed node = A, B

Step 4: Remove the front element C from the queue by incrementing front = front + 1 and display it. Then push all the neighbouring vertices of C to the queue by incrementing rear = rear + 1, if it is not in queue, D is already in queue, ignore it.

| 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|--|
| | | D | E | |

Front = 3 Rear = 4

# Traversed node = A, B, C

Step 5: Again the process is repeated remove the front element D of the queue and add the neighbouring vertex if it is not present in the queue.

| 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|--|
| | | | | E | |

Front = 4 Rear = 4

# Traversed node = A, B, C, D

Step 6: Again the process is repeated until front > rear, remove the front element E of the queue and add the neighbouring vertex if it is present in the queue.

![](img/3d5da05d64722faaa72fdc4daca105f9_323_0.png)

# Traversed node = A, B, C, D, E

So, A, B, C, D, E is the BFS traversal of the graph.

Program: Write a Program to Implement Breadth First Search Traversal.

```c
#include<stdio.h>
#include<stdlib.h>
#include<math.h>
#include<string.h>
void input();
void output();
int db(int);
void bfs();
int d[10], a[10], jj, ii, ti, b1, fi, ri;
char ch[10];
struct b
{
    char node[10];
    struct b *left,*right;
} *temp,*root=NULL,*t,*q[25];
void main()
{
    input();
    output();
}
void input()
{
    int n,m,r,i,f;
    printf("Enter the no of depth:");
    scanf("%d",&d);
    n=pow(2,d+1)-1;
    for(i=1;i<=n;i++)
    {
        printf("Enter the %d node name:",i);
        scanf("%s",ch);
        temp=(struct b *)malloc(sizeof(struct b));
        strcpy(temp->node,ch);
        temp->left=NULL;
        temp->right=NULL;
        if(root==NULL)
        {
            root=temp;
        }
        else{
            t=root;
            r=db(i);
            for(f=1;f<r;f++)
            {
                if(a[f]==0)
                {
                    t=t->left;
                }
                else
                {
                    t=t->right;
                }
            }
            if(a[r]==0)
            {
                t->left=temp;
            }
            else
            {
                t->right=temp;
            }
        }
    }
}

void output()
{
    t=root;
    printf("\n Enter the name Goal:-\n");
    scanf("%s",ch);
    bfs(t);
}
int db(int n)
{
    int ji=0;
    while(n!=0)
    {
        a[ji++]=n%2;
        n=n/2;
    }
    for(ii=0,b1=ji-1;ii<b1;ii++,b1--)
    {
        t=a[ii];
        a[ii]=a[b1];
        a[b1]=ti;
    }
    ji--;
    return ji;
}

void bfs(struct b *t)
{
    int yes=0,index;
    fi=0;
    ri=1;
    q[fi]=t;
    printf("\n Breadth First search:\n");
    while(fi<ri)
    {
        t=q[fi++];
        printf("%s",t->node);
        if(strcmp(t->node,ch)==0)
        {
            yes=1;
            index=fi;
        }
        if(t->left!=NULL)
        {
            q[ri++]=t->left;
        }
        if(t->right!=NULL)
        {
            q[ri++]=t->right;
        }
        if(yes==1)
        printf("\n Goal State Are Present at Node %d",index);
        else
            printf("\n Goal State Not Present");
    }
}
# Output
Enter the no of depth:-3
Enter the 1 node name:-A
Enter the 2 node name:-B
Enter the 3 node name:-C
Enter the 4 node name:-D
Enter the 5 node name:-E
Enter the 6 node name:-F
Enter the 7 node name:-G
Enter the 8 node name:-H
Enter the 9 node name:-I
Enter the 10 node name:-J
Enter the 11 node name:-K
Enter the 12 node name:-L
Enter the 13 node name:-M
Enter the 14 node name:-N
Enter the 15 node name:-O
Breadth First search:-ABCDEFGHIJKLMNO
Goal State Are Present at Node 14

# 2. Depth first search using stack

The Depth First Search (DFS) suggests to search deeper in the graph. Given an graph G=(V, E) and a source vertex S, First visit the starting node, and then we travel through each node along a path, which is, visit a neighbour of S and again a neighbour of S and on. DFS also works on both directed as undirected graphs.

Depth first search technique uses stack to keep unvisited neighbours of the node. Another array VISITED, which will have TRUE if the node has been visited and will have FALSE if the node has not visited. Initially stack is empty and TOP = -1 where n is total number of nodes

Procedure
1. Push starting node into the stack.
2. Pop an element from the stack, if it has already traversed ignore it.
3. Now push all unvisited adjacent nodes of the popped element. Push the element if not already on stack.
4. Repeat steps 3 and 4 until stack is empty.

| Vertex | Adjacency List |
|---|---|
| A | B, C, D |
| B | D, E |
| C | D |
| D | |
| E | D |

![](img/3d5da05d64722faaa72fdc4daca105f9_328_0.png)
Step 1: Push node into stack
![](img/3d5da05d64722faaa72fdc4daca105f9_328_1.png)
Now, Top = 0 and STACK = A.
Step 2: POP node A from stack and traverse it So, Traversed node = A and VISITED [A] = TRUE Now, push all unvisited adjacent nodes B, C, D of the popped element on stack.

| D |
| C |
| B |

Now TOP = 2 and STACK = B, C, D
Traversal = A

**Step 3**: Pop the element D from the stack, and push all its unvisited adjacent nodes. There is no adjacent node. So, Traversed node = D VISITED [D] = TRUE

| C |
| B |

Now TOP = 1, STACK = B, C
Traversal = A, D

**Step 4**: POP the element C from the stack, traverse it and push all its unvisited adjacent nodes. Here node D is adjacent node of C but it is visited node. So, Traversed node = C VISITED [C] = TRUE

| B |

Now TOP = 0, STACK = B
Traversal = A, D, C

**Step 5**: POP the element B from the stack, traverse it and push all its unvisited adjacent nodes i.e., node E. Traversed node = B VISITED [B] = TRUE

| E |

Now TOP = 0, STACK = E
Traversal = A, D, C, B

**Step 6**: POP the element E from the stack, traverse it and push all its unvisited adjacent nodes. No node is here. Traversed node = E VISITED [E] = TRUE

| |

Now TOP = -1, STACK = EMPTY
Traversal = A, D, C, B, E

Since the stack is empty, so we will stop our process.

# Program: Write a Program to Implement Depth First Search Traversal.

```c
#include<conio.h>
#include<stdio.h>
#include<string.h>
#include<malloc.h>
#include<math.h>

void input();
void output();
int db(int);
void DFS(struct tree tree);
struct tree
{
    char node[10];
    struct tree *left,*right;
}temp,*root=NULL,t,*s[25];
int d,a[10], jj,ji,ti,b,top;
char ch[10];
void main()
{
    clrscr();
    input();
    output();
    getch();
}
void input()
{
    int n,m,r,i,f;
    printf("Enter the no of depth:");
    scanf("%d",&d);
    n=pow(2,d+1)-1;
    for(i=1;i<=n;i++)
    {
        printf("Enter the %d node name:",i);
        scanf("%s",ch);
        temp=(struct tree*)malloc(sizeof(struct tree));
        strcpy(temp->node,ch);
        temp->left=NULL;
        temp->right=NULL;
        if(root==NULL)
        {
            root=temp;
        }
        else
        {
            t=root;
            r=db(i);
            for(f=1;f<r;f++)
            {
                if(a[f]==0)
                {
                    t=t->left;
                }
                else
                {
                    t=t->right;
                }
            }
            if(a[r]==0)
            {
                t->left=temp;
            }
            else
            {
                t->right=temp;
            }
        }
    }
}
void output()
{
    t=root;
    printf("\n Enter the name Goal:-\n");
    scanf("%s",ch);
    DFS(t);
}
int db(int n)
{
    int ji=0;
    while(n!=0)
    {
        a[ji++]=n%2;
        n=n/2;
    }
    for(ii=0,b1=ji-1;ii<b1;ii++,b1--)
    {
        t=a[ii];
        a[ii]=a[b1];
        a[b1]=ti;
    }
    ji--;
    return ji;
}
void DFS(struct tree t)
{
    int yes=0,top=1;
    s[top]=t;
    printf("\n Depth First search:\n");
    while(top>0)
    {
        t=s[top];
        top--;
        printf("%s",t->node);
        if(strcmp(t->node,ch)==0)
        {
            yes=1;
        }
        if(t->left!=NULL)
        {
            s[++top]=t->left;
        }
        if(t->right!=NULL)
        {
            s[++top]=t->right;
        }
    }
    if(yes==1)
    printf("\n Goal State Are Present");
    else
        printf("\n Goal State Not Present");
}
```

# 7.7 SPanning TREE

A spanning tree is a subset of Graph G, which has all the vertices covered with minimum possible number of edges. Hence, a spanning tree does not have cycles and it cannot be disconnected.

By this definition we can draw a conclusion that every connected & undirected Graph G has at least one spanning tree. A disconnected graph does not have any spanning tree, as it cannot span to all its vertices.
