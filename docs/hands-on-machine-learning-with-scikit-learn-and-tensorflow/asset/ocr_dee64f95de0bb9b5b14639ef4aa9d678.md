# # Voting Classifiers

Suppose you have trained a few classifiers, each one achieving about 80% accuracy. You may have a Logistic Regression classifier, an SVM classifier, a Random Forest classifier, a K-Nearest Neighbors classifier, and perhaps a few more (see Figure 7-1).

| Logistic Regression | SVM Classifier | Random Forest Classifier | Other... |
| :--- | :--- | :--- | :--- |
| ⚙️ | ⚙️ | ⚙️ | Diverse predictors |

Figure 7-1. Training diverse classifiers

A very simple way to create an even better classifier is to aggregate the predictions of each classifier and predict the class that gets the most votes. This majority-vote classifier is called a *hard* voting classifier (see Figure 7-2).

![](bbox=[0.143, 0.545, 0.857, 0.836])

Figure 7-2. Hard voting classifier predictions