# 3.4.2. Tracking Stability

The central location error (CLE) reflects the stability of the tracking method [15]; i.e., the smaller the CLE, the more stable the tracking method, and the CLE is defined as follows:

CLE = sqrt((x_R - x_G)^2 + (y_R - y_G)^2) (10)

where (x_R, y_R) represents the central location of the tracking result, and (x_G, y_G) represents the central location of the shadow’s ground truth.

# 3.4.3. Tracking Speed

The frames per second (FPS) represent the tracking speed, which is defined as follows:

FPS = N / t (11)

where t represents the total tracking time, and N is the number of images in the Video-SAR sequence.

# 4. Results

# 4.1. Results of the Simulated Video-SAR Data

Figure 12 shows the tracking results of the simulated Video-SAR data. In the rest of this paper, the red box represents the tracking results, and the green box represents the ground truths of the shadow. It can be seen that the red and green boxes have a great overlap, which means that GASN can track the target effectively.

![](bbox=[0.1, 0.48, 0.25, 0.68])

![](bbox=[0.28, 0.48, 0.43, 0.68])

![](bbox=[0.48, 0.48, 0.63, 0.68])

![](bbox=[0.68, 0.48, 0.83, 0.68])

Figure 12. Tracking results of the simulated Video-SAR data: (a) 9th frame in Video 2; (b) 14th frame in Video 2; (c) 37th frame in Video 2; (d) 56th frame in Video 2.

We quantitatively analyzed the tracking results of GASN. Because Siamese-FC and Siamese-RPN significantly outperform MOSSE [19] and KCF [20], only the visual comparison results of GASN with Siamese-RPN and Siamese-FC in terms of accuracy, CLE, and FPS indicators are shown.

# 4.1.1. Comparison with Other Tracking Methods

Figures 13–15 show the results of comparing GASN to Siamese-RPN and Siamese-FC on the six test videos. In the comparative experiments, we retrained Siamese-FC and Siamese-RPN using the same simulated data, and both networks were tuned. Moreover, to ensure the rationality of the experiments, our comparative experiments were all performed under the same conditions, such as the data preprocessing, the hard and soft platforms, and the training mechanism. From the results, we can see that GASN (marked with purple) obtained the highest mIoU (Figure 13) and the lowest CLE (Figure 14) on each video. Moreover, the FPS (Figure 15) of GASN (marked with purple) was almost the same as that of Siamese-RPN (marked with green), which indicates that GASN has almost no speed loss at a higher accuracy. Due to the above phenomenon also applying to real data, we