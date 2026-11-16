![](bbox=[0.226, 0.109, 0.783, 0.196])

Figure 15. Reconstructed images with 2D-PCA and PCA versus original image (t: principal component number). (a) Original image; (b) PCA principal component reconstruction images; (c) 2D-PCA principal component reconstruction images.

# Table 1. Average recognition rates of different recognition methods.

| Serial number | Recognition method | Recognition rate/% |
|---|---|---|
| 1 | PCA + BP | 66.2 |
| 2 | WT + PCA + BP | 67.29 |
| 3 | PCA + HBPNNs | 91.7 |
| 4 | WT + PCA + HBPNNs | 93.3 |

# Table 2. Average recognition rates of different recognition methods.

| Serial number | Recognition method | Recognition rate/% |
|---|---|---|
| 1 | WT + 2D-PCA + RBF | 90.5 |
| 2 | WT + 2D-PCA + HRBFNNs | 95.5 |

As shown in Table 3, “One-Against-One” SVM has higher recognition rate than “One-Against-the-Rest” SVM and at the same time has lower wrong number. Therefore, we use the way of “One-Against-One” to reconstruct the SVM classifier to realize FR.

Experiment 8. In the paper we construct the multiple classification decision fusion classifier (MCDFC)—hybrid HBPNNs-HRBFNNs-SVM classifier. In this experiment, in order to show the efficiency of MCDFC, we first make recognition experiment respectively based on HBPNNs, HRBFNNs and SVM, then use the decision function to make fusions for classification results of three classifiers and get classification results of MCDFC. The experiment is repeated for 20 times and the experimental results are shown in Table 4 and in Figure 16.