
### 9.4.1 Boosting

Boosting works by training a sequence of weak learners, each of which is trained on a weighted version of the training data. The weights of the training data are adjusted after each weak learner is trained, so that the next weak learner focuses on the data points that were misclassified by the previous weak learner. This process is repeated until a desired level of accuracy is reached.

One of the most popular boosting algorithms is AdaBoost (adaptive boosting). AdaBoost works by assigning weights to each training example, such that the examples that are misclassified by the current weak learner are given more weight in the training of the next weak learner. This process is repeated until a desired level of accuracy is reached.

Boosting has been shown to be effective in a variety of machine learning tasks, including classification, regression, and ranking. It is particularly well-suited for tasks where the training data is noisy or imbalanced.

Some examples of boosting in AI:
* In **spam filtering**, boosting can be used to identify spam emails. A weak learner might be trained to identify common spam words, such as “free” or “money”. The next weak learner would then be trained on the data that was misclassified by the first weak learner. This process would continue until a desired level of accuracy is reached.
* In **fraud detection**, boosting can be used to identify fraudulent transactions. A weak learner might be trained to identify transactions that are likely to be fraudulent, such as transactions that are made from new accounts or that involve large amounts of money. The next weak learner would then be trained on the data that was misclassified by the first weak learner. This process would continue until a desired level of accuracy is reached.
* In **image classification**, boosting can be used to classify images into different categories, such as cats, dogs, or cars. A weak learner might be trained to identify features that are common to a particular category of images, such as the shape of an object or the color of an object. The next weak learner would then be trained on the data that was misclassified by the first weak learner. This process would continue until a desired level of accuracy is reached.

Boosting is a powerful machine learning technique that can be used to improve the accuracy of a variety of AI tasks.

### 9.4.2 Bagging

Bagging, also known as bootstrap aggregating, is an ensemble learning meta-algorithm that combines a set of weak learners to create a more accurate and robust model. It works by training multiple copies of a base estimator on different subsets of the training data. Each subset is created by sampling the original training data with replacement, which means that some data points may be included in multiple subsets.

The predictions of the individual models are then averaged or combined in some other way to produce a final prediction. This averaging process helps to reduce the variance of the model, which can make it more robust to noise and outliers in the training data.

Bagging is a relatively simple and easy-to-implement ensemble learning method. It can be used with a variety of base estimators, including decision trees, random forests, and support vector machines. Bagging has been shown to be effective in a variety of machine learning tasks, including classification, regression, and clustering (see [Figure 9.8](#ch9.xhtml#fig9_8)).

![Figure 9.8 Bagging.](images/fig9_8_B.jpg)

[Figure 9.8 Bagging.](#ch9.xhtml#R_fig9_8)

Benefits of using bagging in machine learning:
* It can help to reduce the variance of a model, which can make it more robust with regard to noise and outliers in the training data.
* It can improve the accuracy of a model, especially when the base estimator is a weak learner.
* It can be used with a variety of base estimators, making it a versatile ensemble learning method.
* It is relatively simple and easy to implement.

Drawbacks of using bagging in machine learning:
* It can increase the training time, as multiple models need to be trained.
* It can increase the complexity of the model, which can make it more difficult to interpret.
* It can be less effective than other ensemble learning methods, such as boosting, in some cases.

Overall, bagging is a powerful ensemble learning method that can be used to improve the accuracy and robustness of machine learning models. It is a relatively simple and easy-to-implement method that can be used with a variety of base estimators. However, it is important to note that bagging can increase the training time and complexity of the model.

### 9.4.3 Voting

Voting is an ensemble learning method that combines the predictions of multiple machine learning models to make a final prediction. It is a simple and effective way to improve the accuracy of a model, especially when the individual models are diverse. There are two main types of voting—hard voting and soft voting. Hard voting simply takes the majority vote of the individual models. For example, if a model predicts class A, B, and C with equal probability and another model predicts class A and B with equal probability, then the final prediction will be class A. Soft voting takes into account the confidence of each model’s prediction. For example, if a model predicts class A with a probability of 0.6, and another model predicts class B with a probability of 0.4, then the final prediction will be class A. Voting can be used with a variety of machine learning models, including decision trees, support vector machines, and logistic regression. It is especially effective when the individual models are diverse, meaning that they use different algorithms and make different types of predictions.

Benefits of using voting in machine learning:
* It can improve the accuracy of a model, especially when the individual models are diverse.
* It can be more robust to noise and outliers in the training data.
* It can be more interpretable than other ensemble learning methods, such as boosting.
* It is relatively simple and easy to implement.

Drawbacks of using voting in machine learning:
* It can increase the training time, as multiple models need to be trained.
* It can increase the complexity of the model, which can make it more difficult to train and deploy.
* It can be less effective, in some cases, than other ensemble learning methods, such as boosting.

Overall, voting is a powerful ensemble learning method that can be used to improve the accuracy and robustness of machine learning models. It is a relatively simple and easy-to-implement method that can be used with a variety of machine learning models. However, it is important to note that voting can increase the training time and complexity of the model (see [Table 9.1](#ch9.xhtml#table9_1)).

[Table 9.1 Comparison of Boosting, Bagging, and Voting](#ch9.xhtml#R_table9_1)

| Boosting || Bagging || Voting |
| --- | --- | --- |
| Adopts a method of sequential ensemble learning. || Adopts a method of parallel ensemble learning. || Adopts a method for merging the outcomes of various models. Either a parallel or serial algorithm can be employed to train each individual model in the ensemble. |
| --- | --- | --- |
| Uses random sampling to generate training sets. || By sampling the initial training data with replacement, uses a process known as bootstrapping by which the subsets are produced. || Can be utilized with any combination of models, including both strong and weak learners. |
