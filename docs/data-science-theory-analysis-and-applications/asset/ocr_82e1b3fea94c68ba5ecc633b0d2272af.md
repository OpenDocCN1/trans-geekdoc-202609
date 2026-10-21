Classification of the extracted feature was conducted by training a SVM. SVM is a supervised learning algorithm that is primarily used for classification, regression, and outlier detection tasks on both simple and complicated data [43]. It works by finding an optimum separating hyperplane (OSH) that acts as a boundary that separates classes of data; this is achieved by solving an optimization problem [44]. As a supervised learning algorithm, it learns to classify unseen data based on a set of labeled training data. Thus, the training phase is used to build a model; thereafter, new unseen data is mapped to one of those learned classes by computing the dot product of the model (weights) and image-data features [44].

Moreover, the evaluation was conducted via k-fold cross-validation (CV) techniques, where data is subsampled into k parts equally. CV is a statistical means of evaluating learning algorithms [45] that help to avoid sampling error. A special case of K-fold (where k=10) CV is used, where k−1 is used for training, and the remaining split is used for validation (testing). The iteration continues until all the subsamples are exhausted in such a way that each subsample is used for both training and testing, and finally, the average of all the tests gives the result as expressed mathematically in Equation (9.2) later

Accuracy = 1/n Σ_{i=1}^{n} A_i  (9.2)

where n is the number of folds and A_i is the accuracy obtained in each iteration.

# 9.5 RESULTS AND DISCUSSION

The contingency table in Table 9.2 shows the summary of all the results obtained. The contingency table was used to display the performace output of the classifier, where the columns correspond to original classes fed into the algorithm, and the rows are the corresponding predicted outputs by the algorithm.

The labels (a–c) in Table 9.2 mark the individual class category. Healthy skin images were labeled as “a,” superficial burn images were labeled as “b,” and full-thickness burn images were labeled as “c”. The diagonal value at cell position (a, a) gives the correct predicted samples of healthy skin (660 images), the value at cell position (b, b) gives the exact predicted samples of superficial burns (660), and the one at cell (c, c) is the correct predicted full-thickness images (659). Any other predictions other than those mentioned in the three cells are misclassified instances.

# 9.5.1 TERMS RELATED TO CONTINGENCY TABLE

To evaluate the result obtained in the contingency table as presented in Table 9.2, there are some related terms that need to be defined. These terms include true negatives (TN) that refer to actual negative samples (healthy images) of a class that are predicted as such (refer to cell [a, a] in Table 9.2). Negative images predicted as positives are referred to as false positives (FP). Those positive samples that were predicted as negatives are referred to as false negatives (FN). Burn images that are