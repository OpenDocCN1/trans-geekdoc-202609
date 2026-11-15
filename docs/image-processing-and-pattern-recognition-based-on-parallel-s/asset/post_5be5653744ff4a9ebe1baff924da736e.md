
![](img/d6ed6c69a61b1252a9084096bb4904c6_161_0.png)

| step | FAI |
|---|---|
| 0 | 54 |
| 1 | 53 |
| 2 | 12 |
| 3 | 35 |
| 4 | 18 |
| 5 | 9 |
| 6 | 36 |
| 7 | 29 |
| 8 | 6 |
| 9 | 5 |
| 10 | 20 |
| 11 | 3 |
| 12 | 2 |
| 13 | 9 |
| 14 | 0 |

![](img/d6ed6c69a61b1252a9084096bb4904c6_161_1.png)

| step | FAI |
|---|---|
| 0 | 54 |
| 1 | 54 |
| 2 | 19 |
| 3 | 7 |
| 4 | 3 |
| 5 | 5 |
| 6 | 5 |
| 7 | 2 |
| 8 | 6 |
| 9 | 0 |
| 10 | 0 |
| 11 | 0 |
| 12 | 0 |
| 13 | 0 |
| 14 | 0 |
| 15 | 0 |
| 16 | 0 |

![](img/d6ed6c69a61b1252a9084096bb4904c6_161_2.png)

| step | FAI |
|---|---|
| 0 | 54 |
| 1 | 49 |
| 2 | 33 |
| 3 | 30 |
| 4 | 25 |
| 5 | 20 |
| 6 | 15 |
| 7 | 10 |
| 8 | 2 |
| 9 | 0 |
| 10 | 0 |
| 11 | 0 |
| 12 | 0 |
| 13 | 0 |
| 14 | 0 |
| 15 | 0 |
| 16 | 0 |

![](img/d6ed6c69a61b1252a9084096bb4904c6_161_3.png)

| step | FAI |
|---|---|
| 0 | 54 |
| 1 | 4 |
| 2 | 14 |
| 3 | 19 |
| 4 | 7 |
| 5 | 3 |
| 6 | 5 |
| 7 | 4 |
| 8 | 7 |
| 9 | 0 |
| 10 | 0 |
| 11 | 0 |
| 12 | 0 |
| 13 | 0 |
| 14 | 0 |

![](img/d6ed6c69a61b1252a9084096bb4904c6_161_4.png)

Fig. 8.11: Example of a FAI for an image with negative increment values between shift steps

![](img/d6ed6c69a61b1252a9084096bb4904c6_162_0.png)

![](img/d6ed6c69a61b1252a9084096bb4904c6_162_1.png)

![](img/d6ed6c69a61b1252a9084096bb4904c6_162_2.png)

Fig. 8.12: An example of symmetric figures with the same FAI

In the example shown, the functions of the area of intersection differ for the shear directions 45° and 135°. They indicate the orientation of the triangle in the plane. They also indicate that these are equal triangles by magnitude. Changes in the scales of the figure can be determined by the dynamics of the change in the function of the area of intersection. At the same time, the scale factor is determined. For the same images with different scales, there should be a constant coefficient of proportionality of the change in the function of the area of intersection.

## 8.3 Description of Image with the Help of Quantitative Characteristics of the Basic Properties of FAI

This method differs from the method described in Section 8.2 as in that the FAI curve is analysed. If in the first method the numerical values of the function of the area of intersection are stored and processed, then in the second method, it is the FAI curve.

The graphic method of analysis is described in detail and clearly by using Figs 8.2 and 8.3.

To implement the second method of image description, a program was developed that simulates the technique for analysing the FAI curve. As well as for the previous method, the functions of the area of intersection were formed for shear directions at angles: 0°, 45°, 90°, 135°, 180°, 225°, 270° and 315°. Also for research, images of the BMP format with a size of 500×500 discrete elements (pixels) were selected. The number of division steps was chosen up to seven partitions, that is, the FAI curve can be analysed as a whole, with the help of two sections, three sections, etc. The maximum number of sections of the partition of curve is seven. For larger image sizes, it is necessary to increase the number of sections of the FAI curve. However, if the image has small dimensions, then the possible number of partitions of the FAI curves will decrease.

In the previous section, various deviations from the standard models of images, as well as their orientation were estimated. However, to determine the scale changes using the first method is difficult; most suitable is the second method.

Thus, the first direction of experimental research using the second method is the determination of images of same shapes and different sizes. To solve this problem, a reference image was initially assigned, and its FAI and values of the FAI curvature were determined at all sections of the FAI curve partition. Even images of the same figure were enlarged or reduced in scale.

Thus, sets of figures of the same shape were created. The forms were determined by the number of vertices in the polygon and the angles at these vertices between adjacent sides. For performing experimental studies the images shown in Fig. 8.13 were selected.

For triangles modified on a scale, the following curvature values were obtained for each part of the partition. The results are shown in Figs 8.14–8.16.

Analysis shows that this is a triangle due to the analysis of the 135° direction. The remaining values coincide, which also indicates that this is a right-angled triangle whose catheti are parallel to the coordinate axes. It is also important to note the dynamics of changes in curvature values of the triangle. For example, for the direction of the shift of 90° and for three

![](img/d6ed6c69a61b1252a9084096bb4904c6_164_0.png)

| | 51 | 52 | 53 | 54 | 55 | 56 | 57 |
|---|---|---|---|---|---|---|---|
| 0 | 0.5 | 9 | 8.5 | 10 | 10 | 10 | 10 |
| - | 4.5 | 6 | 7.5 | 9 | 9 | 9 | 9 |
| - | - | 3 | 6.5 | 6 | 9 | 8 | 8 |
| - | - | - | 7.5 | 7 | 7 | 7 | 7 |
| - | - | - | - | 6 | 6 | 6 | 6 |
| - | - | - | - | - | 5 | 5 | 5 |
| - | - | - | - | - | - | 4 | 4 |

| | 51 | 52 | 53 | 54 | 55 | 56 | 57 |
|---|---|---|---|---|---|---|---|
| 0 | 6.5 | 9 | 7.5 | 10 | 10 | 10 | 10 |
| - | 4.5 | 6 | 7.5 | 9 | 9 | 9 | 9 |
| - | - | 3 | 5.5 | 8 | 8 | 8 | 8 |
| - | - | - | 3.5 | 7 | 7 | 7 | 7 |
| - | - | - | - | 6 | 6 | 6 | 6 |
| - | - | - | - | - | 5 | 5 | 5 |
| - | - | - | - | - | - | 4 | 4 |

| | 51 | 52 | 53 | 54 | 55 | 56 | 57 |
|---|---|---|---|---|---|---|---|
| 0 | 9.5 | 9 | 8.5 | 10 | 10 | 10 | 10 |
| - | 4.5 | 6 | 7.5 | 9 | 9 | 9 | 9 |
| - | - | 3 | 5.5 | 8 | 8 | 8 | 8 |
| - | - | - | 3.5 | 7 | 7 | 7 | 7 |
| - | - | - | - | 6 | 6 | 6 | 6 |
| - | - | - | - | - | 5 | 5 | 5 |
| - | - | - | - | - | - | 4 | 4 |

| | 51 | 52 | 53 | 54 | 55 | 56 | 57 |
|---|---|---|---|---|---|---|---|
| 0 | 17 | 19 | 19 | 7 | 7 | 7 | 7 |
| - | 9 | 15 | 15 | - | - | - | - |
| - | - | 11 | 11 | - | - | - | - |
| - | - | - | 7 | - | - | - | - |
| - | - | - | - | - | - | - | - |
| - | - | - | - | - | - | - | - |
| - | - | - | - | - | - | - | - |

Fig. 8.13: Images selected as standard models for conducting experimental studies by the second method

Fig. 8.14: The results of the FAI curvature analysis for the first triangle

partitions, the neighboring values of the quantities differ by 3, and for four directions, the increment values differ by 2. For all other partitions (90° being the direction of the shift), the difference consists of 1. For other shear directions, the difference between adjacent curvature values is different. These values determine the shape, size and orientation of the triangle.

Based on the results of the analysis of the curvature of the function of the area of intersection of the second triangle, the same dynamics of changes in the curvature values of the function of the area of intersection are seen. However, their values are different. For the second triangle, the increments are greater than for the first; for example, for three partitions (shift direction of 90°), the difference in magnitudes is 4, and for the first triangle, it is 3. This indicates that the second triangle is larger than the first.

![](img/d6ed6c69a61b1252a9084096bb4904c6_165_0.png)

| 80 | 81 | 82 | 83 | 84 | 85 | 86 | 87 |
|---|---|---|---|---|---|---|---|
| 8.5 | 12 | 10.5 | 14 | 10.5 | 10.5 | 14.5 | 18 |
| - | 5 | 12.5 | 11 | 22.5 | 12.5 | 12.5 | 14 |
| - | - | 12.5 | 9 | 30.5 | 10.5 | 19.5 | 13 |
| - | - | - | - | 8.5 | 8.5 | 8.5 | 12 |
| - | - | - | - | 8.5 | 8.5 | 6.5 | 11 |
| - | - | - | - | - | 6.5 | 6.5 | 10 |
| - | - | - | - | - | - | 2.5 | 9 |

| 80 | 81 | 82 | 83 | 84 | 85 | 86 | 87 |
|---|---|---|---|---|---|---|---|
| 8.5 | 12 | 10.5 | 14 | 10.5 | 10.5 | 10.5 | 18 |
| - | 9 | 8.5 | 11 | 12.5 | 12.5 | 12.5 | 14 |
| - | - | 8.5 | 9 | 30.5 | 12.5 | 12.5 | 13 |
| - | - | - | 5 | 8.5 | 8.5 | 8.5 | 12 |
| - | - | - | - | 6.5 | 8.5 | 8.5 | 11 |
| - | - | - | - | 6.5 | 6.5 | 6.5 | 10 |
| - | - | - | - | - | 4.5 | 4.5 | 9 |

| 80 | 81 | 82 | 83 | 84 | 85 | 86 | 87 |
|---|---|---|---|---|---|---|---|
| 8.5 | 12 | 10.5 | 14 | 10.5 | 10.5 | 14.5 | 18 |
| - | 9 | 9.5 | 11 | 32.5 | 12.5 | 13.5 | 14 |
| - | - | 8.5 | 9 | 30.5 | 12.5 | 12.5 | 13 |
| - | - | - | - | 8.5 | 8.5 | 6.5 | 12 |
| - | - | - | - | 6.5 | 6.5 | 6.5 | 11 |
| - | - | - | - | - | 4.5 | 4.5 | 10 |
| - | - | - | - | - | - | 2.5 | 9 |

| 80 | 81 | 82 | 83 | 84 | 85 | 86 | 87 |
|---|---|---|---|---|---|---|---|
| 17 | 15 | 17 | 20 | 24 | 28 | 26 | 7 |
| - | 13 | 13 | 25 | 25 | 25 | 25 | - |
| - | - | 11 | 21 | 21 | 21 | 21 | - |
| - | - | - | 17 | 17 | 17 | 17 | - |
| - | - | - | - | 15 | 15 | 15 | - |
| - | - | - | - | - | 9 | 9 | - |
| - | - | - | - | - | - | 9 | - |

![](img/d6ed6c69a61b1252a9084096bb4904c6_165_1.png)

| 80 | 81 | 82 | 83 | 84 | 85 | 86 | 87 |
|---|---|---|---|---|---|---|---|
| 12 | 17.5 | 10.5 | 28 | 18 | 18 | 29.5 | 29.5 |
| - | 7 | 11.5 | 14.5 | 28 | 28 | 12.5 | 12.5 |
| - | - | 8.5 | 12.5 | 12 | 13 | 12.5 | 11.5 |
| - | - | - | 6.5 | 28 | 19 | 15.5 | 10.5 |
| - | - | - | - | 7 | 7 | 14.5 | 11.5 |
| - | - | - | - | - | 4 | 9.5 | 9.5 |
| - | - | - | - | - | - | 7.5 | 7.5 |

| 80 | 81 | 82 | 83 | 84 | 85 | 86 | 87 |
|---|---|---|---|---|---|---|---|
| 11 | 14 | 12.5 | 10.5 | 24 | 19 | 19.5 | 19.5 |
| - | 7 | 11.5 | 14.5 | 25 | 16 | 17.5 | 15.5 |
| - | - | 5.5 | 13.5 | 15 | 13 | 15.5 | 15.5 |
| - | - | - | 6.5 | 18 | 10 | 12.5 | 12.5 |
| - | - | - | - | 7 | 7 | 11.5 | 11.5 |
| - | - | - | - | - | 4 | 9.5 | 9.5 |
| - | - | - | - | - | - | 7.5 | 7.5 |

| 80 | 81 | 82 | 83 | 84 | 85 | 86 | 87 |
|---|---|---|---|---|---|---|---|
| 11 | 18 | 12.5 | 10.5 | 24 | 19 | 19.5 | 19.5 |
| - | 7 | 11.5 | 14.5 | 25 | 16 | 17.5 | 15.5 |
| - | - | 5.5 | 13.5 | 15 | 13 | 15.5 | 15.5 |
| - | - | - | 6.5 | 18 | 10 | 12.5 | 12.5 |
| - | - | - | - | 7 | 7 | 11.5 | 11.5 |
| - | - | - | - | - | 4 | 9.5 | 9.5 |
| - | - | - | - | - | - | 7.5 | 7.5 |

| 80 | 81 | 82 | 83 | 84 | 85 | 86 | 87 |
|---|---|---|---|---|---|---|---|
| 12 | 13 | 21 | 37 | 36 | 36 | 38 | 39 |
| - | 17 | 23 | 26 | 26 | 26 | 26 | 26 |
| - | - | 11 | 21 | 21 | 21 | 21 | 21 |
| - | - | - | 13 | 13 | 27 | 27 | 27 |
| - | - | - | - | 20 | 28 | 28 | 28 |
| - | - | - | - | - | 19 | 19 | 19 |
| - | - | - | - | - | - | 13 | 13 |

Fig. 8.15: The results of the FAI curvature analysis for the second triangle

Fig. 8.16: The results of the FAI curvature analysis for the third triangle

The analysis of the function of the area of intersection of the third triangle shows that the image of the third triangle is larger than the images of the first two triangles. In the direction of 135°, there are differences and all the partitions are filled. This shift direction indicates the same orientation for images of all triangles.

The results of the analysis of the FAI curve for squares are presented in Figs 8.17-8.19.

An analysis of the function of the area of intersection of the square shows that in the perpendicular shear directions the values of all the curvature coincide. This indicates that the figure is a square with a size of 10x10. The larger squares are represented on Figs 8.18 and 8.19.

From the values obtained, it can be determined that the square has dimensions of 15x15 and more than the previous one.
