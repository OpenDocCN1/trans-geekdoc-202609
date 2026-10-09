# Table 3. Performance analysis of YOLOv7 and improved YOLOv7.

| Class | Method | Precision (%) | Recall (%) | mAP@0.5 (%) | mAP@0.5:0.95 (%) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| blight | YOLOv7 | 89.9 | 92.6 | 89.9 | 55.3 |
| | Improved YOLOv7 | 93.5 | 95.6 | 93.5 | 58.5 |
| black rot | YOLOv7 | 91.4 | 92.9 | 91.4 | 52.5 |
| | Improved YOLOv7 | 93.6 | 94.7 | 93.7 | 55.4 |
| black measles | YOLOv7 | 81.6 | 79.3 | 91.1 | 43.4 |
| | Improved YOLOv7 | 84.3 | 81.9 | 93.3 | 45.4 |

# Table 4. Comparison of small target detection quantity.

| | Small Target Quantity | YOLOv7 | Improved YOLOv7 |
| :--- | :--- | :--- | :--- |
| blight | 1730 | 1570 | 1675 |
| black rot | 1356 | 1223 | 1339 |
| black measles | 2098 | 1803 | 1954 |

In order to verify the advantages of the improved model in the identification of grape leaf diseases, the detection results for each of the three diseases are shown in Figure 9 by YOLOv7 and improved YOLOv7, respectively. According to the comparison, it can be found that the original YOLOv7 model in the figure has many missed detections in the detection of small disease spots, and the discrimination of a single disease spot is low. The missed detection rate of the improved YOLOv7 algorithm for grape leaf lesion detection is obviously reduced, and the regional location of the lesion is more accurate. At the same time, the disease spots of different leaves can be detected simultaneously in the natural environment, and the disease spots in the edge area of the image also have a good detection effect, as shown in Figure 9.

![](bbox=[0.08, 0.52, 0.35, 0.73])

![](bbox=[0.36, 0.52, 0.63, 0.73])

![](bbox=[0.64, 0.52, 0.92, 0.73])

Figure 9. Cont.