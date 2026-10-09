**Table 3.** Improved model-performance analysis for each category.

| Category | AP (%) | Precision (%) | Recall (%) | F1 Measure |
|---|---|---|---|---|
| Guns | 95.73 | 98.59 | 84.92 | 0.91 |
| Knives | 83.00 | 91.43 | 67.20 | 0.77 |
| Wrenches | 82.95 | 83.66 | 71.95 | 0.77 |
| Pliers | 85.13 | 92.95 | 74.23 | 0.82 |
| Scissors | 80.74 | 86.88 | 75.13 | 0.81 |

The average value of various objects was taken as the overall performance-evaluation index and compared with the original YOLOv4, as shown in Table 4.

**Table 4.** Comparison of YOLOv4 performance before and after improvement.

| Method | mAP (%) | Precision (%) | Recall (%) | F1 Measure |
|---|---|---|---|---|
| YOLOv4 | 83.11 | 90.35 | 73.00 | 0.80 |
| YOLOv4-PANv2 | 85.51 | 90.70 | 74.69 | 0.82 |

As can be seen from the table, compared with the original YOLOv4 model, the mAP, accuracy, and recall rate of the YOLOv4-PANv2 model increased by 2.4%, 0.35%, and 1.69%, respectively, which means that all indicators of our detection algorithm were improved and the improved model had better detection performance.

The detection performance of the model in the test set is shown in Figure 9, where (a) is a single-target image, (b) is a multi-target image, (c) is an occluded-target image, (d) is an overlapping image, (e) is a placement-difference image, and (f) is a small-target image. It can be seen that the improved model could accurately detect each target with our proposed method.

![](bbox=[0.18, 0.56, 0.85, 0.93])