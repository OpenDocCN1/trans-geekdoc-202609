
![](img/8b41ef3997625b78ba4cb189dbc5f7b9_179_0.png)

Figure 12. Contour of the Euclidean residuals between each certified and measured points.

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_179_1.png)

Figure 13. Contour of the Euclidean residuals between each certified and corrected points.

It can be concluded that the determined coefficients for kinematic geometric error correction works very well in this measurement.

## 4.2. Uncertainty Evaluation

Uncertainty evaluation of the geometric error coefficients is based on the algorithms introduced in Section 3. The heart of the approach is making repeated draws from the PDFs for the input variables Xi (or joint PDF for X) and the evaluation of the output quantity. Here, we define the determinations of the number of repeated draws, namely, the number of simulation trials, the PDFs for the input variables, and the evaluation of the output quantity.

According to GUM-S2 [23] the main stages of uncertainty evaluation constitute formulation, propagation, and summarizing describes as follows:

- 1. The first stage of formulation includes:
  (a) Define the output quantity, namely, the geometric error correction coefficients Cc = (a1, ... g3);
  (b) Determine the input quantity upon which Cc depends, namely, the measurement results (x, y) and their corresponded certified values (Px, Py);
  (c) Develop a measurement function f or measurement model relating the input and output quantities, namely, Equations (4) and (5);
  (d) On the basis of available knowledge, assign PDFs to the components of the input quantities. As indicated by Table 2 in Part I [18], the certified values (Px, Py) follow a rectangular distribution U(−1, 1) μm. As there is no more information about the sources of uncertainties for (Pₓ, Pᵧ) or information for the measured values of X and Y coordinates (x, y), here does not assign more uncertainties to the input quantities, for not introducing unnecessary uncertainties.

- 2. The second stage, propagation, includes: Propagate the PDFs for the components of input quantities through the model to obtain the (joint) PDF for the output quantity.
- 3. The final step, summarizing, includes: Use the PDF for the output quantity to obtain the expectation of the output quantity, the uncertainty matrix, also named covariance matrix, associated with the expectation of the output quantity, and a coverage region containing the output quantity with a specified probability p (the coverage probability).

The simulation was repeated 1 × 10⁴ times. Mean values, expanded uncertainties (k = 2), as well as lower and upper boundaries for a 95% coverage interval are listed in Table 3. Distributions for the output quantities are shown in Figure 14 and we observe that non-symmetric distributions and not assimilable to normal distributions are obtained.

## Table 3. Parameters of the coefficients of the mathematical models for lateral geometric error correction.

| Parameter | Mean Value | Expanded Uncertainty | 95% Coverage Interval Lower Boundary | 95% Coverage Interval Upper Boundary |
|---|---|---|---|---|
| a₁ | 7.50 × 10⁻³ | 4.74 × 10⁻³ | 5.07 × 10⁻³ | 1.61 × 10⁻² |
| a₂ | −2.13 × 10⁻⁶ | 5.41 × 10⁻⁶ | −1.28 × 10⁻⁵ | −6.12 × 10⁻⁸ |
| a₃ | 2.00 × 10⁻¹⁰ | 7.14 × 10⁻¹⁰ | −1.35 × 10⁻¹⁰ | 1.21 × 10⁻⁹ |
| b₁ | −5.91 × 10⁻⁶ | 8.85 × 10⁻³ | −1.62 × 10⁻² | 2.99 × 10⁻³ |
| b₂ | −9.91 × 10⁻⁶ | 9.19 × 10⁻⁶ | −1.50 × 10⁻⁵ | 2.08 × 10⁻⁶ |
| b₃ | −6.86 × 10⁻¹² | 2.36 × 10⁻⁹ | −8.94 × 10⁻¹⁰ | 2.67 × 10⁻⁹ |
| c₁ | 3.41 × 10⁻⁶ | 7.89 × 10⁻⁶ | −6.22 × 10⁻⁶ | 7.41 × 10⁻⁶ |
| c₂ | 1.26 × 10⁻⁸ | 1.86 × 10⁻⁸ | 2.21 × 10⁻¹⁰ | 3.86 × 10⁻⁸ |
| c₃ | −8.16 × 10⁻¹³ | 3.44 × 10⁻¹² | −5.74 × 10⁻¹² | 1.56 × 10⁻¹³ |
| d₁ | −6.57 × 10⁻³ | 4.97 × 10⁻³ | −8.53 × 10⁻³ | 3.52 × 10⁻³ |
| d₂ | 3.93 × 10⁻⁶ | 1.94 × 10⁻⁶ | 1.39 × 10⁻⁶ | 5.37 × 10⁻⁶ |
| d₃ | −5.88 × 10⁻¹¹ | 3.78 × 10⁻¹⁰ | −4.59 × 10⁻¹⁰ | 1.53 × 10⁻¹⁰ |
| e₁ | 5.89 × 10⁻⁶ | 2.95 × 10⁻⁶ | 2.00 × 10⁻⁶ | 8.04 × 10⁻⁶ |
| e₂ | −6.57 × 10⁻⁹ | 6.71 × 10⁻⁹ | −1.44 × 10⁻⁸ | −4.88 × 10⁻¹¹ |
| e₃ | −2.34 × 10⁻¹⁵ | 5.80 × 10⁻¹³ | −2.36 × 10⁻¹³ | 3.30 × 10⁻¹³ |
| f₁ | −2.21 × 10⁻² | 1.42 × 10⁻² | −5.15 × 10⁻² | −1.43 × 10⁻² |
| f₂ | 1.40 × 10⁻⁵ | 1.73 × 10⁻⁵ | 6.71 × 10⁻⁶ | 4.98 × 10⁻⁵ |
| f₃ | −2.94 × 10⁻⁹ | 2.92 × 10⁻⁹ | −5.37 × 10⁻⁹ | −1.14 × 10⁻¹¹ |

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_180_0.png)

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_180_1.png)

Figure 14. Cont.

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_181_0.png)

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_181_1.png)

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_181_2.png)

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_181_3.png)

Figure 14. Distributions of the uncertainties of some geometric error correction coefficients.

## 5. Experimental Study of the Applications of Determined Coefficients

This section aims to verify the applicability of the determined error correction coefficients and the residuals of measured and corrected points with respect to certified points are compared.

This experiment measures the dot grid target standard used in Section 4. The measured area of this standard is different from those in Section 4. All the environmental and operational parameters are the same as those in Section 4. The measurement data are processed using the same algorithms and procedures, until the fitted cylinder centers are approximated parallel with the x-axis. Then the fitted centers are corrected by the error correction coefficients determined. By comparing the mean residuals, the sum of all squared residuals, and the standard deviation of residuals of measured points and corrected points with respect to certified positions, the effectiveness of the calculated coefficients and our model can be observed.

Measurement data are processed using our developed and validated algorithms. The raw measurement data with form removed are shown in Figure 15, implementing the form removal method presented in the pair publication Part I [18] Section 4.1. The cylinders are separated from the base with our developed algorithms, with results demonstrated in Figure 16. Figure 16a shows the initial separated cylinders, Figure 16b shows the cylinders with outliers removed and with clusters classified, and Figure 17 shows the histograms of the three coordinates of the cylinders.

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_182_0.png)

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_182_1.png)

Figure 15. The measured surface with form removed: (a) 3D reconstruction and (b) 2D reconstruction.

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_182_2.png)

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_182_3.png)

Figure 16. Separation of the cylinders: (a) The separated cylinders from the base and (b) separate cylinders into individual clusters.

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_182_4.png)

Figure 17. Histogram of the three coordinates of the separated cylinders.

The separated clusters are fitted for their centers. The coordinate values of the fitted cylinder centers are shown in Table 4. Figure 18 shows the fitted cylinder centers, as well as the centroids of each cluster data.

## Table 4. The raw coordinate values of the fitted cylinder centers.

| Cluster N° | X Coordinate [µm] | Y Coordinate [µm] | Cluster N° | X Coordinate [µm] | Y Coordinate [µm] |
|---|---|---|---|---|---|
| 1 | 47.3 | 42.6 | 19 | 541.8 | 298.1 |
| 2 | 172.3 | 42.9 | 20 | 667.7 | 301.3 |
| 3 | 294.8 | 44.0 | 21 | 796.8 | 298.4 |
| 4 | 425.1 | 49.5 | 22 | 40.2 | 420.6 |
| 5 | 544.9 | 48.1 | 23 | 163.3 | 417.8 |
| 6 | 669.2 | 46.6 | 24 | 291.1 | 421.0 |
| 7 | 796.4 | 48.3 | 25 | 415.9 | 424.6 |
| 8 | 42.4 | 166.5 | 26 | 538.9 | 423.9 |
| 9 | 167.7 | 171.9 | 27 | 666.1 | 430.0 |
| 10 | 292.6 | 172.3 | 28 | 794.6 | 430.3 |
| 11 | 419.3 | 172.6 | 29 | 41.2 | 530.7 |
| 12 | 544.1 | 175.2 | 30 | 163.3 | 548.3 |
| 13 | 666.6 | 174.6 | 31 | 289.5 | 546.6 |
| 14 | 797.0 | 176.0 | 32 | 415.0 | 548.2 |
| 15 | 40.1 | 295.9 | 33 | 539.9 | 551.7 |
| 16 | 163.4 | 294.6 | 34 | 662.6 | 550.7 |
| 17 | 293.0 | 294.5 | 35 | 796.9 | 550.8 |
| 18 | 417.9 | 295.3 |  |  |  |

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_183_0.png)

## Figure 18. Comparison of the fitted circle center and the centroid of the data.

As shown in Figure 18, the cluster numbered 29 has too many outliers. Here, we only choose the first 28 clusters for the kinematic geometric error correction. The correction employs the mathematical model Equations (4) and (5), as well as our calculated error coefficients. Before correction, the data are aligned to be parallel with the X coordinate as much as possible. Table 5 shows the aligned measurement data and the corrected data.

## Table 5. The aligned and corrected measurement data.

| Cluster N° | X Coordinate [µm] (Rotated Measurement Data) | Y Coordinate [µm] (Rotated Measurement Data) | X Coordinate [µm] (Corrected Data by Error Coefficients) | Y Coordinate [µm] (Corrected Data by Error Coefficients) |
|---|---|---|---|---|
| 1 | 47.2 | 42.8 | 47.5 | 41.6 |
| 2 | 172.2 | 43.4 | 173.4 | 41.7 |
| 3 | 294.7 | 44.8 | 296.7 | 42.7 |
| 4 | 425.1 | 50.6 | 427.7 | 48.2 |
| 5 | 544.8 | 49.5 | 548.2 | 46.8 |
| 6 | 669.0 | 48.3 | 673.1 | 45.2 |
