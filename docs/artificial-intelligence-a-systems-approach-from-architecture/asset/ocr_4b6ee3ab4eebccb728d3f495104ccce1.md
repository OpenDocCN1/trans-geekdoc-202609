# 76 Chapter 3: Data Conditioning

![](bbox=[0.237, 0.104, 0.762, 0.323])

| Classifier | Description | Error rate (%) |
|---|---||
| Linear classifier | Pairwise linear classifier | 7.6 |
| K-Nearest Neighbors | K-NN with non-linear deformation (P2DHMDM) | 0.52 |
| Boosted Stumps | Product of stumps on Haar features | 0.87 |
| Non-linear classifier | 40 PCA + quadratic classifier | 3.3 |
| Support-vector machine | Virtual SVM, deg-9 poly, 2-layer jittered | 0.56 |
| Deep neural network | 2-layer 784-800-10 | 1.6 |
| | 2-layer 784-800-10 (elastic distortions) | 0.7 |
| | 6-layer 784-2500-2000-1500-1000-500 | 0.35 |
| | 6-layer 784-40-80-500-1000-2000-10 | 0.31 |
| Convolutional neural network | 6-layer 784-50-100-500-1000-1010-10 | 0.27 |
| | Committee of 3 CNNs, 1-20-P-40-P-1520 | 0.23 |
| | Committee of 5 CNNs, 6-layer 784-50-100-500-1000-1010-10 | 0.21 |

Figure 3.6 MNIST handwritten data set and algorithm test error rate performance.

years later (ILSVRC 2015), Microsoft researchers demonstrated the ResNet CNN algorithm with a top-five 3.57 percent error rate. The ResNet CNN algorithm used 128 million labeled images for training, 50,000 images for cross-validation, and 100,000 test images [44].

With gratitude to several AI researchers, these major leaps in algorithm performance were made possible only because of the advent of open-source data sets, supported by computing engines such as graphics processing units (GPUs). Although the MNIST and ImageNet sets continue to serve as benchmarks, there