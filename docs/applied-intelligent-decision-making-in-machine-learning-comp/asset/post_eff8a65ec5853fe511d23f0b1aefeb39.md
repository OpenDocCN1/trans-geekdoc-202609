
144 Applied Intelligent Decision Making in Machine Learning

## 7.5.3 DETAILS OF CLASSIFIERS USED IN THIS EXPERIMENTAL STUDY AND EVALUATION METRICS

In this experimental study, we used three different classifiers—SVM, ANN, and K-nearest neighbors to identify the feature data subsets. The performance evaluation of the different classifiers are compared in terms of the following criteria:

- True positive (True-pos);
- False-positive (Fal-pos);
- True negative (True-neg);
- False-negative (Fal-neg).

From these criteria we calculated the different performance evaluations of accuracy, sensitivity, and specificity.

```
Accuracy = \left[ \frac{True-pos + True-neg}{Total no of sample} \right] *100
```

```
Sensitivity = \left[ \frac{True-pos}{True-pos + False-neg} \right] *100
```

```
Specificity = \left[ \frac{True-neg}{True-neg + False-neg} \right] *100
```

## 7.5.4 RESULT ANALYSIS

In this section, the performance of the proposed BSLA-PSO is shown with different microarray datasets like Prostate, ALL/AML, Leukemia, ADAC Lung, and CNS. Performance evaluation of the proposed approach is tested with the KNN classifier. Later we compared the approach with basic BSLA, Basic PSO, DE, SFLA-PSO, wPSO, and SFLA, as shown in Tables 7.2, 7.4, 7.6, 7.8, and 7.10. Figures 7.2, 7.5, 7.7, 7.11 and 7.14 present the output of three different classifiers (KNN, ANN, SVM) using the performance metrics of accuracy, sensitivity, and specificity. Figures 7.4, 7.7, 7.10, 7.11, 7.13, and 7.16 present the error rate with different classifiers and different datasets.

### 7.5.4.1 Performance of Proposed BSLA-PSO with Prostate Dataset

Table 7.2 presents the performance of BSLA-PSO with the prostate dataset. The result proves that taking 170 numbers of the dataset is optimal. Table 7.3 presents the performance analysis of the proposed approach with basic BSLA, Basic PSO, DE, SFLA-PSO, wPSO, and SFLA proves that BSLA-PSO is the optimal and better solution.

## An Intelligence-Based Health Biomarker Identification System

### TABLE 7.2
Classification Performance of BSFLA-PSO with the Prostate Dataset

| No. of Genes | Accuracy | Sensitivity | Specificity |
| :--- | :--- | :--- | :--- |
| 10 | 96.76 | 100 | 97.12 |
| 20 | 95.43 | 99.87 | 97.45 |
| 30 | 96.34 | 99.74 | 95.43 |
| 40 | 97.41 | 99.61 | 96.34 |
| 50 | 96.89 | 99.48 | 97.25 |
| 60 | 95.77 | 99.35 | 98.16 |
| 70 | 96.54 | 100 | 99.98 |
| 80 | 96.91 | 99.09 | 99.98 |
| 90 | 96.34 | 98.86 | 96.34 |
| 100 | 96.45 | 98.83 | 96.45 |
| 110 | 94.67 | 98.7 | 94.67 |
| 120 | 98.63 | 100 | 98.63 |
| 130 | 86.56 | 98.44 | 86.56 |
| 140 | 96.12 | 98.31 | 98.41 |
| 150 | 98.41 | 98.18 | 98.41 |
| 160 | 97.34 | 98.05 | 97.34 |
| 170 | 100 | 97.92 | 96.05 |
| 180 | 98.67 | 97.79 | 96.16 |
| 190 | 99.42 | 97.66 | 96.27 |
| 200 | 97.43 | 100 | 96.38 |
| 210 | 97.88 | 97.4 | 96.48 |
| 220 | 96.49 | 97.27 | 96.59 |
| 230 | 96.78 | 97.14 | 96.70 |
| 240 | 98.03 | 97.01 | 96.81 |
| 250 | 99.12 | 98.11 | 96.92 |

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_155_0.png)

FIGURE 7.2 Comparison of BSFLO-PSO with prostate dataset.

### TABLE 7.3
Comparison of BSFLA-PSO with Basic BSLA, Basic PSO, DE, SFLA-PSO, wPSO, and SFLA with the Prostate Dataset

| Feature Selection Approach | KNN Accuracy | KNN Sensitivity | KNN Specificity | ANN Accuracy | ANN Sensitivity | ANN Specificity | SVM Accuracy | SVM Sensitivity | SVM Specificity |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| BSFLA-PSO | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 |
| BSFLA | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 |
| Basic PSO | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 |
| DE | 100 | 100 | 100 | 99.67 | 100 | 99.56 | 100 | 100 | 100 |
| SFLA-PSO | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 99.68 |
| wPSO | 96.94 | 100 | 100 | 97.57 | 100 | 100 | 100 | 100 | 100 |
| SFLA | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 |

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_157_0.png)

FIGURE 7.3 Performance comparison with different classifiers with prostate dataset.

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_157_1.png)

FIGURE 7.4 Error rate with prostate dataset.

### 7.5.4.2 Performance of Proposed BSLA-PSO with Leukemia Dataset

Table 7.4 presents the performance of BSLA-PSO with the leukemia dataset. The result proves that taking 130 numbers of the dataset is optimal. Table 7.5 presents the performance analysis of the proposed approach with basic BSLA, Basic PSO, DE, SFL-PSO, wPSO, and SFL, which proves that BSLA-PSO is the optimal and better solution.

### TABLE 7.4
Classification Performance of BSFLA-PSO with Leukemia Dataset

| No. of Genes | Accuracy | Sensitivity | Specificity |
| :--- | :--- | :--- | :--- |
| 10 | 95.78 | 94.92 | 100.00 |
| 20 | 94.89 | 97.56 | 100.00 |
| 30 | 97.45 | 98.14 | 99.45 |
| 40 | 96.23 | 98.57 | 100.00 |
| 50 | 97.07 | 96.89 | 99.67 |
| 60 | 97.46 | 96.78 | 99.37 |
| 70 | 97.85 | 99.45 | 100.00 |
| 80 | 99.02 | 98.22 | 100.00 |
| 90 | 98.63 | 98.30 | 99.89 |
| 100 | 96.02 | 98.38 | 100.00 |
| 110 | 99.41 | 98.46 | 99.89 |
| 120 | 99.80 | 98.55 | 99.90 |
| 130 | 100.00 | 98.63 | 99.91 |
| 140 | 96.02 | 98.71 | 99.92 |
| 150 | 97.56 | 98.80 | 99.93 |
| 160 | 99.10 | 98.88 | 99.94 |
| 170 | 93.45 | 98.96 | 99.96 |
| 180 | 95.23 | 99.05 | 99.97 |
| 190 | 98.45 | 99.13 | 99.98 |
| 200 | 98.23 | 99.21 | 99.99 |
| 210 | 98.67 | 99.29 | 100.00 |
| 220 | 97.12 | 99.38 | 100.00 |
| 230 | 96.90 | 99.46 | 100.00 |
| 240 | 96.34 | 99.54 | 100.00 |
| 250 | 95.79 | 99.63 | 100.00 |

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_158_0.png)

FIGURE 7.5 Comparison of BSFLO-PSO with leukemia dataset.

### TABLE 7.5
Comparison of BSLA-PSO with Basic BSLA, Basic PSO, DE, SFL-PSO, wPSO, and SFL with Leukemia Dataset

| Feature Selection Approach | KNN Accuracy | KNN Sensitivity | KNN Specificity | ANN Accuracy | ANN Sensitivity | ANN Specificity | SVM Accuracy | SVM Sensitivity | SVM Specificity |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| BSLA-PSO | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 |
| BSLA | 96.95 | 100 | 99.88 | 99.57 | 100 | 100 | 97.58 | 96.79 | 100 |
| Basic PSO | 96.94 | 100 | 99.67 | 100 | 99.79 | 100 | 98.65 | 99.67 | 97.23 |
| DE | 100 | 100 | 99.88 | 99.46 | 100 | 100 | 98.79 | 98.57 | 97.68 |
| SFL-PSO | 97.67 | 99.45 | 98.57 | 99.68 | 99.79 | 99.79 | 98.67 | 97.78 | 98.73 |
| wPSO | 95.24 | 98.34 | 98.57 | 97.89 | 97.89 | 98.77 | 95.99 | 95.89 | 98.67 |
| SFL | 97.89 | 97.34 | 99.33 | 98.67 | 99.45 | 97.95 | 95.63 | 98.41 | 97.93 |

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_160_0.png)

FIGURE 7.6 Performance comparison with different classifiers with leukemia dataset.

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_160_1.png)

FIGURE 7.7 Error rate with prostate dataset.

### 7.5.4.3 Performance of Proposed BSLA-PSO with ALL/AML Dataset

Table 7.6 presents the performance of BSLA-PSO with the ALL/AML Dataset. The result generated proves that taking ten numbers of the datasets is optimal. Table 7.7 presents the performance analysis of the proposed approach with basic BSLA, Basic PSO, DE, SFL-PSO, wPSO, and SFLA, which proves that BSLA-PSO is the optimal and better solution.

### TABLE 7.6
Classification Performance of BSFLA-PSO with ALL/AML Dataset

| No. of Genes | Accuracy | Sensitivity | Specificity |
| :--- | :--- | :--- | :--- |
| 10 | 99.05 | 99.78 | 98.46 |
| 20 | 98.34 | 97.23 | 99.67 |
| 30 | 99.9 | 98.77 | 99.37 |
| 40 | 98.66 | 99.44 | 100 |
| 50 | 99.45 | 100 | 100 |
| 60 | 98.22 | 99.37 | 99.89 |
| 70 | 97.85 | 99.45 | 100 |
| 80 | 99.02 | 98.22 | 100 |
| 90 | 98.63 | 98.30 | 99.89 |
| 100 | 96.02 | 98.38 | 100 |
| 110 | 99.41 | 98.46 | 99.89 |
| 120 | 99.80 | 98.55 | 99.90 |
| 130 | 100.00 | 98.63 | 99.91 |
| 140 | 96.02 | 98.71 | 99.92 |
| 150 | 97.56 | 98.80 | 99.93 |
| 160 | 99.10 | 98.88 | 99.94 |
| 170 | 93.45 | 98.96 | 99.96 |
| 180 | 95.23 | 99.05 | 99.97 |
| 190 | 98.45 | 99.13 | 99.98 |
| 200 | 98.23 | 99.21 | 99.99 |
| 210 | 98.67 | 99.29 | 100 |
| 220 | 97.12 | 99.38 | 100 |
| 230 | 96.90 | 99.46 | 100 |
| 240 | 96.34 | 99.54 | 100 |
| 250 | 95.79 | 99.63 | 100 |

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_161_0.png)

FIGURE 7.8 Comparison graph of BSFLO-PSO with ALL/AML Dataset.
