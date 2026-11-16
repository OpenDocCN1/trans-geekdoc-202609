
from the features to describe colonic polyp images. However, in this case, the results from CNN-F and AlexNet CNN are better using the features from the last fully connected layers.

### Table 7. Results from i-Scan1 database with images resized to 224 × 224 using the last fully connected layer and the prior fully connected layer

| | CNN-F | CNN-M | CNN-S | CNN-F MCN | CNN-M MCN | CNN-S MCN | GoogleLeNet | VGG-VD16 | VGG-VD19 | AlexNet | AlexNet MCN | $\overline{x}$ |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Prior fully connected layer | 89.33 | 90.67 | 90.00 | 82.00 | 90.67 | 91.42 | 90.67 | 85.33 | 82.67 | 87.33 | 84.67 | 87.70 |
| Last fully connected layer | 90.67 | 84.67 | 85.33 | 78.67 | 88.00 | 89.33 | 90.67 | 84.67 | 79.33 | 81.33 | 90.67 | 85.75 |

### Table 8. Accuracies of the methods for the CC-i-Scan databases in %

| Methods | -CVC | i-Scan1 | i-Scan2 | i-Scan3 | -CVC | i-Scan1 | i-Scan2 | i-Scan3 | $\overline{x}$ |
|---|---|---|---|---|---|---|---|---|---|
| 1: CNN-F | 86.16 | 89.33 | 80.65 | 88.41 | 86.53 | 81.40 | 84.22 | 80.62 | 84.66 |
| 2: CNN-M | 82.45 | 90.67 | 81.38 | 83.58 | 87.99 | 89.55 | 87.40 | 90.53 | 87.31 |
| 3: CNN-S | 81.80 | 90.00 | 80.64 | 79.33 | 90.22 | 92.56 | 91.00 | 92.34 | 90.41 |
| 4: CNN-F MCN | 88.84 | 82.00 | 73.15 | 70.73 | 85.78 | 89.55 | 89.72 | 83.15 | 85.36 |
| 5: CNN-M MCN | 89.53 | 90.67 | 88.88 | 94.66 | 86.97 | 89.29 | 87.40 | 90.53 | 89.74 |
| 6: CNN-S MCN | 89.21 | 90.67 | 88.64 | 90.65 | 86.50 | 88.49 | 90.10 | 90.27 | 89.48 |
| 7: GoogleLeNet | 79.65 | 90.67 | 72.43 | 74.51 | 88.27 | 80.46 | 75.60 | 84.08 | 80.70 |
| 8: VGG-VD16 | 82.45 | 85.33 | 86.38 | 79.65 | 92.47 | 89.80 | 95.26 | 92.38 | 88.59 |
| 9: VGG-VD19 | 81.49 | 82.67 | 89.24 | 89.71 | 93.07 | 88.84 | 95.46 | 88.28 | 88.98 |
| 10: AlexNet | 91.40 | 82.33 | 75.65 | 89.32 | 87.71 | 83.03 | 84.22 | 79.24 | 84.73 |
| 11: AlexNet MCN | 89.42 | 84.67 | 78.88 | 83.78 | 89.36 | 83.55 | 81.10 | 78.32 | 83.63 |
| 12: BSAG-LFD | 86.27 | 86.67 | 84.60 | 83.87 | 85.50 | 80.63 | 78.78 | 71.99 | 80.50 |
| 13: Blob SC | 77.67 | 83.33 | 82.10 | 75.22 | 79.28 | 78.83 | 66.13 | 59.83 | 72.79 |
| 14: Haralick-Weber | 73.72 | 76.67 | 79.60 | 86.80 | 81.30 | 69.94 | 72.38 | 83.63 | 78.00 |
| 15: Local binary... | 79.75 | 70.00 | 76.45 | 82.88 | 72.09 | 74.34 | 77.27 | 80.59 | 76.86 |
| 16: LCVP | 76.60 | 66.60 | 42.75 | 77.12 | 77.45 | 79.00 | 70.01 | 69.56 | 70.43 |
| 17: MB-LBP | 78.26 | 80.67 | 81.38 | 83.37 | 69.29 | 70.60 | 72.22 | 78.32 | 77.38 |
| 18: Fusion 5/8 | 81.37 | 80.00 | 83.58 | 90.84 | 90.21 | 78.98 | 92.40 | 91.33 | 86.44 |
| 19: Fusion 5/8 | 88.84 | 85.33 | 83.88 | 92.14 | 93.12 | 90.49 | 96.88 | 94.00 | 90.58 |
| 20: Fusion 5/12 | 92.79 | 92.67 | 88.88 | 96.98 | 87.71 | 90.49 | 93.23 | 90.56 | 91.03 |
| 21: Fusion 5/8/14 | 95.94 | 90.00 | 88.64 | 92.14 | 94.69 | 84.43 | 92.04 | 90.66 | 92.22 |
| 22: Fusion 5/8/15 | 91.51 | 86.67 | 82.10 | 93.75 | 94.68 | 91.43 | 98.44 | 95.85 | 92.67 |
| 23: Fusion 5/8/14 | 90.98 | 90.00 | 88.88 | 92.14 | 93.94 | 89.80 | 96.88 | 95.61 | 92.27 |
| 24: Fusion 5/8/12/14 | 93.38 | 86.67 | 84.84 | 93.75 | 94.06 | 92.12 | 97.33 | 94.52 | 93.08 |
| 25: Fusion 5/8/12/17 | 93.38 | 90.00 | 91.38 | 93.75 | 92.75 | 92.12 | 97.63 | 97.46 | 93.55 |
| CNN-05 | - | 91.00 | - | 89.00 | - | - | - | - | - |
| CNN-05 + SVM | - | 83.00 | - | 72.55 | - | - | - | - | - |

Based on the results from the two experiments explained before, we tested the methods with all the other databases using the inputs resized to size 224 × 224 × 3 by bicubic interpolation and extracting the features from the prior fully connected layer. The accuracy results for the colonic polyp classification for the 8 different databases are reported in Table 8. As can be seen, the results in Table 8 are divided into three groups: off-the-shelf features, classical features, and the fusion between off-the-shelf features and classical features that will be explained as follows.

Among the 11 pretrained CNNs investigated, the CNNs that present lower performance were GoogleLeNet, CNN-S, and AlexNet MCN. These results may indicate that such networks themselves are not sufficient to be considered off-the-shelf feature extractors for the polyp classification task.

As it can be seen in Table 8, the pretrained CNN that presents the best result on average for the different imaging modalities ($\overline{x}$) is the CNN-M network trained with the MatConvNet parameters (89.74%) followed by the CNN VGG-VD16 (88.59%). These deep models with smaller filters generalize well with other datasets as it is shown in [49], including texture recognition, which can explain the better results in the colonic polyp database. However, there is a high variability in the results and thus it is difficult to draw general conclusions.

Many results obtained from the pretrained CNNs surpassed the classic feature extractors for colonic polyp classification in the literature. The database that presents the best results using off-the-shelf features is the database staining the mucosa without any i-Scan technology (~CVC, 88.54% on average). In the case of classical features, the database with the best result on average is the database using the i-Scan3 technology without staining the mucosa (81.61%).

To investigate the differences in the results we assess the significance of them using the McNemar test [57]. By means of this test we analyze if the images from a database are classified differently or similarly when comparing two methods. With a high accuracy it is supposed that the methods will have a very similar response, so the significance level $\alpha$ must be small enough to differentiate between classifying an image as correct or incorrect.

The test is carried out on the databases i-Scan3 and i-Scan1 without staining the mucosa using significance level $\alpha = 0.01$ with all the off-the-shelf CNNs, all the classical features, and the CNN-05 architecture trained from scratch. The results are presented in Figure 3. It can be observed by the black squares (indicating significantly differences) that, among the pretrained CNNs, in the i-Scan1 database the results are not significantly different and in the i-Scan3 database the CNN-M MCN and GoogleLeNet present the most significantly different results comparing to the other CNNs. It also can be seen that the CNN-05 does not have significantly different results comparing to the other CNNs in the i-Scan1 database and has significantly different results with CNN-M MCN and GoogleLeNet in the i-Scan3 database.

![](img/1752b062af2760b8561f6faaf183b3d0_273_0.png)

### Figure 3. Results of the McNemar test for the i-Scan1 (a) and i-Scan3 (b) databases without staining. A black square in the matrix means that the methods are significantly different with significance level and a grey square in (a) means that the methods are significantly different with significance level . If the square is white then there is no significant difference between the methods.

Also, in Figure 3, when comparing the classical feature extraction methods with the CNNs features it can be seen that there is a quite different response among the results in i-Scan3 database, especially for CNN-M MCN that is significantly different from all the classical methods with the exception of the Shearlet-Weibull method.

The CNN-05 and CNN-05 + SVM did not present significantly different results with the classical features (except with LCVP in i-Scan1 database) and with the pretrained CNNs (except with CNN-M and GoogleLeNet in i-Scan3 database). Likewise, the methods with high accuracy in the i-Scan3 database (BSAG-LFD, VGG-VD16, and VGG-VD19) are not found to be significantly different.

In the i-Scan1 database, with the significance level \(\alpha\) =0.05, the results are not significantly different in general (except for LCVP features). However, with the significance level \(\alpha\) = 0.01, the significance results represented by the grey squares in Figure 3(a) show that the two databases presented different correlation between methods which means that it is difficult to predict a good feature extractor that can satisfy both databases at the same time.

Observing the methods that presented significantly different results in Figure 3 and with good results in Table 8 we decided to produce a feature
