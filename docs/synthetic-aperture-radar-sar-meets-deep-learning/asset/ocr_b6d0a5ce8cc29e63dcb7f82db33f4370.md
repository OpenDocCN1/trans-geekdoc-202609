achieve outstanding performance. However, they always adopt complex structures in exchange for improved accuracy at the expense of detection efficiency. Lately, some single-stage detection methods, such as R³Det, GWD, and CS²A-Net, have been presented, which show competitive performance and efficiency on RSSD. Our method can further improve the accuracy of these rotation detectors and has a minimal impact on detection efficiency. As per Table 10, the proposed approach achieves 75.41%, 96.62%, and 87.87% accuracy in terms of inshore AP, offshore AP, and test AP on CS²A-Net, respectively, without using multi-scale training and testing, which is already extremely close to the performance of the advanced ReDet and GWD. When employing a stronger backbone (i.e., ResNet101) and multi-scale training and testing, our approach achieves state-of-the-art performance, with the AP of 77.65%, 97.35%, and 89.18%, respectively, which is 1.98%, 0.65%, and 1.11% higher than that of the suboptimal method (i.e., GWD). Furthermore, the inference speed of our method reaches 12.1 fps, which is 11.1 fps and 2.5 fps faster than that of ReDet and GWD, respectively. Compared to the original CS²A-Net, our approach trades off a speed loss of only 1.1 fps for significant gains, of 3.48%, 0.87%, and 1.85%, in accuracy.

Table 10. Comparison with state-of-the-art methods on RSSD. Here, MS indicates the multi-scale training and testing, FPS is obtained by calculating the overall inference time and the number of images, TDLoU + AW-FPN represents the CS²A-Net detector based on TDLoU loss and AW-FPN, R-50 refers to ResNet50 (likewise R-101, R-152), and ReR-50 and H-104 denote ReResNet50 [68] and Hourglass104, respectively [69].

| Method | Backbone | Stage | MS | Inshore AP | Offshore AP | Test AP | FPS |
|---|---|---|---|---|---|---|---|
| SCRDet [41] | R-101 | Two | ✓ | 65.47 | 95.53 | 83.65 | 5.0 |
| RSDNet [70] | R-152 | Two |  | 68.48 | 95.88 | 84.85 |  |
| Gliding Vertex [71] | R-101 | Two |  | 70.83 | 96.11 | 85.80 | – |
| CSL [44] | R-152 | Two | ✓ | 71.45 | 96.18 | 86.15 | 4.0 |
| SCRDet++ [72] | R-101 | Two | ✓ | 71.66 | 96.21 | 86.24 | 5.0 |
| ReDet [68] | ReR-50 | Two | ✓ | 75.57 | 96.65 | 88.03 | <1.0 |
| RetinaNet-R [17] | R-50 | Single |  | 44.30 | 91.38 | 72.13 | 17.5 |
| DRN [73] | H-104 | Single | ✓ | 67.95 | 95.68 | 84.40 | – |
| R³Det [74] | R-152 | Single | ✓ | 71.47 | 96.25 | 86.21 | 9.6 |
| DCL [45] | R-101 | Single | ✓ | 71.92 | 96.23 | 86.36 | 12.0 |
| GWD [23] | R-152 | Single | ✓ | 75.67 | 96.70 | 88.07 | 9.6 |
| CS²A-Net [67] | R-50 | Single |  | 70.99 | 96.13 | 85.95 | 16.5 |
| CS²A-Net [67] | R-101 | Single | ✓ | 74.17 | 96.48 | 87.33 | 13.2 |
| TDLoU + AW-FPN (ours) | R-50 | Single |  | 75.41 | 96.62 | 87.87 | 15.1 |
| TDLoU + AW-FPN (ours) | R-101 | Single | ✓ | 77.65 | 97.35 | 89.18 | 12.1 |

Figure 24 shows qualitative results of different methods on RSSD. As per the results of the offshore scene containing multiple ships (the first row), the other four methods detect islands and reefs incorrectly as ships, while our method is more robust in distinguishing small ships from background components. For the complex inshore scenes (the second row to the fourth row), the results of other methods include false alarms and leave some vessels undetected. In contrast, our method succeeds in detecting all ships and locating them more precisely, especially for densely arranged ships close to man-made facilities.

# 6.4.2. Results on the SSDD

Table 11 shows experimental results of different methods on the SSDD. Since SSDD contains few SAR images and the scenes are relatively simple, the ship detection accuracy is generally high. As shown in Table 11, based on CS2A-Net (R-50), our approach achieves 80.75%, 99.64%, and 94.05% of inshore AP, offshore AP, and test AP, respectively. When using ResNet101 as the backbone network, the AP of our approach reaches 84.34%, 99.71%, and 95.16%, compared to the state-of-the-art detectors ReDet (82.80%, 99.18%, and 94.27%) and GWD (81.99%, 99.66%, and 94.35%). Moreover, our approach improves the overall accuracy by 1.26% and 0.44% compared to BiFA-YOLO and R2FA-Det, respectively, and the inference speed by 5.5 fps compared to the suboptimal R2FA-Det, indicating that the proposed method achieves the best performance and satisfies high detection efficiency.