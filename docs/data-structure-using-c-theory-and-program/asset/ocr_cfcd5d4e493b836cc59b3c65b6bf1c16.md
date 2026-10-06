a good sequence of choices, your final state is a goal state; if you didn’t, isn’t. Conceptually, you start at the root of a tree; the tree probably has some good leaves and some bad leaves, it might be that the leaves are all good or bad. You want to get a good leaf. At each node, beginning with the root, you choose one of its children to move to, and you keep this until you get to a leaf.

+   - Branch and Bound: In a branch and bound algorithm a given sub-problem, which cannot be bounded, has to be divided into at least two new sub-problems. Branch and bound algorithms are methods for global optimization in non-convex problems.

# Analysis of algorithm

The algorithm can be traced by step-by-step instructions, reading the algorithm for logical correctness, and testing it on data using mathematical techniques. After designing an algorithm, it has to be checked and its correctness needs to be predicted; this is done by analysing the algorithm. thus, its analysis measures the efficiency of the algorithm. The efficiency of an algorithm can be checked by (i) correctness of an algorithm, (ii) implementation of an algorithm, (iii) simplicity of an algorithm (iv) execution time and memory requirements of an algorithm.

# Types of Analysis

**Best Case:** The best case complexity of the algorithm is the function defined by the minimum number of steps taken on any instance of n.

**Average Case:** The average case complexity of the algorithm is the function defined by an average number of steps taken on any instance of size n.

**Worst Case:** The worst case complexity of an algorithm is the function defined by the maximum number of steps taken on any instance of size n.

# 1.7 TIME-SPACE TRADE OFF

For many natural problems, such as sorting or matrix-multiplication, there are many choices of algorithms to use, some of which are extremely space-efficient and others of which are extremely time-efficient. This is an instance of a general phenomenon where one can save space by recomputing intermediate results. Research in time-space trade off lower bounds seeks to prove that, for certain problems, no algorithms exist that achieve small space and time simultaneously. In computer science, a space-time or time-memory trade off is a way of solving a problem or calculation in less time using more storage space (or memory), or by solving a problem in very little space by spending a long time. Most computers have a large amount of storage, but not infinite space. Also, most people are willing to wait a little while for a big calculation, but not forever. So if