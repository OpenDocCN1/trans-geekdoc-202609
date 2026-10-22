evaluation. The root mean square error (*RMSE*) is used to evaluate performance in this stage. It can be described as

$$RMSE=\sqrt{\frac{1}{N}\sum_{i=1}^{N}(S(i)-O(i))^2}, \tag{3.7}$$

where $S(i)$ is *NSE* or *Bias* calculated by SM with the $i^{th}$ set of parameters; $O(i)$ is *NSE* or *Bias* calculated by VIC with the $i^{th}$ set of parameters.

If the values of *ER* of SM-I and *RMSE* of SM-II are less than the allowance error set by users, SM is built. Otherwise, we set $N=N+1$ and return to Step 1 to acquire more samples to train SM-I and SM-II until the *ER* and *RMSE* values meets the requirement.

# *Performance Metric of the Surrogate Model*

The Pareto solutions of SM are acquired and the parameter sets given by SM are validated with VIC. The distance between the center points of the two-point groups (one is the Pareto fronts of SM and the other is the points consisting of the objective values, which are calculated with the Pareto solutions of SM in VIC) is used to evaluate the performance of SM. Here, we define a center point as a point with the minimum sum of distance to all the points, which is shown as

$$\min \sum_i d=\sum_{i}^{n}\lVert x_0-x_i\rVert, \tag{3.8}$$

where the vector $x_0$ is the position of center point and the vectors $x_i$ ($i=1, 2, 3, \ldots,n$) are the positions of $n$ Pareto optimal points; $\lVert\cdot\rVert$ is the norm of vector. If the distance of the two center points is less than a specified value, the parameter calibration is complete. Otherwise, SM will be updated with the data mixing the original samples, which is used in the previous iteration with the validated values and then the next iteration will be conducted.

# 3.3. Study Area and Data

To show the performance of the proposed surrogate model, we choose the Lanjiang River (LJR) basin and the Xiangjiang River (XJR) basin, which are located in different parts of China. They have different features in land cover, dominating processes, and meteorological conditions in case studies to investigate the role and efficiency of a large and complex hydrologic model. The locations of the two basins are shown in Figure 3.3.