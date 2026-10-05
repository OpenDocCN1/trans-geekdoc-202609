# Hybrid DBCT for lung cancer detection & severity analysis

![](bbox=[0.135, 0.095, 0.863, 0.355])

Figure 11.6 Proposed DBCT architecture.

Table 11.1 Performance analysis of CNN algorithms, compact convolutional transformer with the proposed dense block convolutional transformer model on CT scan dataset – binary classification
| Algorithms | Accuracy % | F1-score % | Precision % | Recall % |
|---|---|---|---||}{
| EfficientNet-B0 | 93.5 | 93.6 | 93.8 | 93.2 |
| ResNet-50 | 96.2 | 95.4 | 96.8 | 95.5 |
| DenseNet-121 | 96.5 | 96.4 | 96.7 | 96.3 |
| CCT | 97.6 | 97.4 | 97.8 | 97.5 |
| DBCT | 98.5 | 98.2 | 98.9 | 97.8 |

Table 11.2 Performance analysis of CNN algorithms, compact convolutional transformer with the proposed dense block convolutional transformer model on LC25000 dataset multiclass classification with five classes
| Algorithms | Accuracy % | F1-score % | Precision % | Recall % |
|---|---|---|---||}{
| EfficientNet-B0 | 87.2 | 86.3 | 87.4 | 86.5 |
| ResNet-50 | 90.5 | 89.7 | 90.7 | 90.3 |
| DenseNet-121 | 91.3 | 90.2 | 91.6 | 91.0 |
| CCT | 93.4 | 92.2 | 93.6 | 92.5 |
| DBCT | 94.5 | 93.9 | 94.7 | 94.1 |