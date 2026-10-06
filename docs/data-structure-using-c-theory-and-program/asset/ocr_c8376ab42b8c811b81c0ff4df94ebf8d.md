nodes adjacent to starting node. We maintain the status of visited node array so that no node can be traversed again.

Let us take a graph and apply BFS to it.

| Vertex | Adjacency List |
| --- | --- |
| A | B, C, D |
| B | D, E |
| C | D |
| D | E |
| E | |

Take the node A as the starting node and start the traversal of the given graph.

First we traverse node A, then we traverse all adjacent nodes to node A, i.e., B,C, D. Now we traverse all adjacent nodes to B, then all the adjacent nodes to D and E.

Now we traverse all nodes adjacent to C, then all the nodes adjacent to D. Now we traverse all nodes adjacent to D, then all the nodes E now the traversal is: A, B, C, D, E

This was the traversal when we take node A as the starting node.

# BFS through Queue

Take an array queue which will be used to keep the unvisited neighbours of the node. Take a Boolean array visited which will have value true if the node has been visited and will have value false if the node has not been visited.

Initially queue is empty and front = -1 and rear = -1
initially visited [i] = false where i=1 to n, n is total number of nodes.

# Procedure

+   1. Inserting node into the queue
2. Delete front element from the queue and insert all its unvisited neighbours into the queue at the end, and traverse them. Also make the value of visited array true for these nodes.
3. Repeat step 2 until the queue is empty.

Suppose the source vertex is A. Then following steps will illustrate the BFS
Step 1: Initially push A to the queue.

| 0 | 1 | 2 | 3 | 4 |
| --- | --- | --- | --- | --- |
| A | | | | |

Front = 0
Rear = 0