
These methods are also parameterized using references to the corresponding publications.

## 3. Case Study

Two co-registered L-band UAVSAR full polarimetric images are utilized to assess the performance of the proposed method. These two images belong to the city of Los Angeles, California, acquired on 23 April 2009 and 11 May 2015, by the Jet Propulsion Laboratory/National Aeronautics and Space Administration UAVSAR. There are 786 × 300 pixels in the first dataset and 766 × 300 pixels in the second dataset. Figure 6a,b,d,e shows the RGB (Red: |HH–VV|; Green: 2|HV|; Blue: |HH+VV|) Pauli images of the two subsets of the PolSAR scenes. The GT images connected with these subsets, shown in Figure 6c,f, were prepared for the numerical analysis of CD results by using Google Earth images. Actually, the image of GT is a binary image in which the black pixels are no-change and the white pixels are change. The first and second datasets are called dataset#1 and dataset#2, respectively.

![](img/828a5d28a36454f7b3332df93f35492f_181_0.png)

![](img/828a5d28a36454f7b3332df93f35492f_181_1.png)

![](img/828a5d28a36454f7b3332df93f35492f_181_2.png)

![](img/828a5d28a36454f7b3332df93f35492f_181_3.png)

![](img/828a5d28a36454f7b3332df93f35492f_181_4.png)

![](img/828a5d28a36454f7b3332df93f35492f_181_5.png)

Figure 6. Pauli decomposition of UAVSAR images taken over Los Angeles, California on (a,d) 23 April 2009; (b,e) 11 May 2015; (c,f) ground truths, where white means change area and black means no-change area. Top: dataset#1. Bottom: dataset#2.

## 4. Experimental Results and Analysis

### 4.1. Parameter Setting

In NR_ELM and CWNN, parameters are neighborhood size r = 3 × 3 and patch size w = 7, respectively. The PCANet parameters are the image patch size k = 5, the number of filters L1 = L2 = 8 and training samples 30% of the total data. In PCA_kmeans, patch size h = 5 is used. In Gabor feature extraction, the orientation of Gabor kernel U = 8, the scale of Gabor kernel V = 5, the maximum frequency kmax = 2π and the spacing factor between kernels in the frequency domain f = √2 are used. To generate DDI and parallel clustering in DP_PCANet, the center bias b in the Sigmoid function b = 0.1 and the number of pooled images that are accumulated to generate the DDI, T = 7 are used. For TCD-Net, Table 2 lists the details of the configuration settings for each channel. Additionally, Table 3 shows the total number of filters in each multi-scale block. The model parameters are trained based on the mini-batch back-propagation algorithm with a size of 150. The error is minimized in 250 epochs and is calculated based on the determined objective function and then the parameters are updated. Adam optimizer, with an initial learning rate of 1 × 10⁻³ and an epsilon value of 1 × 10⁻¹⁰, is used as the optimization algorithm.

Table 2. TCD-Net configurations of each channel and block.

|  | Channel 1 | Channel 2 | Channel 3 |
|---|---|---|---|
| Inputs (shape) | 11 × 11 × 4 | 11 × 11 × 4 | 11 × 11 × 4 |
| Block 1 | Multi-Scale Shallow Block:<br>1 × 1 Conv1 + BN + RELU(NoF₁¹)<br>3 × 3 Conv2 + BN + RELU(NoF₂¹)<br>5 × 5 Conv3 + BN + RELU(NoF₃¹)<br>Channel Concat.<br>3 × 3 Conv4 + BN + RELU(256) | Multi-Scale Shallow Block:<br>1 × 1 Conv1 + BN + RELU(NoF₁¹)<br>3 × 3 Conv2 + BN + RELU(NoF₂¹)<br>5 × 5 Conv3 + BN + RELU(NoF₃¹)<br>Channel Concat.<br>3 × 3 Conv4 + BN + RELU(256) | Multi-Scale Shallow Block:<br>1 × 1 Conv1 + BN + RELU(NoF₁¹)<br>3 × 3 Conv2 + BN + RELU(NoF₂¹)<br>5 × 5 Conv3 + BN + RELU(NoF₃¹)<br>Channel Concat.<br>3 × 3 Conv4 + BN + RELU(256) |
| Output | 2 × 2 Max-Pooling<br>7 × 7 × 256 | 2 × 2 Max-Pooling<br>7 × 7 × 256 | 2 × 2 Max-Pooling<br>7 × 7 × 256 |
| Block 2 | Multi-Scale Residual Block:<br>1 × 1 Conv1 + BN + RELU(NoF₁²)<br>3 × 3 Conv2 + BN + RELU(NoF₂²)<br>5 × 5 Conv3 + BN + RELU(NoF₃²)<br>Channel Concat.<br>3 × 3 Conv4 + BN + RELU(256) | Multi-Scale Residual Block:<br>1 × 1 Conv1 + BN + RELU(NoF₁²)<br>3 × 3 Conv2 + BN + RELU(NoF₂²)<br>5 × 5 Conv3 + BN + RELU(NoF₃²)<br>Channel Concat.<br>3 × 3 Conv4 + BN + RELU(256) | Multi-Scale Residual Block:<br>1 × 1 Conv1 + BN + RELU(NoF₁²)<br>3 × 3 Conv2 + BN + RELU(NoF₂²)<br>5 × 5 Conv3 + BN + RELU(NoF₃²)<br>Channel Concat.<br>3 × 3 Conv4 + BN + RELU(256) |
| Output | 7 × 7 × 256 | 7 × 7 × 256 | 7 × 7 × 256 |
| Block 3 | Multi-Scale Residual Block:<br>1 × 1 Conv1 + BN + RELU(NoF₁³)<br>3 × 3 Conv2 + BN + RELU(NoF₂³)<br>5 × 5 Conv3 + BN + RELU(NoF₃³)<br>Channel Concat.<br>3 × 3 Conv4 + BN + RELU(256)<br>2 × 2 Max-Pooling | Multi-Scale Residual Block:<br>1 × 1 Conv1 + BN + RELU(NoF₁³)<br>3 × 3 Conv2 + BN + RELU(NoF₂³)<br>5 × 5 Conv3 + BN + RELU(NoF₃³)<br>Channel Concat.<br>3 × 3 Conv4 + BN + RELU(256)<br>2 × 2 Max-Pooling | Multi-Scale Residual Block:<br>1 × 1 Conv1 + BN + RELU(NoF₁³)<br>3 × 3 Conv2 + BN + RELU(NoF₂³)<br>5 × 5 Conv3 + BN + RELU(NoF₃³)<br>Channel Concat.<br>3 × 3 Conv4 + BN + RELU(256)<br>2 × 2 Max-Pooling |
| Output | 5 × 5 × 256 | 5 × 5 × 256 | 5 × 5 × 256 |
| Block 4 | Multi-Scale Residual Block:<br>1 × 1 Conv1 + BN + RELU(NoF₁⁴)<br>3 × 3 Conv2 + BN + RELU(NoF₂⁴)<br>5 × 5 Conv3 + BN + RELU(NoF₃⁴)<br>Channel Concat.<br>3 × 3 Conv4 + BN + RELU(256) |  | Multi-Scale Residual Block:<br>1 × 1 Conv1 + BN + RELU(NoF₁⁴)<br>3 × 3 Conv2 + BN + RELU(NoF₂⁴)<br>5 × 5 Conv3 + BN + RELU(NoF₃⁴)<br>Channel Concat.<br>3 × 3 Conv4 + BN + RELU(256) |
| Output | 5 × 5 × 256 |  | 5 × 5 × 256 |
| Classifier | Flatten<br>RELU<br>Fully Connected (350)<br>Softmax<br>Fully Connected (2) |  |  |

NoF_k^{ij} is the number of filters for k^{th} convolutional layer of multi-scale block in i^{th} channel of j^{th} block.

Table 3. The total number of filters in each multi-scale block.

| Block | Channel 1 | Channel 2 | Channel 3 |
|---|---|---|---|
| 1 | NoF₁¹¹ + NoF₂¹¹ + NoF₃¹¹ = 16 | NoF₁²¹ + NoF₂²¹ + NoF₃²¹ = 64 | NoF₁³¹ + NoF₂³¹ + NoF₃³¹ = 16 |
| 2 | NoF₁¹² + NoF₂¹² + NoF₃¹² = 32 | NoF₁²² + NoF₂²² + NoF₃²² = 128 | NoF₁³² + NoF₂³² + NoF₃³² = 32 |
| 3 | NoF₁¹³ + NoF₂¹³ + NoF₃¹³ = 64 | NoF₁²³ + NoF₂²³ + NoF₃²³ = 256 | NoF₁³³ + NoF₂³³ + NoF₃³³ = 64 |
| 4 | NoF₁¹⁴ + NoF₂¹⁴ + NoF₃¹⁴ = 128 | NoF₁²⁴ + NoF₂²⁴ + NoF₃²⁴ = 256 | NoF₁³⁴ + NoF₂³⁴ + NoF₃³⁴ = 128 |

### 4.2. Pseudo-Label Training Sample Generation

As previously mentioned, we first use the pre-trained model introduced in [2]. Based on Table 4, which shows the results of the CD framework proposed in [2] for our case study, it can be seen that this model is not robust for all case studies. On the other hand, the performance of this model is dependent on the objects of the study area. For this reason, we generate PCHM using the pre-trained model. Then, by applying a reliable threshold, we extract the pixels that most likely belong to the change and no-change classes. Quantitative results show that this increases the performance significantly. In addition, we obtain PCHM with the FCM clustering. Finally, we extract the pixels that have been identified in both algorithms as change and no-change pixels. The quantitative results show that the aggregation of these two algorithms greatly increases accuracy. For dataset#1, the OA and KC in the FCM clustering is 94.10% and 0.66, in the TL-based classification is 93.85% and 0.75 and in the aggregation is 97.58% and 0.84. For dataset#2, the OA and KC in the FCM clustering is 95.84% and 0.52, in the TL-based classification is 97.64% and 0.82, and in the aggregation of these two methods is 99.52% and 0.91. Therefore, the quantitative results show that the aggregation of these two methods improves the pseudo-label generation accuracy. We considered 5% of the total data as the reference data and divided the reference data into 65% for training, 15% for validation, and 20% for testing (Table 5).

Table 4. The accuracy of the CD framework proposed in [2] for dataset#1 and dataset#2.

| Method | TN | TP | FP | FN | TPR (%) | FPR (%) | FNR (%) | Precision | OA (%) | F1-Score | DR (%) | KC | OER (%) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| [2] dataset#1 | 187,570 | 27,606 | 11,581 | 9043 | 75.33 | 5.82 | 24.67 | 70.45 | 91.25 | 72.86 | 74.02 | 0.68 | 8.76 |
| [2] dataset#2 | 202,423 | 10,710 | 4188 | 12,479 | 46.19 | 2.03 | 53.81 | 71.89 | 92.75 | 56.24 | 29.22 | 0.52 | 7.25 |

Table 5. The number of change and no-change pixels extracted from the parallel pseudo-label generation framework and the number of training, testing and validation pixels used in the training process of TCD-Net.

| Dataset | Class | Total Number of Pixels | Number of Samples | Valid Percentage (%) | Training | Validation | Testing |
|---|---|---|---|---|---|---|---|
| dataset#1 | change | 36,649 | 12,717 | 34.70 | 1191 | 357 | 366 |
| dataset#1 | no-change | 199,151 | 165,308 | 83.01 | 6472 | 1493 | 1991 |
| dataset#2 | change | 23,189 | 11,156 | 48.11 | 753 | 173 | 231 |
| dataset#2 | no-change | 206,611 | 81,650 | 39.52 | 6714 | 1549 | 2066 |

### 4.3. Comparison of Results for Dataset#1

Figure 7 illustrates the result of CD for dataset#1. As seen, Figure 7a,c,d show the results of CD for PCA_kmeans, Gabor_PCANet and DP_PCANet that have many noisy pixels, while other methods provide the low noisy pixels. Furthermore, the NR_ELM, Figure 7b and CWNN, Figure 7e, have miss detection pixels that are evident in the top and bottom of the study areas (red circles). In Figure 7, the red circles show the no-change pixels that have
