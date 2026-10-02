where X_max, Y_max and Z_max refer to the maximum values of the corresponding coordinates, which can be obtained from the data set. Moreover, from the data set, we can dram the vertical error correction point and the horizontal error correction point in three-dimensional space. Figure 2 is the result we have drawn with MATLAB.

![](bbox=[0.1, 0.22, 0.9, 0.62])

Figure 2. The physical space and the correct point. The blue point is the vertical error correction point, the yellow point is the horizontal error correction point, the red pentagram indicates starting point, the green pentagram indicates ending points. The range of axes comes from the data set.

# 3.1.2. Objective Function

Two objective optimization functions are proposed for minimizing the trajectory length of a UAV and the number of times an UAV has been corrected:

$F_1 = \min\left(\sum_{i=1}^{m} (\eta_i + \lambda_i + h_i)\right)$ (2)

$F_2 = \min\left(\sum_{i=1}^{m} (a_i + b_i)\right)$ (3)

where $F_1$ represents the trajectory length of an UAV from the starting point A to the ending point B, $F_2$ represents the number of times an UAV has been corrected through the correction area, m represents the total number of corrections of an UAV throughout the flight, $\eta_i$ represents the distance of an UAV's $i$-th flight, $\lambda_i$ represents the correction distance of the $i$-th flight to the vertical error correction point, $h_i$ represents the correction distance of the $i$-th flight to the horizontal error correction point, $a_i$ represents an UAV's $i$-th flight reaches the vertical error correction point, and $b_i$ represents a UAV's $i$-th flight at the horizontal error correction point.