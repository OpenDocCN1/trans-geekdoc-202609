
## Supplemental Table 4: Internal validation of view classifier on TMED-2 test sets

| Development Set Size | Split1 balanced | Split2 balanced | Split3 balanced | Average balanced |
|---|---|---|---|--|
| number studies (train/valid) | accuracy (2.5, 97.5th) | accuracy (2.5, 97.5th) | accuracy (2.5, 97.5th) | accuracy (2.5, 97.5th) |
| 479 (360 / 119) | 96.72 (95.84, 97.53) | 97.23 (96.41, 98.00) | 97.14 (96.61, 98.09) | 97.03 (95.85, 97.54) |
| 165 | 95.47 (94.47, 96.41) | 95.46 (94.44, 96.43) | 96.38 (95.49, 97.24) | 95.77 (94.46, 96.44) |
| 56 | 88.99 (87.55, 90.34) | 89.99 (88.47, 91.42) | 92.03 (90.72, 93.28) | 90.34 (87.52, 90.35) |

Supplemental Table 4: Internal validation of view classifier on TMED-2 test sets. The view classifier is trained to produce a 5-way probabilistic classification (PLAX, PSAX AoV, A4C, A2C, or Other) given a single image. We report balanced accuracy across 3 training/test splits of the TMED-2 dataset with a 95% bootstrap CI in parentheses.

## Supplemental Table 5: External validation of view classifier on Stanford EchoNet

| Development Set Size | Split1 | Split2 | Split3 | Average |
|---|---|---|---|---||
| number studies (train/valid) | A4C accuracy (2.5, 97.5th) | A4C accuracy (2.5, 97.5th) | A4C accuracy (2.5, 97.5th) | A4C accuracy (2.5, 97.5th) |
| 479 (360 / 119) | 95.02 (94.61, 95.45) | 92.99 (92.31, 93.33) | 92.21 (92.11, 93.17) | 93.41 (93.21, 93.77) |
| 165 | 70.57 (69.69, 71.48) | 90.02 (89.43, 90.60) | 82.84 (82.11, 83.57) | 81.14 (80.72, 81.58) |
| 56 | 61.30 (60.33, 62.24) | 55.29 (54.34, 56.28) | 81.66 (80.90, 82.41) | 66.08 (65.55, 66.61) |

Supplemental Table 5: External validation of view classifier on Stanford EchoNet. We evaluate the TMED-2 trained classifier on all 10030 A4C view images in the Stanford EchoNet Dynamic dataset. We report accuracy (fraction of A4C views correctly identified) across 3 training splits of the TMED-2 training set, with a 95% bootstrap CI in parentheses.

## Supplemental Table 6: AS diagnosis classifier balanced accuracy on TMED-2 test set

| Dev Size number | Method | Split1 balanced accuracy | Split2 balanced accuracy | Split3 balanced accuracy | Average balanced |
|---|---|---|---|---|--|
| studies (train/valid) | | (2.5, 97.5th) | (2.5, 97.5th) | (2.5, 97.5th) | balanced |
| 479 (360/119) | Simple Average | 35.16 (31.82, 38.97) | 35.29 (33.33, 38.27) | 34.18 (31.37, 37.50) | 34.88 |
| | Prioritized View | 74.63 (66.73, 82.24) | 72.61 (66.05, 79.24) | 76.24 (69.62, 82.87) | 74.49 |

**Supplemental Table 6:** AS diagnosis classifier balanced accuracy on TMED-2 test set. We report balanced accuracy for this 3-class problem (no AS, early AS, significant AS), with 95% bootstrap CI in parentheses. Random chance would have 33.33% balanced accuracy.

## Supplemental Figure 1: Image Labeling Tool

![img/9e83ae159adbe9802ed604394e24f29_48_0.png

Supplemental Figure 1: Image labeling tool. Labeling tool displays de-identified images in an array that allows rapid assignment of view labels using quick keys for the labels of interest.

## Supplemental Figure 2. Diagnosis Classification Accuracy as a Function of Sample Size

![img/9e83ae159adbe9802ed604394e24f29_49_0.png

Supplemental Figure 2. Diagnosis Classification Accuracy as a Function of Sample Size. We plot balanced accuracy across all studies in the TMED-2 test set (y-axis) versus the number of studies available for model development (training and validation, x-axis). Each line gives the performance of one prediction strategy for aggregating all images in a study: Prioritized View and Simple Average. Square markers give the average over 3 splits, and the color bar represents standard deviation.

## Supplemental Figure 3. Projections of View Classifier Error Rate vs Sample Size

![img/9e83ae159adbe9802ed604394e24f29_50_0.png

**Supplemental Figure 3.** Projections of View Classifier Error Rate as Training Set Size Increases. As amount of available labeled data increases, using the power law scaling rule $an^{-\beta}$ fit to minimize squared error with the three measurements shown. With this prediction, 1000 labeled studies available for training and validation (double our current release's amount) would yield a balanced error rate of 1.5%, equivalent to balanced accuracy of 98.5%.
