# 4.2. Trajectory Planning Algorithm for the Problem 2

Problem 2 has a constraint on the minimum turning radius. Therefore, we adopt an improved sparse A* algorithm, which is an effective method to avoid useless trajectory nodes in space and reduce the time to search for feasible successor nodes. Using trajectory constraints to search only the effective space reduces the search space and speeds up the search. So, for Problem 2, we propose a trajectory planning problem based on the improved sparse A* algorithm. First, we plan the division of space. Attention should be paid to reducing the number of divided cells as much as possible, thereby reducing the amount of calculation and improving the algorithm’s convergence speed, so that the algorithm can plan the feasible trajectory of a UAV in the shortest time. Then, there is the determination of the cost function.

If g(n) represents the actual cost of a UAV at the current trajectory node n in space:

$$g(n) = q_1 R_n(P) + q_2 S_n(P) \tag{28}$$

where R,S represents the flight cost of a UAV respectively, the horizontal and vertical error correction costs of a UAV, and q1,q2 each represent the weight coefficient of R,S.

$$R_n = \sum_{i=1}^{m} \eta_i \tag{29}$$

$$S_n = \sum_{i=1}^{m} (a_i + b_i) \eta_i \delta \tag{30}$$

where ηi represents the distance of an UAV’s i-th flight, ai represents an UAV’s i-th flight to the vertical correction point, bi represents an UAV’s i-th flight to the horizontal correction point, and δ indicates that the horizontal error and vertical error increase by δ units each time an UAV flies 1 metre.

Let h(n) represent the Euclidean distance from the current trajectory node to the target trajectory node B(xB, yB, zB), and q3 represent the weight coefficient of h(n), then:

$$h(n) = \sqrt{(x_n - x_B)^2 + (y_n - x_B)^2 + (z_n - x_B)^2} \tag{31}$$

Therefore, the improved cost function f(n) can be determined as:

$$f(n) = q_1 R_n(P) + q_2 S_n(P) + q_3 h(n) \tag{32}$$

A UAV’s online real-time trajectory planning task requires an improved sparse algorithm to complete the trajectory planning in a short time and a small memory space. The node can be expanded by an improved cost function, nodes can be expanded with an improved cost function, using two linked lists, of which the open table stores the nodes to be expanded, and the close table stores the nodes already. The specific algorithm flow is as follows and can be seen in

+   1. The search space is divided according to the requirements of the aircraft for the accuracy of the trajectory.
2. Put the starting point A into the open table, and the closing table is initially empty.
3. If the open table is empty, it means that the search failed, and the algorithm exited.
4. Remove the least costly trajectory node in the open table as the current trajectory node, and store the point in the closing table.
5. If the current node is midpoint B, the search is ended, and the algorithm exits successfully. Starting from point B and going back to point A, we get the optimal path from point A to point B. Otherwise, go to the next step.
6. The successor node of the node with the least expansion cost. Point the parent pointer of the succeeding node to the node with the least cost.