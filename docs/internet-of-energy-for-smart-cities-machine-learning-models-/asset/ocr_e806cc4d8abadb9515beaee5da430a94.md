K-Fold Cross-Validation: this is a powerful method to avoid overfitting problems, especially in classification problems. The data is segmented to k number partitions, as shown in Figure 8.14. In each iteration, one segment is used as the validation set and the others as the training set. This is the most favorable method to select the best model in practice. K-fold cross-validation method provides a more structured approach to split the original dataset into training and validation datasets so as to avoid the overfitting problem by giving the variability in overall performance compared to suing an individual partition of the data.

![](bbox=[0.15, 0.275, 0.85, 0.49])

**Figure 8.14** K-fold cross-validation method

Leave-one-out cross-validation: it is a particular case of cross-validation where the number of partitions (k) equals the dataset’s size (N), number of instances, or samples in the dataset. Thus, the validation data set has precisely one sample in the learning model and all other samples as a training dataset for each iteration, similar to the statistical jack-knife estimation. The error on the validation set is not only used to decide when to stop training and avoid overfitting but also is used to determine the model’s generalization performance.

# ## 8.5.3 MODEL PERFORMANCE'S EVALUATION METRICS

The metrics that are used in each machine learning algorithms are different from each other. In the following, the most used metrics in classification and regression algorithms are discussed.