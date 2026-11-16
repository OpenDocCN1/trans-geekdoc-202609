# Table 2. Classification report for selected features for the models

| Class | Decision Tree Precision | Decision Tree Recall | Decision Tree F1-Score | Random Forest Classifier Precision | Random Forest Classifier Recall | Random Forest Classifier F1-Score | Gradient Boosting Precision | Gradient Boosting Recall | Gradient Boosting F1-Score |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Paroxysmal Positional Vertigo | 1 | 0.95 | 0.97 | 1 | 0.89 | 0.94 | 1 | 0.95 | 0.97 |
| AIDS | 1 | 0.93 | 0.96 | 1 | 1 | 1 | 1 | 0.83 | 0.91 |
| Arthritis | 1 | 0.9 | 0.95 | 1 | 1 | 1 | 1 | 0.9 | 0.95 |
| Diabetes | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| Tuberculosis | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| hepatitis A | 1 | 0.02 | 0.04 | 0 | 0 | 0 | 1 | 1 | 1 |

From the Algorithm-1 first we choose the feature from the given dataset defined as ‘F’ and name that as ‘Fm’, which is a member based on DFS algorithm. If the selected feature is a member of the selected decision group, then make a separate function called ‘Fbm.’ Set ‘Fi’ to select the next feature from the given dataset. Finally compute the average distance of selected feature from the decision tree nodes and return the Fm. Furthermore, the number of unique diseases and their occurrences are calculated by using the below equation:

```
\( F_E = - \sum_{i=1}^{n} P_i * log P_i \) (1)
```

And the Selection of FBM is calculated by using the below equation:

```
\( F_{BM} = 1 - \sum_{i=1}^{n} P_i^2 \) (2)
```

Furthermore, for a better understanding of the data, Figure 2 shows the framework with a detailed step involved.

![](bbox=[0.109, 0.574, 0.791, 0.812])

# Figure 2. Proposed framework for multi-disease prediction.

In the above Figure 2, the first step is dataset acquisition, then selection of appropriate data features containing comprehensive symptom-based disease information is done. While doing this task the major considerations taken into the accounts are: