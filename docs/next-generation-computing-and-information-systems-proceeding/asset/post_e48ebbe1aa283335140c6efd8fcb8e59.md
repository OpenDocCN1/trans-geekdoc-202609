
## 3.5 Applied classifiers

Various machine as well as deep learning algorithms have been used as a classifier to detect hypertension in individuals.

### 3.5.1 Voting classifier

This is an approach to machine learning where the results of numerous independent classifiers are combined to provide a final prediction. The individual classifiers in the ensemble are trained on the same dataset. Each classifier interprets these features and delivers a binary prediction concerning the presence or absence of hypertension. The voting classifier then amalgamates these individual predictions using diverse techniques like majority voting or weighted voting and produces a final decision (Angayarkanni and Hemalatha 2023). Let LR(x) and RF(x) represent the prediction probability of logistic regression and random forest classifier respectively. The soft voting ensemble combines all these probabilities and predicts the class on the basis of highest average probability. The ensemble's prediction \(\widehat{y}\) for a given input x can be computed by Equation (3):

\[
\widehat{y} = \arg\max_i \left( \frac{1}{2} \sum_{j=1}^2 p_i(x) \right)
\]

where i denotes class labels as 0 and 1, \(p_i(x)\) represent the probability estimate that the input x belongs to class i as predicted by each individual classifier, as shown in Equations (4 and 5):

\[
p_0(x) = \frac{1}{1 + e^{-LR(x)}}
\]

\[
p_1(x) = RF(x)
\]

### 3.5.2 Gradient Boosting: LGBM/XGBoost/CatBoost/AdaBoost

In the domain of hypertension detection, these machine learning techniques did well in extracting meaningful patterns from complex medical data. Gradient boosting builds decision trees where each subsequent tree focuses on correcting the errors of the preceding ones and enhances the accuracy of model. CatBoost stands for categorical boosting and works efficiently with the medical data which is often rich in categorical variables (Chaplot et al. 2023). LGBM, optimizes the building of decision trees in a leaf-wise fashion and significantly improves training speed and makes it suitable for large healthcare dataset. XGBoost, an optimized version of gradient boosting, incorporates regularization techniques, prevents overfitting which thereby improves generalization on unseen data. AdaBoost, on the other hand, emphasizes difficult-to-classify instances by assigning higher weights to misclassified samples, and enhances the performance of the algorithm where identifying subtle patterns is crucial, such as in hypertension detection (Singh et al. 2023). The mathematical equation for AdaBoost's final prediction F(x) in the context of multiclass classification with \(\alpha\) as weight and \(h_m^k(x)\) as prediction of weak learners is presented in Equation (6).

\[
F(x) = \arg\max_k \left( \sum_{m=1}^M a_m h_m^k(x) \right)
\]

These algorithms collectively empower healthcare professionals by accurately recognizing intricate relationships within patient data and aid in early hypertension diagnosis and tailored treatment strategies.

### 3.5.3 MLP

It is a computational model inspired by the human brain which is adept at discerning intricate patterns within vast datasets. The input layer of the MLP receives essential features like age, cholesterol levels, restbps, etc. Through hidden layers, these inputs use series of weighted computations and nonlinear transformations which allow the network to capture complex relationships between these variables. The output layer after employing a sigmoid activation function produces a prediction between 0 and 1 and represents the likelihood of an individual having hypertension (Koul et al. 2022). Mathematically, it can be computed as shown in Equation (7)

\[
y = f(Wx^T + b)
\]

where activation function is f, W defines the set of parameters, x in the input vector and b is the bias vector.

## 3.6 Evaluative metrics

Precision, accuracy, recall, as well as F1 score are fundamental metrics used for assessing the performance of classifiers (Kumar et al. 2021) (Table 1).

Table 1. Formulae of evaluative parameters.

| Metrics | Formulae |
|---|---|
| Accuracy | $\frac{True Positive + True Negative}{True Positive + True Negative + False Positive + False Negative}$ |
| Precision | $\frac{True Positive}{True Positive + False Positive}$ |
| Recall | $\frac{True Positive}{True Positive + False Negative}$ |
| F1 score | $2 \times \frac{Precision \times Recall}{Recall + Precision}$ |

## 4 RESULTS

In this section, the performance of the applied learning approaches has been assessed using the parameters listed in sec 3.6. Figure 4 shows a confusion matrix of size 2x2 that has been generated to compute the predicted and actual value of the binary class of hypertension dataset for different methods.

![](img/9eefc6d2972274efeb1680c6a31895e5_238_0.png)

Figure 4. Confusion matrix of the applied classifiers.

At first, the values of the parameters such as accuracy, recall, precision, as well as F1 score for the entire dataset have been generated based on the confusion matrix values to evaluate the performance of the employed algorithms (Table 2).

Table 2. Analysis of classifiers using hypertension dataset.

| Classifiers | Accuracy | Precision | Recall | F1Score |
| :--- | :--- | :--- | :--- | :--- |
| Voting Classifier | 95.39 | 0.96 | 0.95 | 0.95 |
| Gradient Boosting | 98.43 | 0.99 | 0.98 | 0.98 |
| Adaboost | 91.56 | 0.92 | 0.91 | 0.91 |
| XGBoost | 100 | 1.00 | 1.00 | 1.00 |
| CatBoost | 100 | 1.00 | 1.00 | 1.00 |
| LGBM | 100 | 1.00 | 1.00 | 1.00 |
| MLP | 89.86 | 0.92 | 0.89 | 0.89 |

The Voting Classifier exhibits an accuracy of 95.39%, with balanced precision, recall, and F1 score values at 0.96, 0.95, and 0.95, respectively. Gradient Boosting surpasses others with an impressive accuracy of 98.43% and outstanding precision at 0.99, recall at 0.98, and F1 score at 0.98. AdaBoost, whereas having a relatively lower accuracy at 91.56%, still maintains good precision of 0.92, F1 score and recall of 0.91. CatBoost, XGBoost, and LGBM demonstrate flawless performance with a perfect accuracy of 100% and impeccable precision, recall, and F1 score all at 1.00. Lastly, the MLP model lags behind others with an accuracy of 89.86% and slightly lower precision, recall, and F1 score at 0.92, 0.89, and 0.89. In summary, Gradient Boosting, XGBoost, CatBoost, and LGBM stand out as top performers by achieving a perfect accuracy and optimal precision, recall, and F1 score. Besides, the execution of the algorithms have been evaluated for different two classes of the dataset i.e. hypertensive (class 1) and non-hypertensive (class 0) whose results are mentioned in Table 3.

Table 3. Examining the performance of classifiers for different classes of hypertension dataset.

| Classifiers | Precision | Recall | F1Score | Precision | Recall | F1Score |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| | \multicolumn{3}{c}{Hypertensive} | \multicolumn{3}{c}{Non-hypertensive} |
| Voting Classifier | 0.96 | 0.93 | 0.94 | 0.94 | 0.97 | 0.95 |
| Gradient Boosting | 1.00 | 0.96 | 0.98 | 0.97 | 1.00 | 0.99 |
| Adaboost | 0.91 | 0.90 | 0.91 | 0.92 | 0.93 | 0.92 |
| XGBoost | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 |
| CatBoost | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 |
| LGBM | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 |
| MLP | 0.99 | 0.78 | 0.87 | 0.85 | 0.99 | 0.92 |

Voting classifier performed well with hypertensive and non-hypertensive class of the dataset by computing 0.96 and 0.97 as a precision, 0.93 and 0.97 as a recall , which results in 0.94 and 0.95 F1 score respectively. Likewise, Gradient Boosting achieved a perfect precision (1.00) for hypertensive case and high recall (0.96), leading to a strong F1 score of 0.98. For non-hypertensive cases, it exhibits perfect recall and slightly lower precision, resulting in a F1 score of 0.99. Adaboost performed reasonably well with balanced precision and recall for both classes, leading to an F1 score of 0.91 for hypertensive and 0.92 for non-hypertensive cases. XGBoost, CatBoost, and LGBM outperform with perfect precision, recall, and F1 score for both classes which indicates their flawless performance in classifying both
