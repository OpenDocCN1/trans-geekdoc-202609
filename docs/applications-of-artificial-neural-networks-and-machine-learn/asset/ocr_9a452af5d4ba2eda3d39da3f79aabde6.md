# 14.5.2 Example

For a particular graph, first two pseudo-peripheral nodes are selected using the method outlined is Sect. 4.1, and designated by s and e. Then using shortest route trees rooted from s and e, the distance of each node from these two nodes are calculated. These distances are shown by d(s, i) and d(e, i), respectively. At this stage the degree of each node i is also calculated and shown by deg(i).

As an example, consider the graph shown in Fig. 14.3a. Sloan’s algorithm leads to the numbering as shown in Fig. 14.3b. For this graph s = 1 and e = 20 are selected, and for a typical node i = 9, the above defined values are as d(s, 9) = 3, d(e, 9) = 4 and deg(9) = 4.

Similar to Sloan’s method, the states of a typical node i in different stages of the labeling, and the assigned numbers s(i) are as follows:

+   (1) For post-active case s(i) = 1
+   (2) For active case s(i) = 0
+   (3) For pre-active case s(i) = -1
+   (4) For non-active case s(i) = -2.

The number of nodes adjacent to the node i in the status of active is shown by nact(i), and the number of nodes adjacent to i in the status of pre-active is designated by npre(i).

For the graph of Fig. 14.3b, after labeling the nodes 1 and 2, these nodes will be in the state of post-active, and s(i) = 1. The nodes 3 and 4 have active status and s(i) = 0; the nodes 5 and 9 are in the state of pre-active and s(i) = -1; the rest of the nodes have non-active status and s(i) = -2. In this example, for the node 9, nact(9) = 1 and npre(9) = 1.

Considering the above definitions, for each node i, the neural network has six input neurons. Selecting the starting node as assigning the label 1 to this node, the numbering starts. At each consequent step, after updating the status of the nodes, the input is given to the net and the output P(i) as the priority of the node i is obtained for all the candidate nodes. Comparison of the priority numbers results in the node with highest priority to receive the next label.

![](bbox=[0.12, 0.69, 0.35, 0.81])

![](bbox=[0.38, 0.69, 0.6, 0.81])

![](bbox=[0.65, 0.69, 0.88, 0.81])

Fig. 14.3 A simple example