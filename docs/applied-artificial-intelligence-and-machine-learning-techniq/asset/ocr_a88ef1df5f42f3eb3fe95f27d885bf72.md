**TABLE 5.1**
**Confusion Matrix Representation for Classifiers**

| Classifier | TN | TP | FP | FN |
| :--- | :--- | :--- | :--- | :--- |
| SVM | 27 | 36 | 2 | 2 |
| DT | 25 | 30 | 4 | 8 |
| RF | 28 | 37 | 1 | 1 |
| K-NN | 26 | 34 | 3 | 4 |
| ANN | 27 | 36 | 2 | 2 |

**TABLE 5.2**
**Performance Comparison with Related Studies**

| Study | Classifier | Accuracy | Precision | Recall | F1 Score |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Yu et al. [3] | CNN | 94% | 92% | 93% | 93.5% |
| Feng et al. [6] | SVM | 90% | 91% | 89% | 90% |
| Meng et al. [8] | LASSO | 88% | 87% | 90% | 88.5% |
| Pesapane et al. [9] | RF | 85% | 84% | 87% | 85.5% |
| Yu et al. [10] | SVM | 93% | 92% | 94% | 93% |
| Zheng et al. [11] | ANN | 95% | 94% | 96% | 95% |
| Chakravarthy et al. [12] | ELM | 91% | 90% | 92% | 91% |
| Guo et al. [13] | CNN | 89% | 88% | 90% | 89% |
| Li et al. [5] | RF | 92% | 91% | 93% | 92% |
| Martin et al. [14] | ANN | 96% | 95% | 97% | 96% |
| This Work (using RF) | RF | 96% | 94% | 97% | 95.5% |

Table 5.2 highlights the effective use of RF, known for handling high-dimensional data efficiently, which is critical in medical imaging tasks. Studies like those by Martin et al. [14] and Zheng et al. [11] also show high performance with ANN models, reflecting the robustness of deep learning techniques in capturing complex patterns. The variation in model performance can be attributed to the differences in dataset characteristics, feature extraction techniques, and model tuning. The consistent high scores across different studies underscore the potential of advanced machine learning models to significantly enhance diagnostic accuracies, promising better clinical outcomes through earlier and more precise detection.

# 5.4.7 CONCLUSION AND FUTURE SCOPE

This study successfully demonstrated the application of various machine learning classifiers to enhance breast cancer detection using radiomics extracted from MRI