![](bbox=[0.18, 0.15, 0.8, 0.48])

# Figure 11. Trajectory planning path for the Problem 2.

Figure 11 shows that both the horizontal error correction point and the vertical error correction point are evenly distributed in the three-dimensional space. This question considers that when a UAV turns from the current trajectory node in the horizontal direction to the next trajectory node, due to the limitations of the UAV's own performance, it can only turn within a certain yaw angle range. Therefore, through the above algorithm, the feasible correction point is searched in turn. Connect these feasible correction points, that is, get a trajectory planning path, use this method to cycle back and forth, which constitutes the optimal trajectory length in Figure 11.

Under the constraint condition that a UAV is turning within a certain yaw angle, the position of the trajectory planning path and the number of times a UAV passes the correct area for correction can be determined before the correction of the vertical and horizontal errors, and a UAV starts from the starting point. The error correction point number and the trajectory planning result table of the error before correction are shown in Table 3.

# Table 3. Corrects result for Problem 2.

| The Number of the Correction Points | The Type of the Correction Points |
|---|---|
| 0 | The Starting Point |
| 346 | 1 |
| 200 | 0 |
| 294 | 0 |
| 136 | 1 |
| 108 | 1 |
| 74 | 0 |
| 462 | 1 |
| 543 | 0 |
| 369 | 1 |
| 457 | 0 |
| 388 | 1 |
| 436 | 0 |
| 612 | The Ending Point |