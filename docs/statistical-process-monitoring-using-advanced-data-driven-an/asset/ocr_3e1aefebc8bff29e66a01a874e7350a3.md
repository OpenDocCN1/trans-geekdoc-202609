pixel in the right image, \( I_{right} \):

\(\mathcal{D}_{SAD}(i, j, d) = \sum_{u=-\omega}^{\omega} \sum_{u=-\omega}^{\omega} \left| I_{left}(i+u, j+v) - I_{right}(i+u, j-d+v) \right| \quad (8.1)\)

where \( d \) represents the disparity interval \( [d_{min}, d_{max}] \), which is delimited between the minimum and maximum disparity values (\( d_{min} \) and \( d_{max} \), respectively), and \( i \), \( j \) are the coordinates (rows and columns, respectively) of the center pixel of the SAD. Differences are summed over the support window, \( \omega \), to obtain a disparity map.

Estimating the position of the road profile is helpful for identifying obstacles that are standing in the monitored scene. After generating the disparity map, it is essential to compute the U-disparity and V-disparity maps [39]. V-Disparity maps that effectively estimate a road's profile using transform and depth estimation have been developed [4, 6]. These maps have shown a good ability to provide information about obstacles' height and position in reference to the ground [4, 6]. For illustration purposes, Fig. 8.1A–B depicts V-disparity maps of a free scene and a busy scene. The steps for computing the V-disparity are sketched in Algorithm 1.

| Algorithm 1: V-disparity computation steps. |
| :--- |
| Input: Disparity map DispMap(rows, cols) |
| Input: Dmax: Max disparity value. |
| Output: V-disparity DispMap_v (rows, D_max) |
| 1 for Each row r in DispMap do |
| 2     for Each column c in DispMap do |
| 3         current Disparity <- DispMap(r, c) |
| 4         if current Disparity > 0 then |
| 5             DispMap_v(r, c) <- (current Disparity + 1) |

In order to surround obstacles in the ROI, the obstacles' width must be determined. U-disparity expresses histograms over the disparity values for each image column (the U coordinate) [4, 6, 40]. In other words, both the V-disparity and U-disparity can be defined as the number of pixels with the same level of disparity at rows' Y-axis and columns' X-axis in the disparity map. Algorithm 2 describes the main steps taken to obtain the U-disparity.

Relevant information about urban environments can be learned from the U–V-disparity. Fig. 8.1A–B illustrates the U–V-disparity by providing examples of V-disparity and U-disparity analysis of a free scene and a scene containing obstacles, respectively. Interestingly, the road surface is viewed as an inclined line in the V-disparity map, while the static environment is represented by a vertical line (cloud of points) on the lower disparity map. Its thickness is related to the