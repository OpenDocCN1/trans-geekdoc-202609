![](bbox=[0.14, 0.17, 0.86, 0.45])

FIGURE 12.9 Confusion matrix of AdaBoost classifier.

From the confusion matrix, it can be seen that out of 5,55,000 transactions 25 transactions resulted in false positives where the algorithm flagged a clean transaction as a fraudulent transaction and there were 78 fraudulent transactions the algorithm failed to detect.

# 12.4.4.3 XGBoost

Figure 12.10 shows the feature importance of the XGB tree.

As can be seen from Figure 12.10, the XGB Tree is placing the most weight on the errorBalanceOrig feature, i.e., it is most concerned with the error in balance at the origin side and will base its prediction mostly on this variable. Figure 12.11 is the confusion matrix of XGBT.

From the confusion matrix data, out of 5,55,000 transactions only 10 transactions resulted in false positives where the algorithm flagged a clean transaction as a fraudulent transaction, but there were only 6 fraudulent transactions the algorithm failed to detect.

# 12.4.4.4 ROC-AUC SCORE

Table 12.1 lists ROC-AUC values of each algorithm, in which Random Forest and XGBoost have the approximately same score of 0.998 whereas AdaBoost is slightly behind them by a 0.997 score.