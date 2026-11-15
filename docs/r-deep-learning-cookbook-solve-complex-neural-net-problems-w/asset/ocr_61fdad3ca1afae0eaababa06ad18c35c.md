# # How it works...

Model evaluation is a key step in any machine learning process. It is different for supervised and unsupervised models. In supervised models, predictions play a major role; whereas in unsupervised models, homogeneity within clusters and heterogeneity across clusters play a major role.

Some widely used model evaluation parameters for regression models (including cross validation) are as follows:

+   - Coefficient of determination
+   - Root mean squared error
+   - Mean absolute error
+   - Akaike or Bayesian information criterion

Some widely used model evaluation parameters for classification models (including cross validation) are as follows:

+   - Confusion matrix (accuracy, precision, recall, and F1-score)
+   - Gain or lift charts
+   - Area under ROC (receiver operating characteristic) curve
+   - Concordant and discordant ratio

Some of the widely used evaluation parameters of unsupervised models (clustering) are as follows:

+   - Contingency tables
+   - Sum of squared errors between clustering objects and cluster centers or centroids
+   - Silhouette value
+   - Rand index
+   - Matching index
+   - Pairwise and adjusted pairwise precision and recall (primarily used in NLP)

Bias and variance are two key error components of any supervised model; their trade-off plays a vital role in model tuning and selection. Bias is due to incorrect assumptions made by a predictive model while learning outcomes, whereas variance is due to model rigidity toward the training dataset. In other words, higher bias leads to underfitting and higher variance leads to overfitting of models.