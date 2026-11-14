Fig. 4 depicts the ROC curve (Receiver-Operating-Characteristic curve) for the random forest classifier. The true positive rate (i.e., the recall rate or also referred to as sensitivity) is depicted on the y-axis, the x-axis shows the false positive rate.

![](bbox=[0.335, 0.225, 0.675, 0.385])

Fig. 4. The ROC curve of the random forest classifier.

# 4.4 Algorithm Comparison and Selection

While it is often argued that both described tree algorithms (i.e., boosted decision trees and random forests) tend to perfectly adapt their feature values and thus suffer often from overfitting, Breimann [5] showed that random forests are robust against overfitting, providing (among others) possibilities to set regularization parameters.

# 4.5 Evaluation, Results and Design Decision Revisited

It is worth to notice that due to the rather low ratio of the error samples (so-called minority class), we applied re-sampling methods [7, 8] to obtain a more balanced data set. The best results were achieved by down-sampling (i.e., reducing the data set size) in combination with a slight up-sampling, such that the error ratio raises up to nearly 18 %. There is no dominating feature among the most important features.

While several practical comparisons (e.g., [19]) show that the complex ANN outperforms random forests, the variety of important (but not dominating features) combined with their different results of interactions and the threat of overfitting might cause the predominance of random forests in our case.

Nevertheless, we stress that the best results of the random forests is based on the underlying data set and application use case with no indication as a general superiority of random forest classifiers to other classification algorithms, which was for instance argued in [18], but later contradicted (in terms of generalizability) in [17].