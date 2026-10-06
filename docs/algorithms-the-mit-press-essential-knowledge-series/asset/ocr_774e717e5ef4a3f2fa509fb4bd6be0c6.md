From node F we check whether we should update our estimate for its neighbor, node E. The current path to E has a length of 3, while the path through F would have a cost of 10. We let E remain unchanged. Visiting F did not make any difference, but we could not have have known that beforehand. As we have visited all nodes, the algorithm finishes.

![](bbox=[0.135, 0.319, 0.715, 0.638])

When we were going through the algorithm, we were recording path lengths and the predecessor of each node along the shortest path. We did that so that if after finishing the algorithm we want to find the shortest path from A to any other node in the graph—for example, F—we start from the end and make our way to the start. We read