
## Table 21.2: (Continued)

| Algorithm | AUC | Overall accuracy | F-measure | Mean absolute error |
|---|---|---|---|---|
| bayesnet | 0.94 | 85.42 | 0.8 | 0.15 |
| naivebayes | 0.74 | 42.68 | 0.55 | 0.57 |
| multilayer perceptron | 0.87 | 77.56 | 0.68 | 0.23 |
| nbtree | 0.88 | 81.94 | 0.73 | 0.19 |
| SMO | 0.73 | 75.58 | 0.63 | 0.24 |
| RBFNetwork | 0.63 | 66.13 | 0.17 | 0.42 |
| libSVM | 0.65 | 74.97 | 0.47 | 0.25 |
| ibk | 0.77 | 78.43 | 0.68 | 0.22 |

| Kappa | TPR | FPR | TNR | FNR | Precision | Recall | Time training | Time testing |
|---|---|---|---|---|---|---|---|---|
| 0.63 | 0.75 | 0.12 | 0.88 | 0.25 | 0.77 | 0.75 | 0.23 | 0 |
| 0.63 | 0.76 | 0.13 | 0.87 | 0.24 | 0.76 | 0.76 | 0.21 | 0 |
| 0.64 | 0.8 | 0.14 | 0.86 | 0.2 | 0.76 | 0.8 | 0.09 | 0 |
| 0.57 | 0.71 | 0.14 | 0.86 | 0.29 | 0.73 | 0.71 | 0.28 | 0 |
| 0.67 | 0.78 | 0.11 | 0.89 | 0.22 | 0.8 | 0.78 | 0.04 | 0 |
| 0.68 | 0.83 | 0.13 | 0.87 | 0.17 | 0.78 | 0.83 | 0.02 | 0 |
| 0.1 | 0.96 | 0.85 | 0.15 | 0.04 | 0.4 | 0.96 | 0.01 | 0 |
| 0.51 | 0.7 | 0.19 | 0.81 | 0.3 | 0.67 | 0.7 | 10.07 | 0 |
| 0.6 | 0.76 | 0.15 | 0.85 | 0.24 | 0.71 | 0.76 | 5.37 | 0 |
| 0.45 | 0.64 | 0.18 | 0.82 | 0.36 | 0.65 | 0.64 | 0.08 | 0 |
| 0.08 | 0.15 | 0.08 | 0.92 | 0.85 | 0.23 | 0.15 | 0.08 | 0 |
| 0.35 | 0.33 | 0.03 | 0.97 | 0.67 | 0.87 | 0.33 | 0.11 | 0.01 |
| 0.52 | 0.7 | 0.17 | 0.83 | 0.3 | 0.67 | 0.7 | 0 | 0.01 |

Variable Descriptions:

AUC: Area under Receiver Operating Characteristic;
Overall Accuracy: Percentage correctly classified as bankrupt firms;
F-measure: The harmonic mean of precision and recall;
Mean Absolute Error: The predictions deviate from the true probability;
Kappa: Measure that estimates the similarity between the members of ensemble in multi-classifier systems;
TPR: True positive rate in %;
FPR: False positive rate in %;
TNR: True negative rate in %;
FNR: False negative rate in %;
Precision: The number of classified fault-prone modules that are fault-prone;
Recall: Fault-prone modules that are correctly classified in %;
Time Training: Time training in seconds; and
Time Testing: Time testing in seconds.

## Table 21.2: (Continued)

Algorithm description:

- Decision Table: Decision Table Rules;
- Simple CART: Simple Classification and Regression Trees;
- Jrip: Repeated Incremental Pruning Rules;
- Logistic: Linear Logistic Regression Functions;
- J48: C4.5 Decision Trees;
- Bayesnet: Bayesian network;
- Naivebayes: Naïve Bayes;
- Multilayer perceptron: Neural Network Functions;
- Nbtree: Naïve Bayes Trees;
- SMO: Sequential Minimal Optimization Functions;
- RBFNetwork: Radial Basis Functions Network;
- LibSVM: Support Vector Machine Functions; and
- Ibk: K-nearest-neighbor Lazy.

uses K-nearest-neighbor. We use the decision table and repeated incremental pruning to produce error reduction (RIPPER) for the rules category (Peng et al., 2009). Each of these classifiers has pros and cons and we want to see which methods perform better in our bankruptcy context. For executing each of these data mining techniques, refer to Olson and Shi (2007).

We use 11 performance criteria to evaluate the classification performance: overall accuracy, true positive, false positive, true negative, false negative, precision, recall, F-measure, AUC, Kappa statistics (KapS), and mean absolute error (MAE) score. Accuracy is one of the most widely used classification performance metrics. It equals the ratio of correctly predicted records to the total records in the dataset/class. Overall accuracy = (TN+TP)/(TP+FP+FN+TN), true positive rate/sensitivity = TP/(TP+FN), false positive rate = FP/(FP+TN), true negative rate/specificity = TN/(FP+TN), false negative rate = FN/(FN+TP) where TP, FP, TN and FN are defined below.

- TP (True Positive): The number of bankrupt firms correctly classified.
- FP (False Positive): The number of records non-bankrupt firms incorrectly classified as bankrupt firms.
- TN (True Negative): The number of non-bankrupt firms correctly classified.
- FN (False Negative): The number of bankrupt firms incorrectly classified as non-bankrupt firms.

Type-I and Type-II errors are also ratios using TP, FP, TN, and FN as defined above. A Type-I error equals $\frac{FN}{FN+TN}$, and Type-II error = $\frac{FP}{FP+TP}$. There are two types of errors (Type-I and Type-II) involved in prediction studies. A Type-I error refers to a false rejection error. For example, in a bankruptcy prediction study, we reject the null hypothesis that a firm is a non-bankrupt firm even though the firm is a bankrupt firm. This type of error will be very costly for decision makers. A Type-II error is a false acceptance error. For example, we predict a firm to be a bankrupt firm, even though the firm is a non-bankrupt firm. In the Type-II error case, the cost of misclassification is not as severe as in the Type-I error case. For our study, we focus on Type-I errors because the cost of misclassifying can be significant. The receiver operating characteristic (ROC) measures trade-offs between TP and FP rates and the area under ROC (AUC) shows the accuracy of the classifier and the larger the area, the better the classifier. For other metrics, refer to Peng et al. (2009).

Since training results indicate how well the classification model fits the training set and test results reflect the real predicting power of the classification model, the following tables only summarize the 11 metrics for test sets. The standard 10-fold cross-validation process is applied to all classifiers. The standard leave-one-out validation process is applied to LDA.

Based on the overall accuracy rate of both years using all variables, Bayesnet shows 85.42% of overall accuracy with 94% of AUC. Next, the J48 decision tree using C4.5 shows 85.42% of overall accuracy, followed by the decision table with 83.52% of overall accuracy. Interestingly, the overall accuracy rate of the decision table is 85.11% with only 13 financial ratios compared to 83.52% with all variables. In other cases, usual overall accuracy rates are higher for classifiers using all variables. Therefore, we focus on the results of overall variables for further discussions. For Bayesnet, the F-measure is 80%, 0.15 of mean absolute error, and the Kappa rate is 68%, precision is 78%, recall is 83%, training time is 0.02 and testing time is close to 0. Overall, our top data mining models are very effective and efficient and overall prediction rates are close to 85% using 2008 and 2009 US data. Most previous studies show lower than 85% of bankruptcy prediction rates using various methods and our results imply that bankruptcy prediction rates after SOX is improved over pre-SOX rates.

## 21.1.4 Summary and conclusions

In this paper, we used 13 data mining approaches to predict bankruptcy after SOX implementation using 2008-2009 US data with 13 financial ratios and internal control weaknesses, dividend payout, and market return variables. The data mining approaches have recently been applied to several bankruptcy prediction studies (Kwak et al., 2012a, 2012b). This approach has proven to be robust and powerful even for a large sample size using a huge financial database. The results of the Bayesnet approach in our bankruptcy study are better in overall accuracy compared with previous bankruptcy studies before SOX implementation.

Based on overall accuracy and AUC, Bayesnet and the decision table are promising classifiers, but based on Type-I and Type-II error rates, Bayesnet is the best classifier in our bankruptcy context. The Type-I error rate for Bayesnet is 16.35% (23.15% for the decision table) and the Type-II error rate is 13.54% (13.79% for the decision table) as we calculated from Table 54.2, Panel B using all variables. A Type-I error rate is costlier for decision makers. We may need to add more data and variables to improve our study. We may apply similar approaches to other accounting or finance contexts such as bankruptcy prediction using other countries’ data (e.g., Kwak et al., 2012a, 2014), predicting internal control weaknesses (e.g., Kwak et al., 2009), auditor changes, and audit opinion prediction studies.

## 21.2 Bankruptcy Prediction for Korean Firms after the 1997 Financial Crisis: Using a Multiple Criteria Linear Programming Data Mining Approach

### 21.2.1 Introduction

Recently many applications of data mining have been used in business areas such as personal credit card default prediction, consumer buying pattern prediction, and firm bankruptcy prediction. As one of the major tasks of data mining, multiple criteria mathematic programming-based classification has numerous business applications, especially in credit risk analysis (Peng et al., 2008). The purpose of our study is to propose a multiple criteria linear programming (MCLP) approach to predict firm bankruptcy using Korean financial data after the 1997 financial crisis. Korea’s 1997 financial crisis was derived from foreign currency shortages in the banking industry, but high leverage ratios and increased labor costs compared with China were other major contributing factors in their financial problems (Kim and Lee, 2002). There was a significant increase in firm bankruptcy after this financial crisis and this situation provides opportunity for our bankruptcy study.

Data mining can be achieved by association, classification, clustering, and predictions. From the mathematical point of view, the algorithms of data
