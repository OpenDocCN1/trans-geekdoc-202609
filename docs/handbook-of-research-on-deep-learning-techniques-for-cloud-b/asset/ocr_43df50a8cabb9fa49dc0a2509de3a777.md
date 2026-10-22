# **_Accuracy Determination_**

# *Table 1. Training and testing records*

| Attack | Training | Testing |
|---|---:|---:|
| Normal | 14658 | 9792 |
| Denial-of-Service (DoS) | 9355 | 7537 |
| Probing | 2369 | 2521 |
| Remote-to-Local (R2L) | 212 | 2769 |
| User-to-Root (U2R) | 13 | 201 |
| Total | 26106 | 22603 |

# *Table 2. Comparison of data over performance*

| S. No | Performance | SVM | RNN | Proposed |
|---:|---|---:|---:|---:|
| 1 | Accuracy | 88.9 | 93.42 | 91.32 |
| 2 | Precision | 79.6 | 90.4 | 95.24 |
| 3 | Decision rate | 91.2 | 95.3 | 98.61 |
| 4 | False rate | 11.5 | 9.3 | 6.4 |

Figure 6 compares and shows the current Support Vector Machine (SVM), Recommended for RNN-IDS and malware detection. This method has been found to be more accurate than other methods. The RNN performance of this model is 4% lower than the consensus model and the SVM performance of this model is 8% lower than the consensus model. The efficiency of the control method averages 97.5% over the iteration, and there is little difference in detection accuracy when it reaches 1000.

However, the performance characteristics of the SVM in the intrusion prevention environment make a significant change in the detection accuracy of the SVM.

# *Figure 5. Detection rate comparison*

![](bbox=[0.272, 0.664, 0.764, 0.726])

The algorithm that analyzes the evaluation of each of the three models can be seen in Figure 6. The proposed method gives an average accuracy of 96.28% compared to 88.84% and 91.17% for SVM and RNN.

The performance analysis presented in the figure shows how well the proposed method identifies the attack. Unlike classification results, which use the similarity score to determine the type of attack. Adaptive features and training levels increase the detection accuracy of the proposed model. As analysis and risk increase, the effectiveness of protection against access to the model requested by individual entities may appear to slightly reduce detection accuracy. It categorizes attacks better than other systems.