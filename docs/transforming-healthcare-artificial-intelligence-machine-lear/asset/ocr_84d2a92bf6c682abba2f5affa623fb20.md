Melanoma detection by hybrid attention DCNN-BiLSTM architecture 393

+   * Accuracy: The percentage of predictions the model successfully predicted is known as accuracy. It's described as:

```
$Accuracy = \frac{Tp+Tn}{Tp+Tn+Fp+Fn} \quad (18.52)$
```

+   * Precision: Precision is determined by dividing the number of predicted positive samples by the percentage of correctly identified samples.

```
$Precision = \frac{Tp}{Tp+Fp} \quad (18.53)$
```

+   * Recall: Recall is the percentage of all correctly classified positive samples that are correctly identified. It's described as:

```
$Recall = \frac{Tp}{Tp+Fr} \quad (18.54)$
```

+   * F1-score: The F1-score or F-score are other names for this metric. A weighted average of the accuracy and recall results in the F1-score. The best number is 1, while the lowest is 0. In determining the F1-score, recall and accuracy contribute equally, which is described as:

```
$F-Score2 = \frac{Precision \times Recall}{Precision + Recall} \quad (18.55)$
```

where Tp, Tn, Fp, and Fn are the true positive, true negative, false positive, and false negative, respectively.

# 18.4.1 Performance evaluation

The effectiveness of the proposed hybrid attention-based DCNN-BiLSTM model for melanoma detection is assessed using various metrics. This section compares the proposed and current approaches, including ResNet, MobileNet, VGG-16, Inception V3, and Inception ResNet. Accuracy, precision, recall, and F1-score are among the performance indicators examined to assess how well the suggested model compared to the most advanced techniques. These metrics provide an in-depth assessment of the model's robustness and dependability by revealing how effectively it can differentiate between instances with and without melanoma.

Figure 18.5 compares the accuracy of existing models with the newly proposed model, including ResNet, MobileNet, VGG-16, Inception V3, and Inception ResNet. Both ResNet and MobileNet reach an accuracy