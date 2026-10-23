medium ships (1024 < Area_OBBs < 9216 pixels), and large ships (Area_OBBs > 9216 pixels) in the RSSD are 13,369, 7741, and 369, respectively, (62.24%, 36.04%, and 1.72% of all ships, respectively), while in the SSDD, the proportions are 71.12%, 28.30%, and 0.58%, respectively. Ships in both datasets are relatively small in size but have large variations in scale. As shown in Figure 17d,h, the angle distribution of ship ground truths in the RSSD is more balanced than that in the SSDD. This ensures that rotation detectors learn the multi-angle features better.

![](bbox=[0.05, 0.28, 0.95, 0.6])

Figure 17. Statistical comparison between the proposed RSSD and the SSDD. Here, (a) and (e) show the width and height distribution of ship ground truths in RSSD and SSDD, respectively; (b) and (f) display the aspect ratio distribution of ship OBBs; (c) and (g) indicate the area distribution of ship OBBs; (d) and (h) show the rotation angle distribution of ship OBBs.

Table 3. Details of dataset division.

| Dataset | Train | Test | All | Inshore (Test) | Offshore (Test) |
|---|---|---|---|---|---|
| RSSD (ours) | 5692 | 2321 | 8013 | 479 | 1842 |
| SSDD | 928 | 232 | 1160 | 46 | 186 |
| HRSC2016 | 617 | 444 | 1061 | – | – |

Based on the above analysis, it is obvious that the ship targets in our RSSD not only differ significantly in orientation degrees but also have multi-scale characteristics, which provides a challenging benchmark for arbitrary-oriented ship detection in SAR images.

# 6. Experiments and Discussion

In this section, we first present the benchmark datasets, implementation details, and evaluation metrics. Then, extensive comparative experiments with existing methods are carried out to verify the superiority and robustness of our approach. Meanwhile, comprehensive discussions are provided to analyze and interpret the experimental results.

# 6.1. Benchmark Datasets and Implementation Details

The proposed rotated-SARShip dataset (RSSD) and the public SAR ship detection dataset (SSDD), specific information about which is provided in Section 5, are used to evaluate the performance of the proposed method. In our experiments, all SSDD images are resized to 512 × 512 pixels, with padding operation to avoid distortion, while the RSSD images of 800 × 800 pixels are directly used as the network input. The ratio of training set to test set for the RSSD is set to 7:3, while that for the SSDD is set to 8:2. To better assess the