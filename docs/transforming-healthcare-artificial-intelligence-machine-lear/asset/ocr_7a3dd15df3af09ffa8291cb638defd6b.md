# Table 11.3 Performance analysis of CNN algorithms, compact convolutional transformer with the proposed dense block transformer model on IQ-OTH/ NCCD dataset – severity analysis and classification with three classes

| Algorithms | Accuracy % | F1-score % | Precision % | Recall % |
|---| EfficientNet-B0 | 89.5 | 88.6 | 89.8 | 88.5 |
| ResNet-50 | 93.2 | 92.8 | 93.4 | 93.0 |
| DenseNet-12i | 93.8 | 93.5 | 93.9 | 93.6 |
| CCT | 96.6 | 96.3 | 96.8 | 96.4 |
| DBCT | 97.3 | 96.8 | 97.8 | 97.0 |

# 11.5.1 Evaluation metrics

The evaluation metrics describe the performance of the model. The calculation of various evaluation metrics including accuracy, recall, specificity, precision, and F1-score is shown in the following equations:

```
ACC = \frac{TP}{TP + TN + FN} (11.4)
```

```
Recall = \frac{TP}{TP + FN} (11.5)
```

```
Specificity = \frac{TN}{TN + FP} (11.6)
```

```
Precision = \frac{TP}{TP + FP} (11.7)
```

```
F1-Score = 2 \times \frac{Precision \times Recall}{Precision + Recall} (11.8)
```

The training and validation accuracy of the proposed DBCT is shown in Figures 11.7 and 11.8. The proposed model offers an accuracy of 97.8% in classifying the lung cancer. The accuracy of the model is estimated for the binary detection and the multiclass classification.

The graph of training and validation losses over the epochs is shown in Figure 11.8. The proposed model is trained for about 50 epochs. The proposed model is good enough to offer the better accuracy in minimum number of epochs in less time and the reduced computational complexity.