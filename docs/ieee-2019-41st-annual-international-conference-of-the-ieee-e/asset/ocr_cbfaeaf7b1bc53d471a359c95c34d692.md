# IEEE Access

TABLE 4: Comparing the classification accuracy of DDL+SVM with various architectures and methods.

| Dataset | DDL-SVM | Supervised DL | LC-KSVD | D-KSVD | DBN | SDAE-Softmax | CNN |
|---|---|---|---|---|---|---||
| MNIST | 98.64 | 98.95 | 93.30 | 93.6 | 97.1 | 96.69 | 99.06 |
| basic | 97.28 | 95.14 | 92.70 | 92.20 | 96.69 | 98.56 |
| basic-rot | 90.34 | 88.27 | 48.60 | 50.01 | | 90.47 | 89.45 |
| bg-rand | 92.38 | 88.23 | 87.70 | 87.70 | 93.27 | | 93.23 |
| bg-img | 86.17 | 80.92 | 80.65 | 81.20 | 83.32 | 88.89 |
| bg-img-rot | 63.85 | 74.31 | 75.40 | 75.40 | 52.61 | | 57.97 |
| 20-newgroup | 71.97 | 69.22 | 68.90 | 69.45 | 72.40 | |
| GTZAN | 84.92 | 79.86 | 76.85 | 71.68 | 83.98 |

The implementation of these has been obtained from [72] and [73] respectively. Similar to deep learning, SAE and DBN also have a three-layer architecture. The number of nodes is halves in every subsequent layer and comparison with K-Nearest Neighbor (KNN) and Support Vector Machine (SVM). To ensure a fair comparison of techniques, we have kept the classifier for these experiments. The results are shown in Tables 2 and 3.

All the algorithms were run on a machine with Intel(Core™ i5) running at 3 GHz with 8 GB RAM, Windows 10 (64 bit) running Matlab 2014a. For the small MNIST accuracies are nearly as same as the. We only report the results for the larger dataset (KNNK and the basic). We do not include the training and testing time for classification here; since these will be the same for all the techniques as the dimensionality of the features remains the same.

We observe that one case in Tables 2 and 3, the proposed algorithms yield better results than DBN and SAE. For KNN, the results of deep dictionary are better; however, with SVM classifier, deep dictionary yields considerably better.

TABLE 5. Training feature generation time (seconds).

| Dataset | DDL | DBN | SAE |
|---|---|---|--|
| MNIST | 107 | 3071 | 12408 |
| basic | 26 | 597 | 2420 |

We have compared the performance of the proposed algorithm with dictionary learning techniques as D-KSVD [28], and supervised learning [21]. These individuals are finely-tuned to yield the best possible results. The proposed algorithm is in the top two best results and achieves better accuracy than highly tuned models such as DDL, SDAE, and CNN. The CNN-20-newgroup dataset does not have local correlation and cannot be represented as a linear time invariant system—an aspect required for the convolution operation based unit.

TABLE 6. Test feature generation time (seconds).

| Dataset | DDL | DBN | SAE |
|---|---|---|--|
| MNIST | 79 | 50 | 61 |
| basic | 257 | 151 | 185 |

# D. ELECTRICAL APPENDIX CLASSIFICATION

The following sections demonstrate results on benchmark datasets. In this section, we evaluate the effectiveness of deep dictionary learning for solving a real-world problem. Gupta et al.: the problem of classification of electrical instruments from their energy-magnetic interference (EMI) signatures. They showed results on appendix classification

We next compare the proposed algorithm with other deep learning in terms of computational speed (train feature generation + test feature generation).