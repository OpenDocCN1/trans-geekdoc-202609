
(b) If graph G is undirected then the adjacency matrix of G will be symmetric.
That is $[a_{ij}] = [a_{ji}]$ for every $i$ and $j$.

## (ii) Incidence matrix

The incidence matrix consists of a row for every vertex and a column for every edge. The values of the matrix are -1, 0 or 1. The $k^{th}$ edge is $(v_i, v_j)$, the $k^{th}$ column has a value 1 in the $i^{th}$ row, -1 in the $j^{th}$ row and 0 otherwise. For example, let us consider the following graph.

![](img/3d5da05d64722faaa72fdc4daca105f9_318_0.png)

The adjacent matrix A of the above graph G is as follows:

```
A=\begin{pmatrix} v1 & v2 & v3 & v4 \\ 0 & 0 & 0 & 1 \\ 1 & 0 & 1 & 1 \\ 1 & 0 & 0 & 1 \\ 0 & 0 & 1 & 0 \end{pmatrix}
```

Consider the powers $A, A^2, A^3, \dots$ of the adjacency matrix A of a graph G.
Observe that $a_k(i,j) = a_{ij}$ gives the number of paths of length 1 from node $v_i$ to $v_j$. Let A be the adjacency matrix of a graph G. $a_k(i,j)$, the $ij$ entry in the matrix $A^k$, gives the number of paths of length $k$ from $v_i$ to $v_j$.

Consider the previous graph, whose adjacency matrix A is given above. The powers $A, A^2, A^3, \dots$ of the matrix A are as follows:

```
A^2=\begin{pmatrix} v1 & v2 & v3 & v4 \\ 1 & 0 & 1 & 1 \\ 0 & 0 & 1 & 2 \\ 1 & 0 & 1 & 1 \\ 0 & 0 & 1 & 0 \end{pmatrix}
```

```
A^3=\begin{pmatrix} v1 & v2 & v3 & v4 \\ 1 & 0 & 1 & 2 \\ 0 & 0 & 1 & 2 \\ 0 & 0 & 2 & 2 \\ 1 & 0 & 1 & 1 \\ 0 & 0 & 1 & 0 \end{pmatrix}
```

```
A^4=\begin{pmatrix} v1 & v2 & v3 & v4 \\ 1 & 0 & 2 & 2 \\ 0 & 0 & 1 & 2 \\ 0 & 0 & 2 & 2 \\ 1 & 0 & 1 & 1 \\ 0 & 0 & 1 & 0 \end{pmatrix}
```

## (iii) Path Matrix

Let G be a simple directed graph with $n$ vertices $v_1, v_2, \dots, v_n$. An $n \times n$ matrix $P=[P_{ij}]$ is defined as follows:

$P_{ij} = \begin{cases} 1 & \text{if there is a path from } v_i \text{ to } v_j \\ 0 & \text{otherwise} \end{cases}$

Suppose there is a path from $v_i$ to $v_j$, then there must be a simple path from $v_i$ to $v_j$ of length $m-1$ or less, or a cycle from $v_i$ to $v_j$ when $v_i = v_j$. The path matrix $P$ of a given G can be obtained from its adjacency matrix by following steps:

1. From the adjacency matrix A, we can determine whether an edge exists from one vertex to another.
2. Find $A^n$ for some integer $n$.
3. Add the matrices $A, A^2, A^3, \dots, A^n$.
4. Now path matrix $P$ can be obtained from $B^n$ as follows: $P_{ij}=1$ if and only if there is a non-zero element in the $i, j$ entry of the matrix $B^n$.

Since G has only $m$ nodes, such a simple path must have length $m-1$ or less, or a cycle must have length $m$ or less. This means there is a non-zero $ij$ entry in the matrix $B^m$.

Let A be the adjacency matrix and $P=[P_{ij}]$ be the path matrix of a graph G. Then $p_{ij}=1$ if and only if there is a non-zero number in the $ij$ entry of the matrix.

$B^m = A + A^2 + A^3 + \dots + A^m$

Consider the following graph with $m=4$ nodes. Adding the matrix $A, A^2, A^3, A^4$, we obtain the non-zero entries in $B^4$ and replacing them by 1, we obtain the path matrix $P$ of the graph G:

![](img/3d5da05d64722faaa72fdc4daca105f9_319_0.png)

```
$B^4=\begin{pmatrix} 1 & 0 & 2 & 3 \\ 5 & 0 & 6 & 5 \\ 3 & 0 & 3 & 5 \\ 2 & 0 & 3 & 3 \end{pmatrix}$
```

```
$P = \begin{pmatrix} v1 & v2 & v3 & v4 \\ 1 & 0 & 1 & 1 \\ 1 & 0 & 1 & 1 \\ 0 & 1 & 0 & 1 \\ 1 & 0 & 1 & 1 \end{pmatrix}
```

Examine the matrix P; we see that the node $v_2$ is not reachable from any of the nodes. Recall that a directed graph G is said to be strongly connected if for any pair of nodes u and v in G, there are both a path from u to v and v from v to u. Accordingly G is strongly connected if and only if the matrix P of G has no zero entries.

The adjacency matrix A and the path matrix P of a graph G may be viewed as logical Boolean matrices, where 0 represents false and 1 represents true. Thus, the logical operations of ^ (AND) and v (OR) may be applied to the entries of A and P. The values of ^ and v appear in the table:

| | 0 | 1 |
|---|---|---|
| ^ | 0 | 0 |
| v | 0 | 1 |

## Chapter 7 Graphs

(b) If graph G is undirected then the adjacency matrix of G will be symmetric.
That is $[a_{ij}] = [a_{ji}]$ for every $i$ and $j$.

## (ii) Incidence matrix

The incidence matrix consists of a row for every vertex and a column for every edge. The values of the matrix are -1, 0 or 1. The $k^{th}$ edge is $(v_i, v_j)$, the $k^{th}$ column has a value 1 in the $i^{th}$ row, -1 in the $j^{th}$ row and 0 otherwise. For example, let us consider the following graph.

![](img/3d5da05d64722faaa72fdc4daca105f9_318_0.png)

The adjacent matrix A of the above graph G is as follows:

```
A=\begin{pmatrix} v1 & v2 & v3 & v4 \\ 0 & 0 & 0 & 1 \\ 1 & 0 & 1 & 1 \\ 1 & 0 & 0 & 1 \\ 0 & 0 & 1 & 0 \end{pmatrix}
```

Consider the powers $A, A^2, A^3, \dots$ of the adjacency matrix A of a graph G.
Observe that $a_k(i,j) = a_{ij}$ gives the number of paths of length 1 from node $v_i$ to $v_j$. Let A be the adjacency matrix of a graph G. $a_k(i,j)$, the $ij$ entry in the matrix $A^k$, gives the number of paths of length $k$ from $v_i$ to $v_j$.

Consider the previous graph, whose adjacency matrix A is given above. The powers $A, A^2, A^3, \dots$ of the matrix A are as follows:

```
A^2=\begin{pmatrix} v1 & v2 & v3 & v4 \\ 1 & 0 & 1 & 1 \\ 0 & 0 & 1 & 2 \\ 1 & 0 & 1 & 1 \\ 0 & 0 & 1 & 0 \end{pmatrix}
```

```
A^3=\begin{pmatrix} v1 & v2 & v3 & v4 \\ 1 & 0 & 1 & 2 \\ 0 & 0 & 1 & 2 \\ 0 & 0 & 2 & 2 \\ 1 & 0 & 1 & 1 \\ 0 & 0 & 1 & 0 \end{pmatrix}
```

```
A^4=\begin{pmatrix} v1 & v2 & v3 & v4 \\ 1 & 0 & 2 & 2 \\ 0 & 0 & 1 & 2 \\ 0 & 0 & 2 & 2 \\ 1 & 0 & 1 & 1 \\ 0 & 0 & 1 & 0 \end{pmatrix}
```

## (iii) Path Matrix

Let G be a simple directed graph with $n$ vertices $v_1, v_2, \dots, v_n$. An $n \times n$ matrix $P=[P_{ij}]$ is defined as follows:

$P_{ij} = \begin{cases} 1 & \text{if there is a path from } v_i \text{ to } v_j \\ 0 & \text{otherwise} \end{cases}$

Suppose there is a path from $v_i$ to $v_j$, then there must be a simple path from $v_i$ to $v_j$ of length $m-1$ or less, or a cycle from $v_i$ to $v_j$ when $v_i = v_j$. The path matrix $P$ of a given G can be obtained from its adjacency matrix by following steps:

1. From the adjacency matrix A, we can determine whether an edge exists from one vertex to another.
2. Find $A^n$ for some integer $n$.
3. Add the matrices $A, A^2, A^3, \dots, A^n$.
4. Now path matrix $P$ can be obtained from $B^n$ as follows: $P_{ij}=1$ if and only if there is a non-zero element in the $i, j$ entry of the matrix $B^n$.

Since G has only $m$ nodes, such a simple path must have length $m-1$ or less, or a cycle must have length $m$ or less. This means there is a non-zero $ij$ entry in the matrix $B^m$.

Let A be the adjacency matrix and $P=[P_{ij}]$ be the path matrix of a graph G. Then $p_{ij}=1$ if and only if there is a non-zero number in the $ij$ entry of the matrix.

$B^m = A + A^2 + A^3 + \dots + A^m$

Consider the following graph with $m=4$ nodes. Adding the matrix $A, A^2, A^3, A^4$, we obtain the non-zero entries in $B^4$ and replacing them by 1, we obtain the path matrix $P$ of the graph G:

![](img/3d5da05d64722faaa72fdc4daca105f9_319_0.png)

```
$B^4=\begin{pmatrix} 1 & 0 & 2 & 3 \\ 5 & 0 & 6 & 5 \\ 3 & 0 & 3 & 5 \\ 2 & 0 & 3 & 3 \end{pmatrix}$
```

```
$P = \begin{pmatrix} v1 & v2 & v3 & v4 \\ 1 & 0 & 1 & 1 \\ 1 & 0 & 1 & 1 \\ 0 & 1 & 0 & 1 \\ 1 & 0 & 1 & 1 \end{pmatrix}
```

Examine the matrix P; we see that the node $v_2$ is not reachable from any of the nodes. Recall that a directed graph G is said to be strongly connected if for any pair of nodes u and v in G, there are both a path from u to v and v from v to u. Accordingly G is strongly connected if and only if the matrix P of G has no zero entries.

The adjacency matrix A and the path matrix P of a graph G may be viewed as logical Boolean matrices, where 0 represents false and 1 represents true. Thus, the logical operations of ^ (AND) and v (OR) may be applied to the entries of A and P. The values of ^ and v appear in the table:

| | 0 | 1 |
|---|---|---|
| ^ | 0 | 0 |
| v | 0 | 1 |

## 7.6 TRAVERSING A GRAPH

As we know that traversing is visiting each node in some systematic approach. Graph is represented by its nodes and edges. There are two graph traversal methods:

1. Breadth First Search (BFS) Using Queue
2. Depth First Search (DFS) Using Stack

## 1. Breadth first search using queue

This Graph traversal technique uses queue for traversing all the nodes. In this, first we take any node as starting node then we take all adjacent to starting node. We maintain the status of visited array so that no node can be traversed again.

Let us take a graph and apply BFS to it.

| Vertex | Adjacency List |
| --- | --- |
| A | B, C, D |
| B | D, E |
| C | D |
| D | E |
| E | |

