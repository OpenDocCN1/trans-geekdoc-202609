data is indicated in bold. All of the resolution parameter combinations include (1/4, 1/16), (1/2, 1/8), (1, 1/8), and (1/2, 1/5).

Table 3. RMSE and NCM of the different resolution settings on the datasets.

| Pair | Ours_16_4 RMSE | Ours_16_4 NCM | Ours_8_2 RMSE | Ours_8_2 NCM | Ours_8_1 RMSE | Ours_8_1 NCM | Ours_5_2 RMSE | Ours_5_2 NCM |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 1 | 0.683 | 323 | 0.638 | 3789 | 0.665 | 3885 | **0.572** | **8506** |
| 2 | 0.680 | 68 | 0.669 | 533 | 0.680 | 763 | **0.569** | **1763** |
| 3 | 0.703 | 95 | 0.627 | 1012 | 0.673 | 895 | **0.609** | **2410** |
| 4 | 0.676 | 261 | 0.637 | 1288 | 0.671 | 1706 | **0.528** | **6923** |
| 5 | 0.638 | 29 | **0.624** | 149 | 0.636 | 157 | 0.661 | **223** |
| 6 | **0.504** | 26 | 0.618 | 328 | 0.653 | 487 | 0.571 | **758** |
| 7 | 0.685 | 1389 | 0.624 | 8925 | 0.593 | 12,152 | **0.546** | **12,190** |
| 8 | 0.646 | 222 | 0.634 | 2165 | 0.643 | 1955 | **0.484** | **3121** |
| 9 | 0.680 | 658 | 0.641 | 6253 | 0.633 | 7568 | **0.503** | **20,319** |
| 10 | 0.658 | 819 | 0.644 | 2104 | 0.624 | 3348 | **0.485** | **18,270** |
| 11 | 0.659 | 986 | 0.646 | 3025 | 0.642 | 4731 | **0.518** | **23,865** |
| 12 | 0.642 | 1336 | 0.635 | 9616 | 0.612 | 11,253 | **0.537** | **24,515** |
| 13 | 0.636 | 1187 | 0.631 | 4382 | 0.639 | 4906 | **0.560** | **21,782** |
| 14 | 0.638 | 61 | 0.620 | 558 | 0.668 | 603 | **0.538** | **949** |
| 15 | 0.690 | 558 | 0.709 | 1203 | **0.667** | 2478 | 0.696 | **4099** |
| 16 | 0.711 | 195 | 0.643 | 1679 | 0.648 | 2063 | **0.555** | **4401** |
| 17 | 0.654 | 850 | 0.621 | 3339 | 0.668 | 3719 | **0.577** | **14,446** |

It can be seen from Table 3 that, for the datasets, the resolution of (1/2,1/5) has the best performance. It is shown in Table 3 that the size of the low resolution directly affects the overall matched point’s number. It can be found intuitively that the total potential points of resolution 1/16 are a quarter of 1/8’s point number (1/2 × 1/2 = 1/4). As such, configuration (1/2,1/5) can obtain more matched point pairs. Take configurations (1/2,1/8) and (1,1/8) for an example; for high-resolution feature maps, the number of matched points increases to a certain extent with the increase of the resolution. However, here, the GPU memory requested by configuration (1,1/5) exceeds the upper limit of the machine used in this work, so we chose a compromise configuration, (1/2,1/5).

# 4. Discussion

The experimental results corroborate the accuracy and robustness of our method. There are three main reasons for this: First, the features extracted based on Transformer are richer, including the local gray information of the image itself, and global information such as the context. Second, the down-sampled image has stronger semantic information, and is suitable for traditional registration methods. The subsequent registration is provided with a better initial result of coarse matching. Third, according to the K-means++ clustering method, the relationship between the original image and the sub-images to be registered is constructed, and representative sub-images are obtained in order to reduce time and space consumption.

From the performance analysis and model hyperparameter comparison experiments, it can be seen that our proposed method achieved stable and accurate matching results under different ground object scenes and various sensors’ data conditions. Now, we will further examine the rotation, scaling and noise robustness of the proposed method. Furthermore,