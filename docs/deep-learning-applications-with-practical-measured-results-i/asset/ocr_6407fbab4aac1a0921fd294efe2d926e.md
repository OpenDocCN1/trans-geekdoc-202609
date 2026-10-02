![](bbox=[0.25, 0.15, 0.78, 0.38])

Figure 10. Flowchart of the algorithm for data partition.

Since the equations characterizing lateral linearity deviations, Equations (4) and (5) are independent of the vertical axis z, the dimension of the 3D point cloud is reduced to the two dimensions of the x-y-plane.

# 4.2. Algorithm for Determination of Coefficients

This section aims at the determination of the coefficients, a1, a2, a3, b1 … , f3, defined in Equations (4) and (5). The objective is to fit the 18 coefficients to obtain the least squared residuals between the corrected X- and Y- coordinates and the nominal position. That is:

$$\sum_{i=1}^{n} \|P_{nom}^i(x,y) - P_{corr}^i(x,y)\|_2^2 = \min \tag{8}$$

where, $P_{nom}^i(x,y)$ represents the $i_{th}$ nominal position defined by the X- and Y- coordinates, $P_{corr}^i(x,y)$ denotes the $i_{th}$ corrected position obtained from the measured data and Equations (4) and (5).

Therefore, the objective function is

$$\min F(x,y)|_{a1...f3} = \min \sum_{i=1}^{n} \|P_{nom}^i(x,y) - P_{corr}^i(x,y)\|_2^2 = \min\big((x_{nom}^i - x_{corr}^i)^2 + (y_{nom}^i - y_{corr}^i)^2\big) \tag{9}$$

The minimum value of F arrives when the gradient is zero [38,39], i.e.,:

$$\frac{\partial F}{\partial \beta_i} = 0 \tag{10}$$