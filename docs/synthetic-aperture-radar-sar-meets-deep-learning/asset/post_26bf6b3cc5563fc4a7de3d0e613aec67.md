
mainly focuses on the lightweight design of the backbone network, for a fair comparison of performance, we cite the results of the backbone ablation experiments of AFSar [14]. The results are shown in Table 4. As seen from the table, our work not only outperformed other methods in terms of precision but also in terms of speed.

![](img/828a5d28a36454f7b3332df93f35492f_260_0.png)

Figure 6. Visualization effect of the ablation experiment. The purple box is the target that was missed when marked, the red box is the target of misdetection and the blue box is a missed target. CA = coordinate attention; PEA = position-enhanced attention.

**Table 4.** Comparison with the latest target detection methods.

|  | Method | mAP (%) | FLOPs (GMac) | Params (M) | Average Inference Time (ms) |
|---|---|---|---|---|---|
| One-stage | RetinaNet [10] | 91.2 | 81.69 | 36.1 | 44.10 |
|  | SSD300 [11] | 93.1 | 154.45 | 34.31 | 53.62 |
|  | YOLOv3 [12] | 96.2 | 77.54 | 61.52 | 45.81 |
|  | YOLOX | 96.2 | 26.64 | 8.94 | 8.20 |
|  | YOLOv5 | 97.0 | 16.54 | 7.23 | 8.61 |
|  | AFSar [14] | 96.7 | 8.66 | - | - |
| Two-stage | Faster R-CNN [36] | 96.4 | 91.41 | 41.12 | 45.36 |
|  | Cascade R-CNN [37] | 96.8 | 119.05 | 69.17 | 65.56 |
|  | FPN [38] | 96.5 | 71.65 | 63.56 | 78.30 |
| Anchor-free | CornerNet [39] | 94.7 | 707.75 | 201.04 | 95.61 |
|  | CenterNet [40] | 95.1 | 20.4 | 14.21 | 31.54 |
|  | FCOS [41] | 95.3 | 78.63 | 60.97 | 48.67 |
|  | LPEDet | 97.4 | 18.38 | 5.68 | 7.01 |

It should be noted that, except for AFSar, the methods in the comparison experiments were reproduced according to the official open-source code of the comparison method and applied to the SSDD dataset for experimental comparison. The dataset used by the comparison method was exactly the same as that used by our proposed method; the hyperparameters of the comparison method were all set with standard default settings and the number of training epochs is also consistent with our method.

We also visualized the detection results of these methods. As shown in Figure 7, compared with the proposed LPEDet method, the detection rate of the above methods was significantly higher than that of the proposed LPEDet method. Our method has good performance with small target images, complex backgrounds and intensive target image detection. These findings show the effectiveness of our approach.

## 4.4. Comparison with the Latest SAR Ship Detection Methods Using SSDD Datasets

To further verify the performance of our method, we also compared it with the latest SAR ship detection methods, as shown in Table 5.

**Table 5.** Comparison with the latest SAR ship detection methods.

| Methods | mAP (%) | FLOPs (GMac) | Params (M) | Average Inference Time (ms) |
|---|---|---|---|---|
| DCMSNN [30] | 89.43 | - | 41.1 | 46.2 |
| NNAM [31] | 79.8 | - | - | 28 |
| FBR-Net [42] | 94.10 | - | 32.5 | 40.1 |
| CenterNet++ [43] | 95.1 | - | - | 33 |
| EFGRNet [44] | 91.1 | - | - | 33 |
| Libra R-CNN [45] | 88.7 | - | - | 57 |
| DAPN [32] | 89.8 | - | - | 41 |
| LPEDet | 97.4 | 18.38 | 5.68 | 7.01 |

The comparison methods and related experimental results in Table 5 need special explanation. Since none of these comparison methods have open-source original codes, it is difficult for us to completely reproduce the codes and parameter settings of the comparison methods. Therefore, to fairly compare the performance of different detection methods, we directly cite the highest detection results reported in the original reference of the comparison methods. Especially for the two indicators of FLOPs and params, most of the comparison methods have no relevant results. Therefore, we only cite the best experimental results for other indicators published in the references. In addition, the results of the comparison methods listed in Table 5 are mainly from references [42,43].

The results show that not only does our LPEDet achieve SOTA in accuracy but it also has a relatively faster inference speed, which shows the high efficiency of our method.

## 4.5. Comparison with the Latest SAR Ship Detection Methods Using HRSID Datasets

In order to fully verify the performance stability of the LPEDet method proposed in this paper with respect to different datasets, we introduce a new large-scale SAR target detection dataset, namely, HRSID, and compare a variety of state-of-the-art SAR target detection methods using this dataset. The specific results are shown in Table 6, below. By comparing the experimental results, it was found that, compared with the current latest SAR ship target detection methods, the LPEDet method proposed in this paper is superior in terms of accuracy, while the parametric and computational complexity of the model are also the lowest, which proves the stability of our method in relation to different datasets. As can be seen in Table 6, except for the fact that the data for CenterNet2 on AP, AP₇₅, APₘ and APₗ are slightly higher than for our model, the difference is not big, and the number of parameters in our model is almost 1/15 the number of its parameters, such that, considering accuracy and speed, our model still has better performance in comparison.

![](img/828a5d28a36454f7b3332df93f35492f_262_0.png)

Figure 7. Visual detection results of the latest methods. The purple box is the target that was missed when marked, the red box is the target of misdetection and the blue box is a missed target.

**Table 6.** Comparison of the latest SAR target detection methods on HRSID.

| Method | AP | AP₅₀ | AP₇₅ | APₛ | APₘ | APₗ | FLOPs (GMac) | Params (M) | Average Inference Time (ms) |
|---|---|---|---|---|---|---|---|---|---|
| YOLOv3 [12] | 50.9 | 85.0 | 53.1 | 51.0 | 56.1 | 25.5 | 121.15 | 61.52 | 136 |
| SAR-net [46] | - | 84.7 | - | - | - | - | 104.2 | 42.6 | 118 |
| CenterNet2 [47] | 64.5 | 89.5 | 73.0 | 64.7 | 69.1 | 48.3 | - | 71.6 | - |
| RetinaNet [10] | 59.8 | 84.8 | 67.2 | 60.4 | 62.7 | 26.5 | 127.91 | 36.3 | 122 |
| YOLOX [13] | 61.4 | 87.2 | 68.9 | 63.0 | 57.0 | 21.8 | 26.64 | 8.94 | 8.20 |
| LPEDet | 64.4 | 89.7 | 71.8 | 65.8 | 63.4 | 24.2 | 18.38 | 5.68 | 7.01 |

## 4.6. The Effect of the Number of Training Sets on Detection Performance

In order to verify the robust performance of our proposed method under the conditions of different training data, we redivided the training and testing ratios of the dataset under the conditions of 33% and 66% of the training set data, respectively, to validate the performance of our model. The results are shown in Table 7 below. We combined the results of Table 4 in the paper for the analysis (the training data volume of all methods in Table 4 is 80% and above): when we only use 66% of the training data volume, mAP can still reaching 96.8%, the performance is still better than most state-of-the-art SAR target detection methods; and when we use only 33% of the training data volume, mAP can still reach 94.6%, outperforming RetinaNet and SSD300, such that, compared to other state-of-the-art SAR target detection methods, the results are not much different. The analysis of the above results shows that the proposed LPEDet method can still achieve better performance than the latest SAR target detection methods with fewer training data, that it still has good robustness and that it can greatly reduce the labor costs involved in manual labeling of data.

**Table 7.** Comparison of experimental results for different data volumes on SSDD.

| Method | Datasets Rate | mAP (%) |
|---|---|---|
| LPEDet | 33% | 94.6 |
|  | 66% | 96.8 |
|  | 80% | 97.4 |

## 5. Conclusions

Multi-platform SAR earth observation equipment has accumulated massive amounts of high-resolution SAR target image data, and SAR image target detection has great engineering application value in military/civilian fields. Aimed at the problems of unclear target contour information, complex backgrounds, strong scattering and multiple scales in SAR images, a new anchor-free SAR ship detection algorithm, LPEDet, was proposed to improve the accuracy and speed of SAR ship detection in a balanced manner. First, YOLOX was used as the benchmark detection network; then, a new lightweight backbone, NLCNet, was designed. At the same time, to further improve localization accuracy, we designed a location-enhanced attention strategy. The experimental results based on the SSDD dataset showed that the mAP of our LPEDet reached 97.4%, achieving SOTA. Meanwhile, the average inference time for a single image is only 7.01ms when the input size is 640. With respect to the HRSID dataset, our model is also stable, with an AP₅₀ of 89.7%, which is superior to other state-of-the-art object detection methods, while the computational complexity, the number of parameters and the average inference time are lowest. In the future, based on the Hisea-1 SAR satellite that our research group participated in launching, our group independently constructed a larger-scale multi-type SAR target image dataset. We will verify the effectiveness of our proposed LPEDet algorithm on this large-scale dataset. Common SAR image artifacts such as speckle noise can affect SAR target detection results,
