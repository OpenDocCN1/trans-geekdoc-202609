The covariance of the output quantities can be obtained by its PDF $\mathbf{g_Y}(\eta)$ as:

$Cov(Y_i, Y_j) = Cov(Y_j, Y_i) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} [\eta_i - E(Y_i)][\eta_j - E(Y_j)] g_{Y_i,Y_j}(\eta_i,\eta_j) d\eta_i d\eta_j \quad (5)$

where $g_{Y_i,Y_j}(\eta_i,\eta_j)$ is the joint PDF for the two random variables $Y_i, Y_j$.

The correlation of the output quantities can be obtained by its PDF $\mathbf{g_Y}(\eta)$ as:

$Corr(Y_i, Y_j) = Corr(Y_j, Y_i) = \frac{Cov(Y_i, Y_j)}{\sqrt{V(Y_i)V(Y_j)}} \quad (6)$

# 4. Experiment for Determination and Uncertainty Evaluation of the Error Correction Coefficients

The first experiment is the measurement of the standard artefact of the dot grid target. The purpose of this experiment is to obtain the parameters of the coefficients of the kinematic rigid body errors. Uncertainties of the obtained correction coefficients are also evaluated.

# 4.1. Determination of Error Coefficients

The standard artefact of the dot grid target is introduced in Part I of [18]. This artefact was measured in an environment under a controlled temperature of 20 ± 1 °C, using the Leica DCM-3D Confocal Microscopy at the Metrology Laboratory of the Technical University of Madrid. A magnification objective of 50x was used, with a numerical aperture of 0.9. The acquisition parameter of measurement area was defined as the topography stitching measurement, with a 4 × 4 extended topographies, covering an area of 0.828 × 0.621 mm². The parameter of overlapping area was 25% and the correlation takes XYZ option. The level of resolution was 1, and the measured extended topographies contained 2496 × 1872 pixels.

After the measurement, the confocal system generated a file with suffix name ".dat", containing three vectors, which are values of the X, Y, and Z coordinates. Data of this file was imported and analyzed by our developed algorithms. The raw measurement data is shown in Figure 2, which is an inclined surface with some outliers. This surface was aligned to be parallel with the X and Y coordinate plane using our developed surface rotation methods introduced in Part I [18]. The aligned surface is shown in Figure 3. The distribution of the values of the X, Y, and Z coordinates of the surface after rotation is shown in Figure 4.

![](bbox=[0.32, 0.65, 0.75, 0.8])

(a)

Figure 2. Cont.