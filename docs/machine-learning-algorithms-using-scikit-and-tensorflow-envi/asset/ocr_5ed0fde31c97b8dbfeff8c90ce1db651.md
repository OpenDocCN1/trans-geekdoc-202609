# Figure 6. ResNet-50 confusion matrix

![](bbox=[0.26, 0.17, 0.76, 0.52])

# Table 4. Detail analysis for ResNet-50 model by class

| Class | Recall | Precision | F-Measure | TPR | FPR |
|---|---|---|---|---|---|
| Normal | 77.7% | 83.6% | 80.5% | 77.7% | 22.3% |
| Rust high severity | 79.8% | 83.7% | 81.7% | 79.8% | 20.2% |
| Rust Medium severity | 87.7% | 83.7% | 85.6% | 87.7% | 12.3% |
| Spot high severity | 85.9% | 84% | 84.9% | 85.9% | 14.1% |
| Spot Medium severity | 86.5% | 83.6% | 85% | 86.5% | 13.5% |
| Spot Low severity | 80.1% | 86.1% | 82.9% | 80.1% | 19.9% |
| Weighted average | 84.2% | 84.1% | 84.2% | 84.2% | 15.8% |

# 4.2 VGG-19

It has 19 layers including convolutional layers, pooling layer, and three fully connected layers with three blocks and two of them with 4096 neurons and 1000 neurons which is the output of the class probabilities. Besides, this state-of-art architecture, hyper-parameters, and parameters like the number of filters,