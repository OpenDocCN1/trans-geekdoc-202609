
# Ensemble Learning Techniques

We can use mechanisms to alter the training data in each model in ensemble learning. As a simple technique, *k*-fold cross-validation can be used to measure the generalization error. Here, the training dataset is divided into *k* subsets and each subset is trained using a unique model. Bootstrap aggregation (bagging) is another technique, which trains the model with a resampled training dataset with a replacement, which results in different generalization errors. Random training subset ensemble is another technique.

## Changing models

The configuration of each model used for the ensemble can be varied. For instance, models differ based on the number of layers or nodes, learning rates or regularization types. Thus, the ensemble model learns a heterogeneous mapping function and results in a smaller correlation in the output.

## Changing combinations

The combination method of the outcomes from ensemble models can be varied. As a simple technique, model blending can be used that calculates the average of the predictions of each model. This weighted average ensemble can be improved by taking the optimized weights techniques, such as hold-out validation. Additionally, new models can be learned using techniques such as stacking. As an extended technique, boosting can be used. It incorporates one model at a time for the ensemble learning process to address the errors that occurred during the previous model training. Model weight averaging is another method that combines the weights of several models that has a similar structure.

## 5.4.3 Ensemble Learning Techniques

We have learnt that the objective of ensemble learning is to decrease the variance of the predicted results and the generalization error by merging the outputs of several learning models. As discussed above, different ensemble learning techniques are obtained by varying training data, and models, and combining the mechanism of the predictions. The selection of the ensemble techniques depends on the application. There are advanced ensemble learning techniques such as bagging, boosting, and stacking as described as follows.

### Bagging (bootstrap aggregation)

The bagging method selects individual data points more than once and performs a random sample of training data, to reduce the prediction variance within a noisy dataset. Here, a replacement technique is used to create random subsets of a dataset, which are used as independent datasets that are used to train models in parallel. Therefore, a given data point can belong to many subsets of data. The testing phase considers the output of the models that are trained using different subsets of a given dataset, as shown in [Figure 5.13](#ch12.xhtml#f83). The final result is obtained by passing the several model outputs through an aggregation process. Bagging shows higher bias, such that the predictors are less correlated and reduce the ensemble's variance.

![Figure 5.13 Process of bagging technique with parallel processing.](html/images/9781032473246_C005_013.jpg)

[Figure 5.13](#ch12.xhtml#f83b) Process of bagging technique with parallel processing.

### Boosting

Generally, each model would not perform well on the entire dataset; however, they do have high performances in parts of the dataset. Boosting processes the dataset sequentially, such that the entire dataset is input to the initial model and analyze the result. The data points that are incorrectly classified by the model are then passed to the second model. Thus, the second sub-model focuses on the challenging regions of feature space and learns an applicable decision boundary. As the name suggests, each model will contribute to boosting the performance of the overall ensemble. Subsequently, the same process is followed and the combination of all the previous models is used to generate the final result on unseen data as shown in [Figure 5.14](#ch12.xhtml#f84). Here, each model is dependent on the previous model as the successive models aim to rectify the errors of the prior model training for a given subset of data. Thus, the boosting algorithm ensembles a set of inadequate models to generate a robust learning model and boosts the entire prediction using the majority voting weight. This method reduces the bias in the ensemble prediction. Thus, the selected classifiers should be simple models with less trainable parameters that result in low variance and high bias.

![Figure 5.14 Process of boosting technique with sequence processing.](html/images/9781032473246_C005_014.jpg)

[Figure 5.14](#ch12.xhtml#f84b) Process of boosting technique with sequence processing.

### Stacking

The stacking technique uses bootstrapped data subsets and trains multiple models parallelly as in the bagging technique. The output of all these models is used to combine the multiple models through a meta-classifier that produces the overall prediction. Here, two layers of classifiers are used to ensure proper training. The meta-classifier in the next layer may capture the missing features from the set of models in the first layer. For instance, the output class assignment probabilities produced by the first layer of models can be averaged with some weights to combine the model outputs. Then the `argmax` over the average predicted class probabilities can be used for the final prediction. A stacking with one level is shown in [Figure 5.15](#ch12.xhtml#f85). Additionally, there are ensemble models with multi-level stacking, where extra classification layers are included among them. However, compared to the relatively low improvement of the performance results, such methods consume more computational costs.

![Figure 5.15 Process of stacking technique with meta-classifier.](html/images/9781032473246_C005_015.jpg)

[Figure 5.15](#ch12.xhtml#f85b) Process of stacking technique with meta-classifier.

### Mixture of experts

This technique uses several classifier models, and their outputs are ensembled using a generalized linear rule. A gating network, which is a trainable neural network, is used to decide the weight assignment for the combinations as shown in [Figure 5.16](#ch12.xhtml#f86). The mixture of experts' method is applied when there are various models trained on different classes of the feature space, supporting the information fusion problem.

![Figure 5.16 Process of the mixture of expert techniques with a generalized linear rule.](html/images/9781032473246_C005_016.jpg)

[Figure 5.16](#ch12.xhtml#f86b) Process of the mixture of expert techniques with a generalized linear rule.

The following are basic techniques in ensemble learning that operate on similar data.

*   **Max rule**: this technique is based on the probability distributions produced by each model. The prediction of the ensemble model is the class label that has the maximum confidence score of the output among the classifiers, so that it can be applied for multi-class classification as well.
*   **Majority voting**: this method considers a random set of classifier models and computes the predictions for each sample. The most predicted class label by many models is considered as the output of ensemble learning. Since the majority-voted class is selected, this technique works well for binary classification. In multi-class classification, if two or more classes have the same highest voting, then a random class is selected as the final prediction.
*   **Probability averaging**: this method first computes the probability scores, which is the confidence in prediction, for all the models separately. Then it calculates the average scores of all the involved models, considering all the class labels in a given dataset. Among the average scores, the class label with the maximum probability is considered as the predicted class of the ensemble model.
