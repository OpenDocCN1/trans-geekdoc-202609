![](bbox=[0.203, 0.069, 0.796, 0.237])

Figure 2. Training and validation curves of accuracy obtained from DEMNET and D DEMNET frameworks.

![](bbox=[0.203, 0.296, 0.796, 0.458])

Figure 3. (a) Average performance comparison between DEMNET and D-DEMNET frameworks. (b) Accuracy comparison between DEMNET and D-DEMNET frameworks.

In total, the training accuracy, validation accuracy, and testing accuracy of the DEMNET model is 97.89%, 73.74%, and 73.12%. But, the training accuracy, validation accuracy, and testing accuracy of the proposed framework is 98.49%, 80.39%, and 95.16%, respectively. The proposed framework has much higher learning ability than the base model.

| Precision | Recall | Support |
|---|---|---|---|---||
| DEMNET | D-DEMNET | DEMNET | D-DEMNET | DEMNET | |
| AD | 0.81 | 0.88 | 0.78 | 0.79 | 0.86 | 112 |
| CN | 0.38 | 0.65 | 0.89 | 0.53 | 0.65 | 125 |
| eMCI | 0.84 | 0.78 | 0.27 | 0.81 | 0.79 | 117 |
| iMCI | 0.87 | 0.93 | 0.91 | 0.87 | 0.95 | 116 |
| MCI | 0.94 | 0.79 | 0.15 | 0.76 | 0.77 | 110 |

Table 2. Performance indices of individual classes in both DEMNET and D-DEMNET model.

# 5 CONCLUSION

In this paper, a new framework called D-DEMNET which is based on CNN architecture is proposed for improving the performance in classifying the AD stages to detect the progression of the disease. Here we have done a comparison between the proposed framework and the base model to evaluate the performance. For class imbalance, we have used the same technique as explained in the base model. The accuracy obtained by the proposed framework is 95.16% which is better than the base model. Despite having good results, there are still