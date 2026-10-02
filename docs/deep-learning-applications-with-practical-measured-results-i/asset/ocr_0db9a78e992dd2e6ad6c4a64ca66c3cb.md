$P_y = y + \delta_y(x) + x \cdot \sigma_z(x) + \delta_y(y) + x \cdot \sigma_z(y)$
(3)

Those errors in Equations (2) and (3) are functions, which can be simulated by Legendre polynomials. Implementation of Legendre polynomials is computationally simpler and provides a reduction of around 2% higher than using Chebyshev polynomials [31]. After substituting the error functions in Equations (21) and (22) by using the approximation of Legendre polynomials, the final mathematical models for the beam focus point $\vec{P}(P_x, P_y, 0)$ with error corrections can be acquired:

$P_x = x + a_1 x + \frac{3}{2}a_2 x^2 + \frac{3}{2}a_3(5x^3 - 3x) +$
$+ b_1 y + \frac{3}{2}b_2 y^2 + \frac{3}{2}b_3(5y^3 - 3y) -$
$- y \cdot (c_1 y + \frac{3}{2}c_2 y^2 + \frac{3}{2}c_3(5y^3 - 3y))$
(4)

$P_y = y + d_1 x + \frac{3}{2}d_2 x^2 + \frac{3}{2}d_3(5x^3 - 3x) +$
$+ x \cdot (e_1 x + \frac{3}{2}e_2 x^2 + \frac{3}{2}e_3(5x^3 - 3x)) +$
$+ f_1 y + \frac{3}{2}f_2 y^2 + \frac{3}{2}f_3(5y^3 - 3y) +$
$+ x \cdot (c_1 y + \frac{3}{2}c_2 y^2 + \frac{3}{2}c_3(5y^3 - 3y))$
(5)

# 3. Methodology and a Brief Introduction of Experimental Design

To calibrate the kinematic geometric errors of the lateral stage of a dual core 3D CM, a standard artefact with dot grid target on glass is measured and a series of algorithms are developed for the process of the raw measurement data, which include separations of cylinders and flat, fitting of cylinder centers, determination of coefficients, etc. Figure 2 illustrates the standard, which was provided by Max Levy Autograph, Inc. Those dots are deposited on the substrate, which is glass with a thickness of 1.5 mm. Table 1 gives an indication of the size, the dot spacing, the diameter, the accuracy, etc., of the dot pattern.

![](bbox=[0.22, 0.68, 0.72, 0.82])

Figure 2. Illustration of the standard artefact of the dot grid target.

Table 1. Detailed information about the dot grid target standard artefact.

| Width [mm] | Dot Diameter [mm] | Dot Spacing [mm] | X and Y Axis Accuracy [mm] | Dot Array |  |  |
|---|---|---|---|---|---|---|
|  |  |  |  | X | Y | Total |
| 25 | 0.0625 | 0.125 | ±0.001 | 201 | 201 | 40401 |

This work aims at characterizing and correcting the kinematic geometric errors of the movement of the lateral stage, by calculating and applying the coefficients of Equations (4) and (5). To calculate the coefficients, the introduced dot grid target standard is measured, the measurement data are processed for obtaining the coordinate values $(x_i, y_i)$ of the dots' centers, the coordinate values $(x_i, y_i)$ and their corresponding certified values are put into Equations (4) and (5), the coefficients are obtained by solving the equations using non-linear Least Squares method. The obtained coefficients and Equations (4) and (5) are implemented for correcting the new measurement data. Another different area of the introduced dot grid target standard is measured, and the measurement data is corrected. By comparing