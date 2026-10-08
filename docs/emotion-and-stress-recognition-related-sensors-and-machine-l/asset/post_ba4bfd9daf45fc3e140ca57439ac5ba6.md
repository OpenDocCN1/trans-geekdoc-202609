
## 2.5.2. Static-Dynamic Classification

Static-dynamic classification takes into account the training method's time variations. A static model trains the data once and uses the trained model to classify a single feature vector. In a dynamic model, the system is updated continuously. Thus, dynamic models can obtain a sequence of feature vectors and catch temporal dynamics.

Multilayer perceptron (MLP) can be considered a static classifier. Likewise, an example of a dynamic classifier is hidden Markov methods (HMM) because it can classify a sequence of feature vectors.

## 2.5.3. Stable Unstable

Stable classifiers have low complexity and do not affect their performance with small variations of the training set. For example, Nearest Neighbors (kNN) is a common classifier. Unstable classifiers have high complexity and present considerable changes in performance with minor variations of the training set. Examples of unstable classifiers are linear support vector machine (SVM), multi-layer perceptron (MLP), and bilinear recurrent neural network (BLR-NN).

## 2.5.4. Regularized

Regularization consists of carefully controlling classifier complexity to prevent overtraining. Fisher LDA (RF-LDA), linear SVM, and basis function kernel for support vector machine (RBF-SVM) are examples of regularized classifiers.

## 2.5.5. General Taxonomy of Classification Algorithms

Another taxonomy divides classifiers using their properties to distinguish them into general types of algorithms as linear, neural networks, nonlinear Bayesian, nearest neighbor classifiers, and combinations of these (ensemble). Most of the specialized algorithms can be generated from these general types. Table 6 shows this taxonomy criterion with five different categories of general classifiers: (1) Linear, (2) neural networks, (3) nonlinear Bayesian, (4) nearest neighbor classifiers, and (5) combinations of classifiers or ensemble [4,5].

All general classifiers have characteristics of each of the previously mentioned framework models. For instance, SVM is discriminative, static, stable, and regular; HMM is generative, dynamic, unstable, and not regular; and kNN is discriminative, stable, and not regular.

Consequently, the suggested guidelines for classifier selection are also applicable in this categorization. Table 6 presents the usage statistics of classifiers in the 2015–2020 literature. The following are the most commonly used classifiers. Neural networks CNN (46.16%), Linear classifiers SVM (30.3%), and LDA (5.5%), Nearest Neighbors kNN (4.5%), and Ensembled classifier AdaBoost (3.9%).

### Table 6. Categories of general classifiers.

| Category of Classifier | Description | Advantages | Limitations | Usage Statistics |
| :--- | :--- | :--- | :--- | :--- |
| Linear | Discriminative algorithms that use linear functions. | These algorithms have reasonable classification properties. | Linear algorithms tend to have poor outcomes in complex high-dimensional data. | 5.50<br>1.40<br>0.02 |
| Neural networks (NN) | Discriminative algorithms that recognize relationships in nonlinear decision boundaries. | NN generally yields good classification accuracy. | Sensitive to overfitting with small sample data. | 1.60<br>1.20<br>46.16<br>0.40<br>0.12<br>0.10 |
| Bayesian classifier | Generative classifiers predict decision. | Generative classifiers select uncertain samples efficiently. | For Bayesian models, the covariance cannot be ignored and there is not enough training data. | 0.10<br>0.30 |
| Nearest neighbor classifier | Discriminative algorithms that classify cases based on similarity to others. | KNN has excellent performance for low-dimensional features. | KNN is known for poor performance in high-dimensional features. | 0.1 |
| Combination of classifiers (ensemble-learning) | Combined classifiers using boosting, voting, or stacking. | Voting classes have higher accuracy which reduces final class label errors. | Variance reduction leads to increase of classification. | Quality measures are of application dependent. |
| | | | | 2.1<br>0.2<br>3.9 |

## 2.6. Performance Evaluation

Results must be reported consistently so that different research groups can understand and compare them. Hence, evaluation procedures need to be chosen and described accurately [119]. The evaluation of the classifier's execution involves addressing performance measures, error estimation, and statistical significance testing [120]. Performance measures and error estimation configure the fulfillment rate of the classifier's function. The most recommended performance evaluation measures are shown in Table 7. They are confusion matrix, accuracy, error rating, and other measures obtained from the confusion matrix, such as the recall, specificity, precision, Area Under the Curve (AUC), and F-measure. Other performance evaluation coefficients are Cohen's kappa (κ) [121], information transfer rate (ITR) [65] and written symbol rate (WSRB) [121].

Performance evaluation and error estimation may need to be complemented with a significance evaluation. This is because there are general approaches that handle arbitrary class distributions to verify accuracy values that lie significantly above certain levels. Used methods are the theoretical level of random classification or classes are imbalanced (labeled EEG signals typically are). Therefore, significance classification is essential; general approach and adjusted Wald confidence interval for classification accuracy.

The theoretical level of random classification test results for randomness is the sum of the products between the experimental results' classification probability and the probability calculated if all the categorization randomly occurs ($p_0$ = classification accuracy of a random classifier). This approach can only be used after the classification has been performed [122].

Adjusted Wald confidence interval gives the lower and upper confidence limits for the probability of the correct classification, which specifies the intervals for the classifier performance evaluation index [123].

### Table 7. Conventional performance evaluation methods for BCI

- **Confusion matrix**: The confusion matrix presents the number of correct and erroneous classifications specifically for each class. It gives insights into the predictions and errors for each class. Results are difficult to compare and discuss, without some parameters related to the confusion matrix.

- **Accuracy**: The accuracy is the probability of correct classification. It works well if the classes are balanced, i.e., when there are an equal number of samples belonging to each class. Accuracy and error rate are not used when one class occurs more frequently than another; the evaluation may appear biased. In a 2-class problem, the confidence level is 95%, but with a confidence level depending on the level of agreement.

- **Error Rate**: In a certain number of repeated measures, the probability that an incorrect classification has been made.

- **Cohen's Kappa ($\kappa$)**: It is an evaluation between nominal scales. It measures the agreement between a true class and the predicted class in a period agreement. It takes into account the high agreement due to random chance. Cohen's kappa reflects the theoretical chance. This index evaluates the classifier. If it has a low value, the confusion matrix would show high agreement because it uses the information from random chance.

- **Recall (Sensitivity)**: Additionally, called Recall, identifies the true positive rate related to the sum of true positives plus false positives. The Recall measures how often a classifier correctly classifies a positive result. It prioritizes simple percentages.

- **Specificity**: Specificity measures the proportion of identified true negatives over false positives. Specificity measures how often a classifier correctly classifies a negative result.

- **Precision**: Precision also referred to as Positive Predictive Value, measures the fraction of true positives over the sum of true plus false positives. Precision measures the fraction of correct classifications. Precision should not be used when the positive class is one only, and the majority of positive samples is less critical to the problem. Precision should not be used when the positive class is the correct detection and the fraction of samples biases it.

- **False Positive Rate (FPR)**: Rate of False Positive Rate (FPR), is equal to 1 - Specificity.
