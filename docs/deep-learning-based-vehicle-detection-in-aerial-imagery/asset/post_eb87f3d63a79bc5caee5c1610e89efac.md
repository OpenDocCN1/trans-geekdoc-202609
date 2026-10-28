
eq. (6.1) are used to filter the region proposals. The detection performance is clearly improved for all GSDs, whereby the gain in AP increases with higher GSDs even though the semantic labeling accuracy gets worse for higher GSDs. This indicates that the importance of employing semantic context information increases with higher GSDs and consequently smaller object dimensions.

![](img/99de1214c29cbc525a14b293385af5cf_132_0.png)

Figure 6.12: Qualitative detection examples before (top row) and after (bottom row) filtering the region proposals using the semantic labeling mask outputted by FCN-D16 indicate that false alarms located on regions that are unlikely to contain vehicles, e.g., windows on buildings, are removed.

Table 6.7: Average precision (in %) of Faster R-CNN with and without semantic labeling based filtering using FCN-D16 on the Potsdam dataset for different GSDs.

| Filter Criterion | GSD (in cm)<br>5 | GSD (in cm)<br>10 | GSD (in cm)<br>15 | GSD (in cm)<br>20 | GSD (in cm)<br>25 |
| --- | --- | --- | --- | --- | --- |
| - | 92.9 | 92.2 | 90.1 | 82.7 | 62.9 |
| eq. (6.1) | 93.9 | 93.3 | 91.7 | 85.8 | 70.7 |

## 6.2.3 Joint Semantic Labeling and Detection

### Implicit Multi-Task Faster R-CNN

The first variant, which is in the following referred to as Implicit Multi-Task (IMT) Faster R-CNN, is depicted in Figure 6.13. The proposed architecture comprises two branches: one for detection (top branch) and one for semantic labeling (bottom branch). The detection branch includes the RPN and the classification stage, while FCN-D16 is exemplarily employed for the semantic labeling branch. Note that the semantic labeling network can be replaced by the alternative architectures described in Section 6.2.1. Both branches are merged by sharing the first four sequences of convolutional layers. The prerequisite for this is that both branches are based on the same base architecture, i.e., VGG16. This allows the network to learn a shared global feature map, i.e., conv4_3, through which the semantic labeling branch implicitly affects the detection branch. As the semantic labeling branch is only required for training, it can be discarded during deployment.

To allow end-to-end training of both tasks, a joint multi-task loss $L_{MT}$ comprised of five losses is proposed:

$$L_{MT} = \lambda_1L_{SL} + \lambda_2L_{RPN,cls} + \lambda_3L_{RPN,reg} + \lambda_4L_{CLS,cls} + \lambda_5L_{CLS,reg}. \tag{6.2}$$

For this purpose, the output of *conv4_3* of the semantic labeling branch is employed as auxiliary feature map for the classification stage. The set of generated region proposals is projected onto the auxiliary feature map as well and an additional RoI pooling layer extracts the corresponding features. The output of the additional RoI pooling layer has the same dimensions, i.e., 7 × 7, and number of channels, i.e., 512, as the output of the RoI pooling layer of the detection branch. The outputs of both RoI pooling layers are fused via element-wise addition. The fused features are then fed into the sequence of fully connected layers of the classification stage. Outputs of deeper convolutional layers of the semantic labeling branch are not considered as feature map because the number of output channels exceeds 512 as required for the element-wise addition. The EMT Faster R-CNN is trained analogously to the IMT Faster R-CNN using the joint multi-task loss given in eq. (6.2). Thus, semantic context information is induced twofold: implicitly by shared convolutional layers and joint learning and explicitly by exploiting features of the semantic labeling branch for the classification stage.

### Ablation Experiments

In the following, the impact of both variants to induce scene knowledge into the detection framework are evaluated. For this, each model is trained end-to-end for 70,000 iterations with an initial learning rate of 0.001. VGG16 pre-trained on ImageNet is used to initialize the weights of the shared convolutions as well as the weights of both branches. Note that data augmentation, which results in better semantic labeling results [She16], is performed through applying vertical and horizontal flipping as well as rotation in steps of 90 degrees. To account for the characteristics of the Potsdam dataset, the settings introduced in Section 6.2.2 are adopted, i.e., exploitation of *conv4_3* as feature map, setting the anchor base to 4 and the anchor scales to 8, 16, and 24, and forwarding of the top-100 ranked region proposals after NMS to the classification stage.

![](img/99de1214c29cbc525a14b293385af5cf_136_0.png)

Figure 6.14: Schematic illustration of the proposed Explicit Multi-Task Faster R-CNN. In addition to the shared sequences of convolutional layers, features from the semantic labeling branch are explicitly added for each region proposal by way of an additional RoI pooling layer and element-wise addition.

Table 6.8: Detection results for IMT Faster R-CNN and EMT Faster R-CNN with different architectures employed as semantic labeling branch on the Potsdam dataset.

| Semantic Labeling Architecture | IMT Faster R-CNN | EMT Faster R-CNN |
| --- | --- | --- |
| - | 95.7 | 95.7 |
| FCN-32s | 96.3 | 96.6 |
| FCN-16s | 95.7 | 96.4 |
| FCN-D16 | 96.1 | 96.8 |
| SegNet | 96.1 | 96.3 |

Table 6.8 shows the detection accuracy for the IMT Faster R-CNN and EMT Faster R-CNN with different semantic labeling architectures employed as semantic labeling branch. The best detection accuracy for IMT Faster R-CNN is achieved by employing FCN-32s as semantic labeling architecture, which slightly outperforms FCN-D16 and SegNet. The IMT Faster R-CNN exhibits an improved AP compared to the baseline Faster R-CNN except for using FCN-16s as semantic labeling architecture, which indicates that implicitly inducing scene knowledge by sharing features results in improved detection accuracy. Note that the baseline Faster R-CNN is trained on augmented data as well. Thus, the achieved AP is higher compared to the AP reported in Table 6.4. One reason for the absent gain in AP in case of FCN-16s may be the training procedure as no staged training as proposed in [Lon15] is performed. In [Som17a], notably worse semantic labeling results are achieved on the Potsdam dataset by training FCN-16s at once compared to FCN-32s. EMT Faster R-CNN shows better detection results for all semantic labeling architectures compared to its IMT Faster R-CNN counterparts and clearly improved detection results compared to the baseline Faster R-CNN. Hence, explicitly adding features from the semantic labeling branch and consequently more semantic context information boosts the detection accuracy. Overall, the best AP is achieved for FCN-D16, which outperforms the baseline Faster R-CNN by 1.1% in AP.

Table 6.9: Impact of varying the weighting factor λ₁ of the semantic labeling loss exemplarily for EMT Faster R-CNN with FCN-D16.

| Weighting factor λ₁ | AP (in %) |
| --- | --- |
| 1 | 96.5 |
| 2 | 96.5 |
| 3 | 96.7 |
| 4 | **96.8** |

The impact of varying the weight ratio between the semantic labeling loss and the detection loss is given in Table 6.9 exemplarily for EMT Faster R-CNN using FCN-D16 for the semantic labeling branch. For this, the weighting factor λ₁ of the semantic labeling loss (see eq. (6.2)) is varied in the range between 1 and 4, while all other weighting factors are kept fixed at 1. Weighting all losses equally (λ₁ = 1) results in the lowest AP, while the best AP is achieved
