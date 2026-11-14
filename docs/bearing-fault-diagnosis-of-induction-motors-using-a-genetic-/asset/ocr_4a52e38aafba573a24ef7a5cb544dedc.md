# Table 5. The genetic algorithm parameters settings for feature selection.

| Parameter Name. | Types/Values |
| :--- | :--- |
| Population Size. | 200 |
| Genome Length | 20 |
| Selection type | Roulette wheel |
| Crossover | 0.7 (Simple one-point crossover) |
| Mutation Probability | 0.03 (Uniform probability distribution) |
| Maximum Generation No. | 100 |

The classifier’s performance was assessed using the confusion matrix and receiver operation characteristic (ROC) curve presented in Figure 11 and Figure 12, respectively. The evaluation parameters shown in Equations (18)–(22) were calculated from this confusion matrix. In ROC, the area under curve (AUC) was used because it provides a perception of how accurately a classification model performs on the dataset. The range of the AUC curve was from 0.5 to 1, where 0.5 represents a classifier that has not performed better than random guessing, and 1 indicates a good model with no misclassifications. The nearer the value is to 1, the better the model.

![](bbox=[0.14, 0.36, 0.83, 0.73])

Figure 11. Confusion matrix for (a) KNN, (b) decision tree, and (c) random forest classifiers.