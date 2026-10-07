
# Self-Supervised Learning for Intelligent Fault Diagnosis ■ 169

TABLE 9.3 The Training Time (s) of Different Methods on Three Datasets with 20% Labeled Data

| Datasets | MPFT | XITU-SY | ABG |
|---|---|---|---|
| Supervised | 11.12 | 8.21 | 11.54 |
| Pseudo-label | 131.85 | 99.80 | 134.64 |
| II model | 343.06 | 265.89 | 358.28 |
| MTL | 515.21 | 406.10 | 535.74 |
| CR | 301.49 | 226.30 | 308.44 |
| SLA | 229.30 | 175.52 | 240.68 |
| MoCo | 905.94 | 716.80 | 917.50 |
| SimCLR | 1130.18 | 856.53 | 1146.70 |
| ITTSL | 827.58 | 635.73 | 845.38 |

## Discussions

### Ablation of Relation Mining Tasks
To explore the effect of the inter-instance and intra-temporal relation mining modules, an ablation study is conducted. Two variants are derived from the proposed ITTSL, i.e., (1) ISSC which only applies inter-relation mining module, and (2) TSSC which utilizes only intra-temporal relation mining module. The results of these two variants together with the supervised baseline and the proposed ITTSL on different datasets are shown in Table 9.4.

As be observed from the results, ISSC, TSSC and ITTSL outperform the supervised baseline by a large extent, which indicates that the combination of self-supervised learning and SSL makes a significant improvement on SSL tasks. Among the three contrastive learning methods, TSSC obtains a slightly higher accuracy than ISSC, which may be attributed to the temporal features can better reflect the failure modes than inter-instance features. What is more, our method acquires the highest diagnostic accuracy, suggesting that mining both inter-instance and intra-temporal relation of unlabeled data can further improve the discriminability of the model.

### The Influence of UDW
To demonstrate the influence of uncertainty-based dynamic weighting (UDW), we compare it with the traditional fixed weighting approach, namely the weight of each task is equal and constant during the training process. The

TABLE 9.4 The Results of Ablation Study on Three Datasets

| Dataset | MPFT | XITU-SY | ABG |
|---|---|---|---|
| Label rate | 10% | 20% | 40% | 100% | 10% | 20% | 40% | 100% | 10% | 20% | 40% | 100% |
| Supervised | 50.38 ±0.56 | 56.05 ±0.59 | 62.71 ±0.62 | 77.61 ±0.67 | 64.80 ±0.81 | 83.15 ±0.73 | 91.12 ±0.74 | 98.16 ±0.55 | 72.17 ±0.79 | 81.50 ±0.74 | 88.10 ±0.55 | 97.03 ±0.37 |
| ISSC | 64.47 ±0.64 | 70.55 ±0.84 | 76.74 ±0.45 | 83.10 ±0.43 | 77.90 ±0.98 | 90.08 ±1.01 | 95.97 ±1.03 | 98.56 ±0.63 | 78.00 ±0.82 | 85.90 ±0.52 | 91.80 ±0.58 | 97.26 ±0.31 |
| TSSC | 65.15 ±0.79 | 69.76 ±0.84 | 77.19 ±0.47 | 83.56 ±0.44 | 84.16 ±0.93 | 94.11 ±0.48 | 96.53 ±0.33 | 98.40 ±0.47 | 83.90 ±0.76 | 92.40 ±0.39 | 94.60 ±0.36 | 97.32 ±0.42 |
| ITTSL | 66.17 ±0.78 | 71.72 ±0.78 | 77.31 ±0.43 | 84.47 ±0.45 | 84.73 ±0.91 | 92.05 ±0.72 | 97.17 ±0.43 | 98.85 ±0.42 | 84.87 ±0.82 | 92.56 ±0.38 | 95.07 ±0.36 | 97.68 ±0.33 |

TABLE 9.5 The Comparison Results on the MPFT Dataset under Different Label Rates

| | Task Weight | | Accuracy Under Different Label Rates |
|---|---|---|---|---|---|
| Supervised Loss | Temporal Relation Loss | Instance Relation Loss | 10% | 20% | 40% |
| Fixed weighting | 0.5 | 0.5 | 0 | 63.46 | 69.57 | 73.72 |
| | 0.5 | 0 | 0.5 | 60.28 | 68.77 | 76.09 |
| | 0.33 | 0.33 | 0.33 | 61.66 | 71.21 | 75.69 |
| Uncertainty-based dynamic weighting | ✓ | | | 65.15 | 77.19 | 76.74 |
| | | ✓ | | 64.47 | 70.55 | 76.74 |
| | | ✓ | | 66.17 | 71.72 | 77.31 |

results on the MPFT dataset are listed in Table 9.5. It can be observed that when applying the fixed weighting approach, the accuracies of the model that integrates three losses may be lower than those using two losses. It might be owing to certain relation dominating the training process. However, when UDW is adopted, the results with both instance relation and temporal relation contrasting tasks achieve the best performance. The weight distribution curve of ITSSL during the training process is depicted in Figure 9.6, where the weight of supervised loss drops at the first epochs and subsequently grows to a stable value. Instead, the weight of instance relation increases and then decreases. And the weight of temporal relation gradually drops to a certain value. As the training process goes on, the classification uncertainty decreases, and the model learns a proper weighting scheme.

### The Influence of the Split Ratio
As mentioned in the intra-temporal mining module, the length of the former segment is T and the length of the latter one is L. Here we evaluate the performance of different segment split ratio $\eta$, i.e., the ratio of $T$ to $L$. As shown in Figure 9.7, the black line represents the accuracy improvement of ITSL compared to the supervised baseline at different split ratios on the MPFT dataset with 40% labeled data. Although the accuracy improvement all outperforms supervised approaches by a large extent, the accuracy improvement is even higher when $\eta$ is 0.3, 0.4 or 0.5 than other split ratios. An explanation could be, the contrasting tasks between extremely imbalanced segments are unable to extract the temporal dependency underlying the vibration signals. Generally, the split ratio is selected to 0.5 as a compromise.

### Visualization Analysis
To illustrate the better feature extraction all supervised learning, we visualized the results of the latent features of the backbone encoder on X-SY dataset with 20% labeled samples, as shown in Figure 9.8, where the left two graphs denote the representations of unlabeled samples and the right two graphs refer to the representations of testing samples. It can be concluded that (1) for supervised learning, the features of various failure modes are mixed, indicating that supervised method owns little discriminability with only few data, (2) for ITSL, the self-supervised relation mining tasks can guide unlabeled samples of different failure modes to cluster automatically. Besides, features of testing samples are also pulled away, which makes out-of-distribution fault diagnosis more accurate.

![](img/f29bba55de872c43af266705f2_180_0)FIGURE 9.6 The weight distribution curve of ITSSL during training process.

![](img/f29bba55de872c43af266705f2_181_0
FIGURE 9.7 The accuracy improvement of ITSL compared with supervised baseline at different split ratios $\eta$ on MFPT dataset with 40 labeled data.

FIGURE 9.8 Visualized features of (a) the unlabeled samples using supervised methods, (b) the unlabeled samples using ITSL, (c) the testing samples using supervised methods, and (d) the testing samples using ITSL on X-SY dataset with 20% labeled samples, where 0-14 denote failure modes.

# Deep Networks-Enabled Intelligent Fault Diagnosis of Mechanical Systems

# CONCLUSION
This chapter adopts a self-supervised learning technique-based diagnosis framework to address the label-insufficient problem in intelligent fault diagnosis, where few labeled and massive unlabeled data are used concurrently to improve efficiency. As an extension of DA technique, TAD is pertinently designed for vibration signals. Then two self-supervised tasks are constructed, explores the inter-relation and intra-temporal relation of unlabeled data to improve the discriminability of the model. Moreover, UDW is adopted to alleviate single task dominance.
