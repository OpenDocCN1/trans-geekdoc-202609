![](bbox=[0.118, 0.119, 0.878, 0.403])

**FIGURE 7.2**  
Implementation of Linde-Buzo-Grey (LBG) Algorithm.

is repeated with the centroids to generate the desired size of the codebook, which is 16 in this case.

The extracted features from the four public datasets are tested with four different classifiers, namely, K Nearest Neighbor (KNN), Ripple-Down Rule (RIDOR), Artificial Neural Network (ANN) and Support Vector Machine (SVM). The results are given in Table 7.1.

**TABLE 7.1**  
Classification Performances by Feature Extraction using Vector Quantization with Four Different Public Datasets using Four Different Classifiers

| Datasets | Metrics | KNN | RIDOR | ANN | SVM |
|---|---|---:|---:|---:|---:|
| Wang | Precision | 0.900 | 0.900 | 0.928 | 0.888 |
|  | Recall | 0.890 | 0.900 | 0.925 | 0.869 |
|  | MR | 0.042 | 0.039 | 0.038 | 0.043 |
|  | F1-Score | 0.884 | 0.900 | 0.925 | 0.862 |
| OT-Scene | Precision | 0.923 | 0.922 | 0.937 | 0.860 |
|  | Recall | 0.919 | 0.922 | 0.936 | 0.860 |
|  | MR | 0.038 | 0.039 | 0.036 | 0.044 |
|  | F1-Score | 0.923 | 0.922 | 0.937 | 0.856 |
| Corel | Precision | 0.703 | 0.713 | 0.820 | 0.545 |
|  | Recall | 0.658 | 0.668 | 0.819 | 0.499 |
|  | MR | 0.057 | 0.073 | 0.046 | 0.091 |
|  | F1-Score | 0.700 | 0.660 | 0.819 | 0.468 |
| Caltech | Precision | 0.725 | 0.781 | 0.863 | 0.714 |
|  | Recall | 0.725 | 0.777 | 0.864 | 0.712 |
|  | MR | 0.057 | 0.053 | 0.042 | 0.066 |
|  | F1-Score | 0.707 | 0.778 | 0.862 | 0.714 |

> > [Observation: All four datasets have maximum classification results with the ANN classifier.]