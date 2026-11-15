
itself for the presence of negative values of the difference between the neighboring values of the function of the area of intersection. This means that the search negative values are performed. Negative increment values indicate that there are gaps in the image or voids that have a larger area than the elements belonging to the image at each step of the shift. For the fifth figure, the increment values are shown in Table 8.6.

Table 8.6: Results of calculating the deviations for the fifth image (Fig. 8.23) at all time steps of the shift

| Time-step number | 0° | 45° | 90° | 135° | 180° | 225° | 270° | 315° |
|---|---|---|---|---|---|---|---|---|
| 1. | 57 | 112 | 63 | 112 | 57 | 112 | 63 | 112 |
| 2. | -28 | -71 | -36 | -71 | -28 | -71 | -36 | -71 |
| 3. | 31 | 62 | 39 | 61 | 31 | 62 | 39 | 61 |
| 4. | -6 | -31 | -17 | -29 | -6 | -31 | -17 | -29 |
| 5. | 11 | 28 | 24 | 25 | 11 | 28 | 24 | 25 |
| 6. | 10 | -7 | -8 | -3 | 10 | -7 | -8 | -3 |
| 7. | -3 | 10 | 19 | 5 | -3 | 10 | 19 | 5 |
| 8. | 20 | 1 | -9 | 7 | 20 | 1 | -9 | 7 |
| 9. | -11 | 6 | 23 | 0 | -11 | 6 | 23 | 0 |
| 10. | 24 | 1 | -15 | 6 | 24 | 1 | -15 | 6 |
| 11. | -13 | 4 | 26 | 0 | -13 | 4 | 26 | 0 |
| 12. | 22 | 1 | -16 | 4 | 22 | 1 | -16 | 4 |
| 13. | -9 | 2 | 23 | 0 | -9 | 2 | 23 | 0 |
| 14. | 14 | 1 | -11 | 2 | 14 | 1 | -11 | 2 |
| 15. | 0 | 0 | 14 | 0 | 0 | 0 | 14 | 0 |

More clearly, the dynamics of the change in coordinates can be represented graphically (Fig. 8.27).

Use of the second method allows identification of images that have the same geometric content and are represented in different scales. Also, the second method allows determination of the shape of the figure and the various distortions. Herewith the number of data processed is less than that for the first method, have better visibility and better structuredness.

## 8.4 Experimental Analysis of FAI of Patterns Image

The parallel shift technology can be effectively used for images that have a complex structure and are used to form various patterns, especially the method for describing and analysing images that are filled with different patterns. Such images have the function of the area of intersection, the shape of which consists of a set of local extremes. A pattern is an image

![](img/d6ed6c69a61b1252a9084096bb4904c6_172_0.png)

Fig. 8.27: Histograms of the distribution of the values of the change in the FAI values for selected shear directions

consisting of lines, as well as colors and shadows. Patterns also make up templates that are based on repetition and on the alternation of constituent elements. Such patterns form the ornaments.

This form depends on the existence of gaps in the image. The magnitude of the gaps in the image determines the magnitude of the local maxima on the FAI curve. An example of such an FAI is presented for the image of a spiral in Fig. 8.26. Obviously, to estimate the function of the area of intersection by the second method, a large number of partitions and additional computations are required. Therefore, the most appropriate approach for estimating such FAIs is use of a method based on estimating the dynamics of the change in the area values at neighboring time-steps of the shift.

The first indicator of the presence of discontinuities in the image is the presence of a negative number in the code of quantities, which reflect the dynamics of the change in the FAI curve as shown in Table 8.6. The nature of the discontinuities is also determined by the analysis of the FAI obtained in various directions. An example of images with horizontal and vertical discontinuities, as well as their FAIs and the results of calculating the curvature for a different number of partitions are presented in Figs 8.28 and 8.29.

Analysis of the obtained values shows that the first and second methods are applicable for determining the discontinuities in the image. Figure 8.28 shows vertical discontinuity in the direction of shear 90°, since the line of the function of the area of intersection in this direction is almost a straight line. However, in one direction, it is impossible to judge the existence of discontinuity. It is also necessary to analyse the remaining directions. In our example, the functions of the area of intersection in these directions have local maxima, which indicate that there is a gap in the image. On the basis of the function of the area of intersection in the shift directions 0°, 45°, 90° and 135°, it is clear that there is a vertical gap in the image.

![](img/d6ed6c69a61b1252a9084096bb4904c6_173_0.png)

Fig. 8.28: An example of an image with a vertical discontinuity and its FAI in shear directions 0°, 45°, 90° and 135°

For the second example (Fig. 8.29), the straight line maps the FAI to the shift direction at 0°. The remaining functions of the area of intersection have a curved shape. The magnitude of the curvature determines the width of the rupture and of the parts of the image that are on either side of the rupture. This is also determined from the values of the curvature on the corresponding sections of the partition.

Both examples were considered for initial understanding of the description of different patterns using parallel shift technology. To describe the technique for recognising different patterns, the images shown in Fig. 8.30 are used.

![](img/d6ed6c69a61b1252a9084096bb4904c6_174_0.png)

Fig. 8.29: An example of an image with a vertical discontinuity and its FAI in shear directions 0°, 45°, 90° and 135°

![](img/d6ed6c69a61b1252a9084096bb4904c6_174_1.png)

Fig. 8.30: Examples of images that have a regular pattern and are used as patterns

The function of the area of intersection of submitted images of patterns are shown in Figs 8.31–8.37.

![](img/d6ed6c69a61b1252a9084096bb4904c6_175_0.png)

Fig. 8.31: The function of the area of intersection for the first two images is shown in Fig. 8.30 for the shift directions of 0°, 45°, 90° and 135°

![](img/d6ed6c69a61b1252a9084096bb4904c6_175_1.png)

Fig. 8.32: The function of the area of intersection for the third and fourth images is presented in Fig. 8.30 for the shear directions of 0°, 45°, 90° and 135°

![](img/d6ed6c69a61b1252a9084096bb4904c6_176_0.png)

Fig. 8.33: The function of the area of intersection for the fifth and sixth images is presented in Fig. 8.30 for the shear directions of 0°, 45°, 90° and 135°

![](img/d6ed6c69a61b1252a9084096bb4904c6_176_1.png)

Fig. 8.34: The function of the area of intersection for the seventh image is presented in Fig. 8.30 for the shift directions of 0°, 45°, 90° and 135°

Obviously, all the functions of the area of intersection are represented by curves that have shapes with local extremes. Moreover, these extremes have a certain periodicity until a zero value. For each pattern, the shape of the function of the area of intersection is different from the rest. At the same time, the FAI shapes are the same in the perpendicular directions (0°, 90° and 45°, 135°). However, the function of the area of intersection differs in some areas for the fourth and fifth images. So for the fourth image, we can determine the horizontal coordinates of image discontinuities. At these coordinates, there are no points that belong to the image. The FAI analysis along the directions of the fourth image shows that there are two horizontal ruptures (the number of extrema on the FAI curve for the 0° direction is 2), and the vertical discontinuities are seven (the number of extrema on the FAI curve for the 90° direction is 7). Here we can talk about discontinuities, since the extreme values are quite large. As noted earlier, the presence of local extremes indicates the presence of holes or depressions in the figure image. Discontinuities can only be talked about when there is a zero FAI value between the local extremes (Fig. 8.32). To describe and recognize such images, it is necessary to calculate the local extremes, the periods of their appearance and the scale changes in the obtained FAI.

## 8.5 The Sequence of Steps for Using Parallel Shift Technology to Describe and Recognise Images

The proposed image recognition system based on the technology of parallel shift realises an accurate analysis of the function of intersection by quantitative characteristics. An important feature of such a system is the ability to classify images at the input.

Like the classification characteristics of images, topological and geometric characteristics were used. To determine them, an analysis of images of figures with various topological and geometric characteristics was performed. Partially such an analysis is shown in this chapter. Topological characteristics were defined as: the number of vertices of the figure, the number of holes in the filled figure and the number of contour distortions.

The number of vertices is defined as convex vertices (Fig. 8.35a) and concave vertices (Fig. 8.35b). In this case, concave vertices cannot exist without convex vertices. This means that concavity is realised only in convex figures.

In Fig. 8.35(a) is represented the original image, and Fig. 8.35(b) is the same image with two concave vertices. Thus, the number of vertices increased from 6 to 10. Therefore, the first classification characteristic is the number of vertices and all the images of geometric figures organise a

![](img/d6ed6c69a61b1252a9084096bb4904c6_177_0.png)
