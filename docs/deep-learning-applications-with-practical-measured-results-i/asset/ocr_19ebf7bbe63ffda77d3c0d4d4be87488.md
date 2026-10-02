![](bbox=[0.3, 0.16, 0.68, 0.33])

Figure 12. The separation of cylinders into individual point clouds.

After the separation, each individual point cloud is processed by our developed algorithm in order to fit the circle centers. The calculated centers are exactly the same with the generated ones. Figure 13 makes a plot of the calculated centers of the synthetic data generated for algorithm validation.

![](bbox=[0.33, 0.46, 0.68, 0.63])

Figure 13. Plots of the calculated centers of the generated data.

The results indicate that the algorithm developed in this work for the determination of the centers of cylinder point cloud is valid.

# 5.2. Validation of the Algorithm for Determination of Coefficients

Here, we use two methods for the validation of the algorithm for the determination of the coefficients.

The first method is to create a dataset containing points with intervals of 125 μm as certified positions, while making a little displacement with each point. Calculate the correction coefficients and correct the points with the displacement using the algorithm defined in Section 4.2. The points with the displacement with respect to the certified points represent the measured points in the experiments. Therefore, two residuals can be obtained, i.e., the residual between the certified points and the points with displacement as well as the residual between the certified points and the corrected points. Compare those two residuals to check whether the correction is meaningful.

The algorithm first creates the two data described above. Then it rotates the points with displacement to the certified points, aiming at making the axis parallel. This arises from the methodology of this work, which requires locating the standard artefact that is parallel with the axis. As it is impossible