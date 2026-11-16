Table 3. Assessing the performance of each model on diabetic and non-diabetic.

| Models | Diabetic Accuracy | Diabetic Loss | Non-Diabetic Accuracy | Non-Diabetic Loss |
|---|---|---|---|---|
| Logistic Regression | 0.99 | 0.011 | 0.63 | 0.37 |
| Random Forest | 1 | 2.7e-05 | 0.99 | 0.0084 |
| SGD | 0.97 | 0.025 | 0.71 | 0.29 |
| Decision Tree | 1 | 1.4e-05 | 0.99 | 0.0084 |
| KNN | 1 | 0.0039 | 0.6 | 0.4 |
| Naive Bayes | 0.93 | 0.073 | 0.65 | 0.35 |
| SVM | 1 | 1.4e-05 | 0.39 | 0.61 |

accuracy of 0.6 for diabetic cases, leading to “loss” values of 0.0039 and 0.4. Remarkably, both the Random Forest as well as Decision Tree models achieved perfect accuracy (1) for both non-diabetic and diabetic cases, accompanied by extremely low “loss” values of 1.4e-05 and 2.7e-05 for both classes, respectively. While the Support Vector Machine (SVM) reached perfect accuracy (1) for non-diabetic cases, its accuracy for diabetic cases was 0.39. This discrepancy resulted in “loss” values of 1.4e-05 for non-diabetic and 0.61 for diabetic cases.

![](bbox=[0.18, 0.39, 0.82, 0.57])

# Figure 2. Graphical analysis of models.

Remark of Figure 2 depicts that the Decision Tree as well as Random Forest models demonstrated exceptional accuracy by achieving perfect scores across both classes. Other models also showed favourable performances with varying accuracy levels. Selecting the most suitable model should be based on specific task requirements and trade-offs.
The performance of various machine learning models to predict diabetic and non-diabetic cases was assessed using recall, precision, as well as F1 score metrics, as shown in Table 4.

Table 4. Evaluation parameters for diabetic and non-diabetic.

| Models | Diabetic Precision | Diabetic Recall | Diabetic F1score | Non-diabetic Precision | Non-diabetic Recall | Non-diabetic F1score |
|---|---|---|---|---|---|---|
| SVM | 1 | 0.39 | 0.56 | 0.95 | 1 | 0.97 |
| Random Forest | 1 | 1 | 1 | 1 | 0.99 | 1 |
| Logistic Regression | 0.84 | 0.63 | 0.72 | 0.97 | 0.99 | 0.98 |
| SGD | 0.62 | 0.76 | 0.68 | 0.98 | 0.96 | 0.97 |
| Naive Bayes | 0.45 | 0.65 | 0.53 | 0.97 | 0.93 | 0.95 |
| Decision Tree | 1 | 0.99 | 1 | 1 | 1 | 1 |
| KNN | 0.94 | 0.60 | 0.73 | 0.96 | 1 | 0.98 |