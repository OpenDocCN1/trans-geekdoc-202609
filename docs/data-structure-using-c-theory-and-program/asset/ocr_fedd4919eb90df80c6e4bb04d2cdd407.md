# Chapter 7 Graphs 321

+   * Computer Network Routing Protocol
* Cluster Analysis

Let's understand this by a small example. Consider city network as a huge graph and now plan to deploy telephone lines such as a minimum lines we can connect to all nodes. This is where spanning tree comes in the picture.

# 7.8 MINIMUM SPANNING TREE (MST)

In a weighted graph, a minimum spanning tree is a spanning tree that has minimum weight that all other spanning trees of the same graph. In real world situations, this weight can be measured as distance, congestion, traffic load or any arbitrary value denoted to the edges.

# Minimum Spanning-Tree Algorithm

We learn about two most important spanning tree algorithms here –

+   * Kuskal’s Algorithm
* Prim’s Algorithm

Both are greedy algorithms.

# 7.9 KRUKSHAL'S ALGORITHM

This algorithm creates a forest of trees. Initially the forest consists of n single node trees and no edges. That is, in the method initially we take n distinct trees for all nodes of the graph. At each step, we add one edge, so that it joins two together.

+   1. Initially construct a separate tree for each node in a graph.
2. Edges are placed in a priority queue, we take edges in ascending order. We can use a heap for the priority queue.
3. Until we have added n-1 edges.
  (a) Extract the cheapest edge from the queue.
  (b) If it forms a cycle, reject it
    else
    add to the forest.
4. Whenever we insert an edge, two trees will be joined, so that at the end, there will be only one.
In this method, first we examine all the edges one-by-one starting from the smallest edge. To decide whether the selected edge should be included in the spanning tree or not, we will examine the two nodes connecting the edge. If the two nodes belong to the same tree then we will not include the edge in