![](bbox=[0.11, 0.07, 0.88, 0.36])

Figure 4.4 Random forest model. In a random forest model, a relatively large dataset is divided into several small datasets. This process is called bootstrapping and bagging. Then small datasets are used to develop the decision trees. The test dataset is applied on all decision trees and the predicted values are aggregated to make the final prediction.

Several initial studies developed sparse linear regression models to predict drug sensitivity. These studies usually applied ridge regression [42, 45, 47] and elastic net algorithms [10, 14, 16, 32]. Although the performance of those models was poorly generalized, those studies generated a massive amount of pharmacogenomic data that were useful for follow-up studies.

# 4.7 RANDOM FOREST AND KERNEL FUNCTIONS IN DRUG SENSITIVITY PREDICTION

Decision trees are popular supervised learning algorithms and are widely used for clinical decision analysis [63]. In a decision tree, model data are taken in the root node of the tree and, according to a test rule, keep growing until a decision can be drawn [64]. The beauty of a decision tree is that each step can be understood, interpreted, and visualized. A random forest uses a group of decision trees to solve relatively complex problems. In this method, data are randomly divided into small sets and then applied to decision trees (Figure 4.4). Prediction is made by the most chosen value (classification) or by the mean/median value (regression) from the decision of all trees. This process eventually increases the prediction accuracy [65].

Stetson et al. used pharmacogenomic data from the Genomics of Drug Sensitivity in Cancer (GDSC), Cancer Cell Line Encyclopedia (CCLE), and the National Cancer Institute (NCI) datasets and used 1000 selected genes to develop and compare ML models [33]. They found that the random forest model outperforms several other