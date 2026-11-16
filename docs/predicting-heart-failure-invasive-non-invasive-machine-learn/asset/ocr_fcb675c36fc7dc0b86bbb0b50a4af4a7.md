Table 9.6 HF diagnosis classification results, unbalanced class.

| Classifier | Feature Selection | Accuracy% | Classifier | Feature Selection | Accuracy% |
|---|---|---|---|---|---|
| BN | No | 91.86 | BN | Yes | 94.00 |
| NB | No | 92.72 | NB | Yes | 94.65 |
| SVM | No | 95.50 | SVM | Yes | 95.07 |
| k-NN | No | 88.87 | k-NN | Yes | 93.36 |
| ROT | No | 96.36 | ROT | Yes | 95.07 |
| C4.5 | No | 91.43 | C4.5 | Yes | 92.51 |
| LMT | No | 94.65 | LMT | Yes | 95.50 |
| RF | No | 95.29 | RF | Yes | 94.86 |

# 9.2.2.2 Methodology

The development of the model for the NYHA class detection module consisted of three basic stages: preprocessing, feature selection, and classification. During preprocessing, features with more than (≥) 60.00% missing values were removed. Furthermore, discrete features with unbalanced distribution of values were removed. In the second step, the wrapper approach and correlation-based feature selection algorithm were used. In the classification stage, RF, LMT, C4.5, ROT, SVM, radial basis function (RBF) Network, BN, Naive Bayes (NB), and Simple CART classifiers were applied. The classifiers were combined with resampling techniques (SMOTE algorithm), when the class was unbalanced. Resampling was performed only during the training of the model and not during the test for avoiding bias of classification results.

# 9.2.2.3 Results for HF Severity Estimation

The features removed after applying the preprocessing step are depicted in Figure 9.6. The data set consisted of 92 patients’ data. The model was trained to detect NYHA class II, NYHA class III, and NYHA class IV, since HF patients belonging only to one of

Table 9.7 HF diagnosis classification results, balanced class

| Classifier | Feature Selection | Accuracy% | Classifier | Feature Selection | Accuracy% |
|---|---|---|---|---|---|
| BN | No | 92.82 | BN | Yes | 93.78 |
| NB | No | 92.34 | NB | Yes | 94.50 |
| SVM | No | 94.98 | SVM | Yes | 94.74 |
| k-NN | No | 88.52 | k-NN | Yes | 93.30 |
| ROT | No | 95.22 | ROT | Yes | 95.22 |
| C4.5 | No | 93.78 | C4.5 | Yes | 92.82 |
| LMT | No | 95.22 | LMT | Yes | 94.98 |
| RF | No | 94.98 | RF | Yes | 94.50 |