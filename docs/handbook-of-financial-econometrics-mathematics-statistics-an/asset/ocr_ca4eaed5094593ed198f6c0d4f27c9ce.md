Furthermore, to investigate if the algorithm is stable and if the overfitting problem exists, we calculate the cross-validation score. We further split the 70% training set into ten subsets, and fit the algorithm using nine of these subsets being the training data, and one set being the testing data. Rotating which set is the testing set, the average of these ten prediction accuracies is the cross-validation score.

Our selection rule for optimal tuning parameters goes as follows. We first plot the testing and cross-validation scores for various combinations of tuning parameters. The optimal tuning parameters are the simplest to achieve the highest testing scores, whereas the cross-validation scores are later used to check if the overfitting problem exists.

The above procedures give a simple rule to select the optimal tuning parameters. We remark that there are other alternatives to select the optimal tuning parameters. For instance, the optimal combination of tuning parameters are selected to maximize the performance measure (such as the F1-score or AUC).

Figure 101.6 compares testing and cross-validation scores against various combinations of tuning parameters: k ranging from 1, 21, 41, ..., 81, and two weighting schemes (uniform weight and distance weight). Testing scores with uniform and distance weighting are about the same, which are also close

![](bbox=[0.18, 0.7, 0.85, 0.9])

Figure 101.6: Validation curves of the k-nearest neighbors against k with uniform weight and distance weight using training data and cross-validation of the credit card dataset.