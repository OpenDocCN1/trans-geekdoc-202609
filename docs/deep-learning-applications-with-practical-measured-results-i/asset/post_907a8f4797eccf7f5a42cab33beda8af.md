
Attached. For our Imaging CM, the probe is attached to the Z-stage. Therefore, it is obvious that the translation of the X and Y carriage, with an offset of the position $\vec{P}$, stops at the same point reached by the translation of the Z carriage with a probe offset $\vec{T}$, which can be understood as the focus of the probe with the measurand. According to this conclusion, a diagram of the axis chain vector of 3D imaging microscopy is plotted and shown in Figure 1b.

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_152_0.png)

Figure 1. Manifestation of the vectors in 3D Imaging CM: (a) 3D view; (b) diagram of the axis chain vector.

As shown in Figure 1b, there are two kinematical paths from the coordinate origin O(0,0,0) to the laser beam focus, i.e., $\vec{Z} \rightarrow \vec{T}$ and $\vec{X} \rightarrow \vec{Y} \rightarrow \vec{P}$. In each kinematical path, the actual movement of that axis is affected by the rotational error of its predecessors. The movement of $\vec{T}$ is affected by the rotational error of the movement of $\vec{Z}$. $\vec{Y}$ is affected by the rotational error of $\vec{X}$. $\vec{P}$ is affected by the rotational errors of $\vec{X}$ and $\vec{Y}$. Therefore, the chain vector shown in Figure 1b for the two kinematical paths, from the same origin reaching the same laser beam focus, can be expressed by Equation (1).

$$\vec{Z} + \mathbf{R}^{-1}(Z)\vec{T} = \vec{X} + \mathbf{R}^{-1}(X)\vec{Y} + \mathbf{R}^{-1}(X)\mathbf{R}^{-1}(Y)\vec{P}\tag{1}$$

After rearrangement of the above equation, vector $\vec{P}$ can be expressed by all the other vectors and matrices, as the same result presented by G. Zhang et al. [1].

The rotation can be expressed by the infinitesimal rotation matrix. The vectors $\vec{X}$, $\vec{Y}$, $\vec{Z}$ and $\vec{T}$ can be substituted by their position matrix. This has been widely accepted and implemented by many former investigators [1,15,27,30].

In the 3D Imaging CM, there are no real X- and Y-carriages, the workpiece is carried by a lateral stage mounted on a fixed base [13,27], the Z-stage is mounted on another fixed base. In addition to that, the beam focus is considered to be the probe. As the focus is always on the workpiece surface and the information is acquired exactly at that point, there is no Abbe offset on x, y and z, nor is there an angular term. This means $\vec{T}=0$ and $\mathbf{R}(Z)=0$.

In this work, only geometric errors along the X- and Y-directions are studied. After dropping out the Z-stage variables, the geometric error functions for X- and Y-stage are:

$$P_x = x + \delta_x(x) + \delta_x(y) - y \cdot \sigma_z(y)\tag{2}$$

$P_y = y + \delta_y(x) + x \cdot \sigma_z(x) + \delta_y(y) + x \cdot \sigma_z(y)$
(3)

Those errors in Equations (2) and (3) are functions, which can be simulated by Legendre polynomials. Implementation of Legendre polynomials is computationally simpler and provides a reduction of around 2% higher than using Chebyshev polynomials [31]. After substituting the error functions in Equations (2) and (3) by using the approximation of Legendre polynomials, the final mathematical models for the beam focus point $\vec{P}(P_x, P_y, 0)$ with error corrections can be acquired:

$P_x = x + a_1 x + \frac{3}{2}a_2 x^2 + \frac{3}{2}a_3(5x^3 - 3x) +$
$+ b_1 y + \frac{3}{2}b_2 y^2 + \frac{3}{2}b_3(5y^3 - 3y) -$
$- y \cdot (c_1 y + \frac{3}{2}c_2 y^2 + \frac{3}{2}c_3(5y^3 - 3y))$
(4)

$P_y = y + d_1 x + \frac{3}{2}d_2 x^2 + \frac{3}{2}d_3(5x^3 - 3x) +$
$+ x \cdot (e_1 x + \frac{3}{2}e_2 x^2 + \frac{3}{2}e_3(5x^3 - 3x)) +$
$+ f_1 y + \frac{3}{2}f_2 y^2 + \frac{3}{2}f_3(5y^3 - 3y) +$
$+ x \cdot (c_1 y + \frac{3}{2}c_2 y^2 + \frac{3}{2}c_3(5y^3 - 3y))$
(5)

## 3. Methodology and a Brief Introduction of Experimental Design

To calibrate the kinematic geometric errors of the lateral stage of a dual core 3D CM, a standard artefact with dot grid target on glass is measured and a series of algorithms are developed for the process of the raw measurement data, which include separations of cylinders and flat, fitting of cylinder centers, determination of coefficients, etc. Figure 2 illustrates the standard, which was provided by Max Levy Autograph, Inc. Those dots are deposited on the substrate, which is glass with a thickness of 1.5 mm. Table 1 gives an indication of the size, the dot spacing, the diameter, the accuracy, etc., of the dot pattern.

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_153_0.png)

Figure 2. Illustration of the standard artefact of the dot grid target.

Table 1. Detailed information about the dot grid target standard artefact.

| Width [mm] | Dot Diameter [mm] | Dot Spacing [mm] | X and Y Axis Accuracy [mm] | Dot Array |  |  |
|---|---|---|---|---|---|---|
|  |  |  |  | X | Y | Total |
| 25 | 0.0625 | 0.125 | ±0.001 | 201 | 201 | 40401 |

This work aims at characterizing and correcting the kinematic geometric errors of the movement of the lateral stage, by calculating and applying the coefficients of Equations (4) and (5). To calculate the coefficients, the introduced dot grid target standard is measured, the measurement data are processed for obtaining the coordinate values $(x_i, y_i)$ of the dots' centers, the coordinate values $(x_i, y_i)$ and their corresponding certified values are put into Equations (4) and (5), the coefficients are obtained by solving the equations using non-linear Least Squares method. The obtained coefficients and Equations (4) and (5) are implemented for correcting the new measurement data. Another different area of the introduced dot grid target standard is measured, and the measurement data is corrected. By comparing

the residuals before correction and after correction, the significance and practicality of our model for kinematic geometric error correction can be observed.

The algorithms used for measurement data processing and for calculating the coefficients are introduced in Section 4. Validations of those algorithms are introduced in Section 5. The details of the experimental procedures, parameters, and analysis are presented in Part II, which is published in another paper in the same journal.

## 4. Algorithms and Procedures for Measurement Data Processing

### 4.1. Algorithm and Procedure for the Separation of Flats and Cylinders

The raw measurement data usually contains defects, outliers, unmeasured points, etc. [32]. The measured surface often inclines, as it is impossible to locate the measurand surface perfectly perpendicular to the Z-axis. Figure 3 gives an example of the measurement of the dot grid target, implementing an objective of magnification 50×, numerical aperture of 0.90. The acquisition parameter of measurement area was defined as the topography stitching measurement, with 8 × 8 extended topographies, covering an area of 1.78 × 1.33 mm². The parameter of the overlapping area is 25%, and the correlation takes the XYZ option. The level of resolution is 2, and the measured extended topographies contain 2673 × 2003 pixels.

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_154_0.png)

Figure 3. Reconstruction of the measured surface with its raw measurement data: (a) contour plot; (b) surf plot.

This measurement has many unmeasured points in the right-top corner due to the Z-range parameter setting. The first step is to choose an area of this raw surface with appropriate size and location, targeting at minimizing the influence of defects and removing outliers [32] by selecting valid grid positions with loss of the uniformity of the grid. Figure 4 shows a surface reconstruction by trimming the raw data with 10% edges along the X- and Y-directions. As there are too many measurement defects when y > 800 μm, this part is also abandoned.

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_155_0.png)

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_155_1.png)

Figure 4. Reconstruction of the surface with trimmed raw data: (a) contour plot; (b) areal plot.

After obtaining an appropriate area for analysis, it is necessary to eliminate its form. The principal axes of the distribution of data points of the measured point cloud are determined by solving the eigen value problem. The data are rotated by principal axis transformation to align them in the direction of the eigen vectors. Figure 5 gives an example of the rotated surface, which is rotated from the surface shown in Figure 4. Figure 5a was plotted by the Matlab® function ‘plot3’, while Figure 5b was plotted by the function ‘surf’. It can be found that after rotation, the range of the Z-axis is much smaller, and many details of the surface can be observed. It is obvious that this surface is constructed using point clouds, which form a flat plane and many cylinders perpendicular to this flat.

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_155_2.png)

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_155_3.png)

Figure 5. Reconstruction of the rotated surface: (a) point plot; (b) surfplot using Z for the color data.

This rotated surface is now ready for the separation of flats and cylinders. Figure 6 gives an indication of the distribution of the heights of the surface. Figures 7 and 8 give examples of the separations of the rotated surface shown in Figure 5.
