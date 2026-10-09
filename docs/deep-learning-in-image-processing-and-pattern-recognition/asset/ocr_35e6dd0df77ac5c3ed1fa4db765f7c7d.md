Table 4. Performance of the different state-of-the-art methods on Le2i dataset.
| Method | Accuracy (%) | 0.5 mAP | Precision of Fall |

![](bbox=[0.16, 0.27, 0.82, 0.5])

![](bbox=[0.16, 0.5, 0.82, 0.72])

Table 5 shows the results of McNemar’s significance test on UR-Fall dataset where the performance of YOLOv7 is statistically significant ($p<0.05$) over RetinaNet, but it is not statistically different from that of YOLOv5. Table 6 shows the different object detection algorithms on the UR Fall detection dataset. YOLO models achieve high results on metrics such as accuracy and mAP, with YOLOv7 performing the best among all the models. However, RetinaNet did not perform well on the UR-Fall dataset, reporting the lowest accuracy of 40.9% as well as the lowest mAP of 0.464. Similarly, to the experiments on Le2i FDD, YOLOv7 is integrated with the Deep SORT tracking algorithm to report the results on the UR-Fall dataset. The proposed method outperforms all the methods in terms of accuracy, mAP, and precision. As shown in the second row of Figure 6, the visual results on the UR-Fall dataset using the proposed method highlights the improved performance on the enhanced video frames as compared to the YOLOv7 + Deep SORT.