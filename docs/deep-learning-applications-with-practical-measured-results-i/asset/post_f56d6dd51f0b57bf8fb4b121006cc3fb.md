
![](img/8b41ef3997625b78ba4cb189dbc5f7b9_100_0.png)

Figure 11. Trajectory planning path for the Problem 2.

Figure 11 shows that both the horizontal error correction point and the vertical error correction point are evenly distributed in the three-dimensional space. This question considers that when a UAV turns from the current trajectory node in the horizontal direction to the next trajectory node, due to the limitations of the UAV's own performance, it can only turn within a certain yaw angle range. Therefore, through the above algorithm, the feasible correction point is searched in turn. Connect these feasible correction points, that is, get a trajectory planning path, use this method to cycle back and forth, which constitutes the optimal trajectory length in Figure 11.

Under the constraint condition that a UAV is turning within a certain yaw angle, the position of the trajectory planning path and the number of times a UAV passes the correct area for correction can be determined before the correction of the vertical and horizontal errors, and a UAV starts from the starting point. The error correction point number and the trajectory planning result table of the error before correction are shown in Table 3.

Table 3. Correction result for Problem 2.

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

Obtaining the optimal trajectory length from starting point to ending point is 14957.842315 m. From the table, the number of times of correction of the correction area is calculated 12 times, and the error correction point number passing through the starting point from the starting point is obtained.

## 5. Performance Comparison of the Proposed Algorithm with Traditional Swarm Intelligence Algorithm

### 5.1. For the Problem 1

For the data set, we compare the proposed improved GA algorithm with the traditional GA algorithm in trajectory planning. Figure 12 shows the fitness change of traditional GA algorithm:

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_101_0.png)

Figure 12. Fitness curve of traditional GA algorithm for the Problem 1.

Figure 13 shows the fitness change of the proposed improved GA algorithm:

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_101_1.png)

Figure 13. Fitness curve of the proposed improved GA algorithm for the Problem 1.

In order to compare the performance of the two algorithms more clearly, draw the fitness curves of Figures 12 and 13 into a unified coordinate system, as shown in Figure 14:

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_102_0.png)

Figure 14. Two algorithms for fitness.

It can be seen from Figure 14 that: (1) the proposed improved GA algorithm converges significantly faster than the traditional GA algorithm, (2) the proposed improved GA algorithm has a lower overall cost for the optimal trajectory search, (3) during the search of the proposed improved GA algorithm, the shock is small. Therefore, the proposed improved GA algorithm in the paper is significantly better than the traditional GA algorithm.

### 5.2. For the Problem 2

Experiments were performed using the basic A* algorithm and the improved A* algorithm, and the superiority of the algorithm was verified by comparing the path length of the trajectory planning and the number of correction points passed. Using the data set, the two weight coefficients q1, q2 and q3 of Formula (32) are set, respectively, as shown in Table 4.

Table 4. The weight coefficient of the improved cost function f(n).

| Number | q1 | q2 | q3 |
|---|---|---|---|
| 1 | 0.3 | 0.2 | 0.5 |
| 2 | 0.3 | 0.5 | 0.2 |

In the course of trajectory selection, the smaller the value of the cost function, the better the trajectory. Table 5 compares the experimental performance of the proposed improved sparse A* algorithm and the basic A* algorithm in the same environment.

Table 5. Performance comparison of A* algorithm and the proposed improved sparse A* algorithm.

| Number | Algorithm | Number of Correction Points Passed | Trajectory Length |
|---|---|---|---|
| 1 | Before improvement | 31 | 35,436.632176 |
| 1 | After improvement | 12 | 14,957.842315 |
| 2 | Before improvement | 39 | 41,258.581392 |
| 2 | After improvement | 15 | 19,513.452647 |

In Table 5, before improvement means that the basic A* algorithm, and after improvement means that the proposed improved sparse A* algorithm in this paper is used. Numbers 1 and 2 represent the weight coefficients of numbers 1 and 2 in Table 4. It can be seen from Table 5 that the larger q2 is, the larger correction points are passed, and the larger q3 is, the shorter the trajectory length is. Therefore, the values of these weighting factors can be adjusted from different needs. Furthermore, it can be seen that the performance of the improved sparse A* algorithm is significantly better than the basic A* algorithm.

## 6. Conclusions

The proposed method allows for multiple constraints optimal trajectory planning using the improved genetic algorithm (GA) and A* algorithm. The conclusions of this research work are: (1) The numerical results of the experiment proved that the improved genetic algorithm (GA) and A* algorithm are good for optimal trajectory planning. (2) All essential constraints like the correction and turning radius of a UAV are satisfied with all solutions obtained from the trajectory planning algorithm.

Future work should take into account more complex and realistic constraints, such as threats to the ground or in the air, the avoidance of obstacles, and other constraints of the UAV itself (such as its own battery life), improve the algorithm optimization model and objective functions (such as considers flight time [28]), and ensure that UAVs are able to adapt to more complex environments.

Author Contributions: Optimization problem software development, H.Z.; supervision, H.-L.X.; data curation, N.-D.T. and L.C.; resources, Y.L.; writing, H.Z. All authors have read and agreed to the published version of the manuscript.

Funding: This research was funded by the Key Projects of Natural Science Research of Universities in Anhui of China (KJ2019A0864), and by the Chongqing Technology Innovation and Application Development Project (cstc2019jsx-ksbx0103), and by the Fundamental Research Funds for the Central Universities under Project (SWU119904).

Conflicts of Interest: The authors declare no conflict of interest. The funders had no role in the design of the study; in the collection, analyses, or interpretation of data; in the writing of the manuscript, or in the decision to publish the results.

## References

1. Zhao, S.Y.; Hu, Z.Y.; Chen, B.M.; Lee, T.H. A Robust Real-Time Vision System for Autonomous Cargo Transfer by an Unmanned Helicopter. IEEE Trans. Ind. Electron. 2015, 62, 1210–1218. [CrossRef]
2. Shen, Y.F.; Rahman, Z.; Krusienski, D.; Li, J. A vision-based automatic safe landing-site detection system. IEEE Trans. Aerosp. Electron. Syst. 2013, 49, 294–311. [CrossRef]
3. Huh, S.; Cho, S.; Jung, Y.; Shim, D.H. Vision-based sense-and-avoid framework for unmanned aerial vehicles. IEEE Trans. Aerosp. Electron. Syst. 2015, 51, 3427–3439. [CrossRef]
4. ElMikatty, M.; Stathaki, T. Car Detection in Aerial Images of Dense Urban Areas. IEEE Trans. Aerosp. Electron. Syst. 2018, 54, 51–63. [CrossRef]
5. Zhao, L.; Wang, D.; Huang, B.; Xie, L. Distributed Filtering-Based Autonomous Navigation System of UAV. Unmanned Syst. 2015, 3, 17–34. [CrossRef]
6. Carrillo, L.R.G.; Fantoni, I; Rondon, E.; Dzulk, A. Three-dimensional position and velocity regulation of a quad-rotorcraft using optical flow. IEEE Trans. Aerosp. Electron. Syst. 2015, 51, 358–371. [CrossRef]
7. Kaiser, M.K.; Gans, N.R.; Dixon, W.E. Vision-Based Estimation for Guidance, Navigation, and Control of an Aerial Vehicle. IEEE Trans. Aerosp. Electron. Syst. 2010, 46, 1064–1077.
8. Khatib, O. Real-time obstacle avoidance for manipulators and mobile robots. Int. J. Robot. Res. 1986, 5, 90–99. [CrossRef]
9. Chazelle, B.; Edelsbrunner, H. An improved algorithm for constructing kth-order Voronoi diagrams. IEEE Trans. Comput. 1987, 100, 1349–1354. [CrossRef]
10. Li, Q.Q.; Zhe, Z. A Voronoi-based hierarchical graph model of road network for route planning. In Proceedings of the 11th Conference Intelligent Transportation Systems, Beijing, China, 12–15 October 2008; pp. 599–604.
