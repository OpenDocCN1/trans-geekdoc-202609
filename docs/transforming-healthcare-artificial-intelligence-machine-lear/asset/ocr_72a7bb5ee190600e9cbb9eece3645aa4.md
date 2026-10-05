# 72 Transforming Healthcare

### Table 3.2 Machine learning-based treatment outcome predictions

| Disease | ML model | Dataset | Accuracy (%) | Sensitivity (%) | Specificity (%) |
|---|---|---|---|---|--|
| Diabetes | Random Forest | Pima Indians | 88.5 | 87.1 | 90.4 |
| Cancer prognosis | Gradient boosting machine (GBM) | TCGA dataset | 89.7 | 90.2 | 89.0 |
| Cardiovascular | Support vector machine (SVM) | Framingham heart | 85.6 | 86.3 | 84.9 |
| Stroke prediction | XGBoost | Stroke dataset | 87.4 | 88.5 | 86.3 |
| Eye disease | K-Nearest neighbour (KNN) | Eye disease dataset | 84.1 | 83.4 | 85.0 |

# 3.5.2 Machine learning-based treatment outcome predictions

ML models are also used to predict treatment outcomes. The results for supervised learning models are shown in Table 3.2, focusing on diseases such as diabetes, cancer, cardiovascular conditions, and eye disease.

The evaluation of the ML model's ability to predict treatment outcomes of diseases such as diabetes, cancer, CVDs, and eye disease has some valuable revelations regarding the benefits and shortcomings of these models. Diabetes (Random Forest): There is a rapid growth of training and test accuracies during the initial epochs, which develops steadily. After the twentieth epoch, the training accuracy hits nearly 100%. The test accuracy thereby reaches around 88.5%, which shows good generalisation of the model, but can still be seen that there is a difference between training and test accuracies. This proves that the Random Forest does very well in understanding the patterns in data, but it does tend to overfit to some extent for complex or varied datasets.

Just like in the Round of twenty centuries extension model, the Gradient Boosting Machine (GBM) model also records a considerable increase in training accuracy, reaching 99% at the twentieth epoch. In contrast, test accuracy hovers around 82%–89%. That is the distinguishing feature of GBM, which brought up the question. This resource relocation between how and what GBM achieves a different purpose for the reader. Future iterations of this model may far better using, among other methods, cross-validation and regularisation or feature selection and generalisation (Figure 3.4).

In many ways, the SVM can be equated with the GBM in terms of training accuracy — nearly 100 is attained. Referring to Figure 3.3, though, 85% seems to be the ceiling for test accuracy. Once again, the problem area here lies under generalisation. Test accuracy could be slightly lower due to many variables related to cardiovascular issues or an imbalance in