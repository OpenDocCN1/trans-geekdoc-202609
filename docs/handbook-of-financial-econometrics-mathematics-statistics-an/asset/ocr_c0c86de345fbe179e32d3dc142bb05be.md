# Table 21.2: (Continued)

Algorithm description:

+   - Decision Table: Decision Table Rules;
+   - Simple CART: Simple Classification and Regression Trees;
+   - Jrip: Repeated Incremental Pruning Rules;
+   - Logistic: Linear Logistic Regression Functions;
+   - J48: C4.5 Decision Trees;
+   - Bayesnet: Bayesian network;
+   - Naivebayes: Naïve Bayes;
+   - Multilayer perception: Neural Network Functions;
+   - Nbtree: Naïve Bayes Trees;
+   - SMO: Sequential Minimal Optimization Functions;
+   - RBFNetwork: Radial Basis Functions Network;
+   - LibSVM: Support Vector Machine Functions; and
+   - Ibk: K-nearest-neighbor Lazy.

uses K-nearest-neighbor. We use the decision table and repeated incremental pruning to produce error reduction (RIPPER) for the rules category (Peng et al., 2009). Each of these classifiers has pros and cons and we want to see which methods perform better in our bankruptcy context. For executing each of these data mining techniques, refer to Olson and Shi (2007).

We use 11 performance criteria to evaluate the classification performance: overall accuracy, true positive, false positive, true negative, false negative, precision, recall, F-measure, AUC, Kappa statistics (KapS), and mean absolute error (MAE) score. Accuracy is one of the most widely used classification performance metrics. It equals the ratio of correctly predicted records to the total records in the dataset/class. Overall accuracy = (TN+TP)/(TP+FP+FN+TN), true positive rate/sensitivity = TP/(TP+FN), false positive rate = FP/(FP+TN), true negative rate/specificity = TN/(FP+TN), false negative rate = FN/(FN+TP) where TP FP, TN and FN are defined below.

+   - TP (True Positive): The number of bankrupt firms correctly classified.
+   - FP (False Positive): The number of records non-bankrupt firms incorrectly classified as bankrupt firms.
+   - TN (True Negative): The number of non-bankrupt firms correctly classified.
+   - FN (False Negative): The number of bankrupt firms incorrectly classified as non-bankrupt firms.