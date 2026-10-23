![](bbox=[0.13, 0.17, 0.27, 0.28])

![](bbox=[0.27, 0.17, 0.41, 0.28])

![](bbox=[0.47, 0.17, 0.61, 0.28])

![](bbox=[0.67, 0.17, 0.81, 0.28])

![](bbox=[0.25, 0.3, 0.44, 0.42])

![](bbox=[0.42, 0.3, 0.58, 0.42])

Figure 8. The SAR image datasets (a–q) of datasets 1–17.

As for our method, we set K = 4 and window size = 640 for the sub-image. SAR-SIFT and KAZE-SAR are traditional methods, and Hardnet, Tfeat, SOSNet, LoFTR, and CMM-Net are deep learning methods. The algorithm in this paper was trained and tested on a server with a GPU of NVIDIA TITAN_X (12GB), a CPU of Intel(R) Core(TM) i7-5930K @3.50GHZ, and a memory size of 128 GB. The comparison experiment was carried out using the same hardware. As will be discussed later (Section 3.4), under existing hardware conditions, (1/2,1/5) resolution was adopted in this paper in order to achieve the best effect, and was used as the final network model to calculate the speed and accuracy of the algorithm. Like diverse methods, in addition to feature point detection and feature point description, other processing steps are consistent with our method, including the rough matching of sub-sampling images and the acquisition of subimages. The other settings were based on the original settings of the algorithm in order to ensure the fairness of the comparison.

Table 2 shows the performance results of several methods on the above dataset, in which the best performance corresponding to each indicator is shown in bold. ‘-’ in the table means that the matching result of the corresponding algorithm is incorrect. It can be seen that the performance of our method on RMSE is better than the comparison methods in more than half of the datasets. For all of the SAR image registration datasets, the performance of our method reaches the sub-pixel level. Considering NCM, our method obtains the best performance for all of the total datasets, as well as a better spatial distribution of points, i.e., dense matching. Figure 9 shows that our method’s NCMs are higher than those of other methods, while the RMSEs are lower in most cases.

# 3.3. Visualization Results

In order to display the matching accuracy more intuitively, we added the checkerboard mosaic images. In Figure 10, the continuity of the lines can reflect the matching accuracy. As the pictures show, the areas and lines overlap well, indicating the high accuracy of the proposed method.