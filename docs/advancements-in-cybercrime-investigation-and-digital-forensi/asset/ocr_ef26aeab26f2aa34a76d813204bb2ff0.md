multiple decision trees (Tanwar, 2018) and combines them to get more accurate. Figure 12.6 shows the feature importance considered by the random forest. It can be seen from the figure the random forest is placing the most weight on the newBalanceOrig variable, i.e., it is most concerned with the new balance of the origin of the transaction and will base its prediction mostly on this variable (Figure 12.7).

![](bbox=[0.12, 0.28, 0.88, 0.6])

FIGURE 12.6 Feature importance for random forest.

From the confusion matrix, it can be seen that out of 5,55,000 transactions 0 transactions resulted in false positives where the algorithm flagged a clean transaction as a fraudulent transaction, and there were only 6 fraudulent transactions the algorithm failed to detect. This algorithm was able to detect every valid transaction and showed an exceptional performance.

# 12.4.4.2 ADABOOST

The basic idea of Ada-boost is to line the weights of classifiers and train the info sample in each iteration such it ensures the accurate predictions of negative observations. Figure 12.8 shows the feature importance taken into account by the AdaBoost. It can be seen from the figure that the AdaBoost is placing the most weight on the errorBalanceOrig feature, i.e., it is most