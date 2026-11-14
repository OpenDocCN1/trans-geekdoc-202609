

| benchmark | WiSPPN | PIW | Wi-Mose | EASFN |
|---|---|---|---|---|
| SPE | 21.86% | 32.96% | 33.13% | **50.05%** |
| GPE | × | 27.64% | × | **43.98%** |

conduct multi-person joint association given JHMs and PAFs. The output tensor is \(p \times 18 \times 3\), where \(p\) represents the number of persons that the networks detected, \(18 \times 3\) denotes the x-axis, y-axis, and confidences of 18 body joints.

For the evaluation metric, Percentage of Correct Keypoints (PCK) is a widely-used metric for evaluating the performance of pose estimation, which measures the probability that a model correctly predicts the location of human joints within a tolerated error. Since the human body size varies in video frames due to displacement, the tolerated error should change with different human body sizes. Therefore, we take the distance from the right shoulder to the left hip as torso length and also correlate tolerated error with torso length using \(\alpha\) as follows.

\(PCK@\alpha = \frac{1}{N} \sum_{n}^{N} \Phi(\frac{\|\hat{P}_{(i,n)} - P_{(i,n)}\|_2}{\|P_{(5,n)} - P_{(8,n)}\|_2})\) (6)

\(\Phi(x) = \begin{cases} 1, & \text{if } x < \alpha \% \\ 0, & \text{otherwise,} \end{cases}\) (7)

where \(i\) denotes the index of human joints, i.e., \(i \in \{1,2,\dots,18\}\) for the COCO\_18 model in OpenPose [20] and \(N\) represents the number of people in the test frames; \(P_{(i,n)}\) and \(\hat{P}_{(i,n)}\) refer to the coordinates of \(i\)-th joints of \(n\)-th person obtained from ground truth and prediction, respectively; \(\|P_{(5,n)} - P_{(8,n)}\|_2\) is torso length since the index of right shoulder and left hip are 5 and 8. We compare our method with other methods with different \(\alpha\), i.e., \(\alpha\) is set from 10 to 50. Note that PIW normalizes the error by a fraction of the bounding box size instead of torso length, and thus the PCK value reported in our work is greater.

Our train-test split strategy follows PIW, by taking the first 80% of samples for training, and the last 20% for testing.

### 5.2. Quantitative results

We compare our approach with two state-of-the-art methods for WiFi-based 2D human pose estimation. The first is WiSPPN [11], which is an end-to-end CNN network supervised by a joint coordinate adjacency matrix. The second is PIW [12], which leverages a well-developed CNN to map Wifi signals into three supervision components: SM, JHMs, and PAFs. The third is Wi-Mose [32], which fuses the amplitude and phase of CSI signals into CSI images and uses a neural network to extract features from them.

Table 1 compares EASFN with WiSPPN and PIW in terms of PCK@20. Please note that WiSPPN can only estimate poses in single-person scenes due to the limitation of the fixed dimension (\(18 \times 18 \times 3\)) of the supervision matrix. Therefore, we only train and test WiSPPN on the SPE dataset. The results show that our model outperforms other two approaches in both scenarios. In terms of PCK@20, our model outperforms WiSPPN and PIW on the SPE dataset by 28% and 17%, respectively. On the GPE dataset, the proposed EASFN outperforms PIW by 16% in terms of PCK@20. This improvement is attributed to our spatial-frequency encoder, which captures the temporal relationship between consecutive CSI signals by multiple frequency encoders of different kernel sizes while previous works ignore such temporal information. For instance, Wi-Mose treats consecutive CSI signals as images and uses kernels of the small receptive field (\(3 \times 3\)) to extract features, which performs poorly at capturing long-term patterns. Also, WiSPPN and PIW simply aggregate both subcarriers and consecutive samples by channel dimension of convolutional layers, which loses the sequential relationship. Therefore, without long-term consecutive information, previous works perform inferior to EASFN. The PCK curves of all approaches are provided in Fig. 2, which illustrates that EASFN outperforms other methods by a large margin with respect to all PCK thresholds.

![](img/efd360d946b871d0c04d9f4466e6ac53_4_0.png)

Fig. 2. PCK curve of three models evaluated on SPE benchmark.

| Action | WiSPPN | PIW | Wi-Mose | EASFN |
|---|---|---|---|---|
| Walking | 23.58% | 39.87% | 42.97% | **61.14%** |
| Waving | 25.92% | 33.06% | 33.49% | **45.81%** |
| Running | 22.12% | 37.91% | 35.71% | **58.11%** |
| Jumping | 15.82% | 20.99% | 21.97% | **35.15%** |

### 5.3. Detailed analysis on each action

We further investigate the performance of our model with other methods with different human actions on the SPE dataset. Table 2 presents the comparative results, revealing the advantage of EASFN for predicting moving subjects. Specifically, for the actions of Walking and Running, EASFN significantly improves the baselines, i.e., by about 21% over PIW and 37% over WiSPPN, because the frequency features are sensitive to moving subjects, while the evolving attention module adaptively adjusts the weights of each channel to focus on specific frequency features. The lowest improvement is in the cases of waving, i.e., only 12% over PIW and 20% over WiSPPN. This is because volunteers only wave their hands or arms while keeping their torso static, and the performance on static keypoints is similar for the different methods.

From Table 2, we can also observe that EASFN achieves the worst result when handling the pose of jumping. Accurately estimating the human pose of jumping is an arduous task. It requires fine time granularity to capture the thin and fast-moving limbs. Specifically, jumping can be regarded as high-speed waving, and therefore using CSI sampled at the same time granularity to estimate the movement of higher speed would lead to a performance drop. In that case, one possible solution to improve EASFN's ability to handle jumping is to increase the sampling rate of CSI samples, which can refine the time granularity of data. To investigate the relation between the sampling rate of CSI and pose estimation result, we need to collect a larger dataset including multiple sampling rates, which is left as our future work.

Table 3 Ablation study on our SPE benchmark.

| Combination | SFE | AM | EM | d | PCK@20 |
|---|---|---|---|---|---|
| Baseline | - | - | - | - | 35.13% |
| C1 | ✓ | - | - | - | 44.99% |
| C2 | - | ✓ | - | - | 45.95% |
| C3 | - | - | ✓ | 1 | 48.08% |
| **C4** | - | - | ✓ | **3** | **50.05%** |
| C5 | - | - | ✓ | 5 | 47.95% |

### 5.4. Ablation study

To demonstrate the advantage of each component in EASFN, we conduct an ablation study on the SPE dataset. Five combinations are conducted for comparison. (Baseline): taking the ResNet as feature encoder same as PIW and WiSPPN; (C1): using spatial-frequency encoder; (C2): applying the static attention module; (C3-C5): proposed EASFN with different dilated rates.

Table 3 shows the results of different models in terms of PCK@20, which verifies our assumptions. First of all, the baseline has better performance than PIW, demonstrating that U-Net is not suitable for Wifi signal and thus leads to worse performance. In contrast, C1 outperforms the baseline by a large margin since the spatial-frequency encoder is designed for Wifi and can extract both the spatial semantic information of the environment and human movement information. Moreover, the attention mechanism (C2) is beneficial for pose estimation by focusing on certain channels. However, if the attention masks are derived simply from single frame-level features, the performance only slightly increases by around 1% in terms of PCK@20. On the other hand, the proposed evolving attention module (C3-C5) can increase the performance at least by 2%. The different outcomes between C3 and C4 imply that increasing the receptive field across time can improve performance by around 2%. Nevertheless, a comparison of the results of C4 and C5 shows that if the receptive field is too large across time, it can deteriorate the performance. This is why we take EASFN with d=3 as the proposed method.

![](img/efd360d946b871d0c04d9f4466e6ac53_5_0.png)

Fig. 3. Comparative visualization of EASFN and other methods.

Table 4 Comparative results under through-wall and low-light scenarios(PCK@20).

| scenario | PIW | OpenPose | EASFN |
|---|---|---|---|
| Wall | 8.92% | - | **30.45%** |
| Dark | - | 42.89% | **46.97%** |

Dominated by the through-wall degradation. From Table 4, we can observe that PIW suffers a severe performance drop under the through-wall scenario. On the flip side, though having a perceptible degradation, EASFN still remains an acceptable performance under such harsh conditions. The result indicates that EASFN is more robust compared with PIW when capturing useful information from through-wall signals.

For exhibiting the power of EASFN under low-light scenarios, we design a comparative experiment in a dark environment. We separately perform human pose estimation from CSI data via

### 5.5. Qualitative results

Fig. 3 illustrates the examples of human poses generated from CSI signals by EASFN and the other methods. We choose samples from three subjects with different actions (walking, waving, and complex stretching actions). The results show that EASFN generates more accurate poses for different actions since it effectively learns the static spatial features and dynamic frequency features across continuous frames. The other contenders can approximately detect the human torso but perform poorly at estimating joints in human arms and legs. These joints are difficult to predict because arms and legs usually have complicated actions across the time. However, with the evolving attention module, EASFN can pay more attention to the specific channels of moving arms and legs. By learning the dependency between channels across the time, EASFN estimates the joints in arms or legs accurately.

### 5.6. Through-wall and low-light scenarios

In order to demonstrate that the proposed approach offers strong advantages under specific scenarios, we conduct experiments under a through-wall and a low-light scenario. For the through-wall scenario, the transmitter is placed right outside the concrete wall of the classroom, and signals would pass through the wall, reflect off the human body, and then be received by the receiver. The task is challenging because the CSI would be

![](img/efd360d946b871d0c04d9f4466e6ac53_5_1.png)

Fig. 4. Comparison of results of EASFN and OpenPose in the dark.
