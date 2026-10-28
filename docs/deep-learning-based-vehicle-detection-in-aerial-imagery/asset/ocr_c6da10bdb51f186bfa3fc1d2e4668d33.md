The detection results of the proposed semantic labeling based filtering, the IMT Faster R-CNN and the EMT-Faster R-CNN are given in Table 6.12. To account for the smaller object dimensions in case of DLR 3K, the output of conv3_3 is used as feature map instead of conv4_3. Hence, the feature map resolution is increased as required for accurately localizing tiny objects. Furthermore, the anchor base is set to 2 and the anchor scales are set to 7, 14, and 21 analogous to Section 5.2.2. For the semantic labeling based filtering, FCN-D16 is used to generate semantic labeling masks and eq. (6.1) is used as filter criterion. For the EMT Faster R-CNN, the outputs of conv4_3 and conv5_3 of the semantic labeling branch are employed as auxiliary feature maps for the classification stage and RoI pooling layers are added to extract the corresponding features for each candidate region. The extracted features of the semantic labeling branch and conv3_3 are combined via element-wise addition. The further settings are adopted from Section 6.2.2 and Section 6.2.3, respectively. Image patches of size 936 × 936 are used for training and evaluation. Furthermore, data augmentation is conducted during training by applying vertical and horizontal flipping as well as rotation in steps of 90 degrees.

# Table 6.12: Average precision of Faster R-CNN with and without semantic labeling based filtering, IMT Faster R-CNN and EMT Faster R-CNN on DLR 3K.

| Approach | AP (in %) |
|---|---|
| Faster R-CNN | 95.0 |
| Faster R-CNN + Semantic Filtering | 95.2 |
| IMT Faster R-CNN | 95.8 |
| EMT Faster R-CNN | 96.2 |

The semantic labeling based filtering, the IMT Faster R-CNN and the EMT-Faster R-CNN outperform the baseline Faster R-CNN. Note that the AP of the baseline Faster R-CNN is higher compared to the AP reported in Table 5.2 due to the performed data augmentation. The gain in AP achieved for semantic labeling based filtering is only 0.2% though the employed FCN-D16, which is trained accordingly to Section 6.2.2, exhibits good semantic labeling results (see Table 6.13). While the overall accuracy and the F1-scores for categories