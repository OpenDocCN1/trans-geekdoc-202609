Figure 70: Mean F1-scores by transformations

![](bbox=[0.296, 0.183, 0.773, 0.452])

z-scores, results that contradict my expectation of the relative frequency hav-ing the lowest outcomes. The transformations with the highest results are the applied logarithmic transformation with different bases, without a statistical difference between them. This shows that, regardless of the base used (e, 10, or 1000), the logarithmic transformation of linguistic data provides the results of the classification for subgenes. The proposed concatenations of steps (tfidf-zscores and log10-zscores) do not seem to result in any improvement.

The third parameter evaluated the classifiers: support vector machines (SVC), logistic regression (LR), decision trees (DT) and k-nearest neighbors (KNN). Two classifiers obtain the highest results in nine of twenty-three subgenes (SVC and LR), four by DT, and one by KNN. These results are also observed when all combinations are taken in account.

Two classifiers in, addition, do clearly lower results in Figure 71: decision trees (which, in addition, cover perfect results with the whiskers) and k-nearest neighbors (with results around the baseline). The differences between these two and the other algorithms are statistically significant (p-value < 0.001), while there is no statistical significance between the results of log-regression and support vector machines. Besides these four algorithms, several trials were run using random forest, which is notably more time-con-