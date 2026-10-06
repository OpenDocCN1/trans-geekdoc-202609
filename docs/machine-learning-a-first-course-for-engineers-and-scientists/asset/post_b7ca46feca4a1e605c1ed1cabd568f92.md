
## 11 User aspects of machine learning

Dealing with supervised machine learning problems in practice is to a great extent an engineering discipline where many practical issues have to be considered and where the available amount of work-hours to undertake the development is often the limiting resource. To use this resource efficiently, we need to have a well-structured procedure for how to develop and improve the model. Multiple actions can potentially be taken. How do we know what action to take and is it worth spending the time implementing it? It is for example spending a week collecting and labeling training data or should we do something else? These issues will be addressed in this chapter. Note that the layout of this chapter is thematic and not necessarily represent the sequential order in which the different issues should be addressed.

## 11.1 Defining the machine learning problem

Solving a machine learning problem in practice is an iterative process. We train the model, and from there suggest an action for improvement and train the model again, and so on. To do this efficiently, we need to tell whether a new model is improvement over the previous one or not. One way to evaluate the model after each iteration would be to put it into production (for example running a traffic-sign classifier in a self-driving car for a few hours). Besides the obvious safety issues, this evaluation procedure would be very time consuming and cumbersome. We would most likely be inaccurate since it would be hard to tell whether the proposed change was an actual improvement or not.

A better strategy is to automate this evaluation procedure without the need to put the model into production each time we want to evaluate its performance. We do this by putting a validation dataset and a test dataset and evaluate the performance using a scalar evaluation metric. The validation and test datasets together with the evaluation metric will define the machine learning problem that we are solving.

### Training, validation and test data

In Chapter 4 we introduced the strategy of splitting the available data into training data, validation data and test data.

- **Training data** is used for training the model.
- **Hold-out validation data** is used for comparing different model structures, choosing hyperparameters of the model, feature selection, and so on.
- **Test data** is used to evaluate the performance of the final model.

All available data

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_234_0.png)

This material will be published by Cambridge University Press. This pre-publication version is free to view and download for personal use only. Not for re-distribution, re-sale or use in derivative works.
Andreas Lindholm, Nils Wahlström, Fredrik Lindquist, and Thomas B. Schön 2021.

## User aspects of machine learning

If the amount of available data is small, it is possible to perform k-fold cross-validation instead of putting aside hold-out validation data, the idea of how to use it in the iterative procedure is unchanged. To get a final estimate of performance, test data is used.

In the iterative procedure, the hold-out validation data (or k-fold cross-validation) is used to judge if the new model is an improvement over the previous model. During this stage, we can also choose to train several new models. For example, if we have a neural network model and are interested in the hidden units in a certain layer, we can train several models, with a different choice of hidden units. Afterwards, we pick the one that performs best on the validation data. The number of hidden units in a layer is one example of hyperparameter. If we have more hyperparameters we want to evaluate we can make a search over these parameters. In Section 5.6 we discuss hyper-parameter optimization in detail.

Eventually, we have effectively used the validation data to compare many models. Depending on the size of the validation data, we might risk picking a model that performs well on the validation data in comparison to unseen data. To detect and to get a fair estimate of the actual performance of a model, we use the test data, which has neither used during training nor. If the performance on the validation data is substantially better than the performance on the test data, we have overfitted on the validation data. The easiest solution in that case would be to extend the size of the validation data. The test data should not be reused as a part of the training and model selection procedure. If we start making decisions based on our test data, the model will be adapted to the test data and we can no longer trust that the test performance is an objective of the actual performance of our model.

It is important that both the validation data and the test data always come from the same distribution, namely the data distribution that we are expecting to see when we put the model into production. If we do not stem from the same distribution, we are validating and improving our models towards something that is not represented in the test data and "aiming for the wrong target". Usually, the training data is expected to come from the same distribution as the test and validation data, but this requirement can be relaxed if we have good reasons to do so. In Section 11.2 we will discuss this further.

When splitting the data into training, validation, and test, group leakage can be a potential problem. Group leakage can occur if the data points are not stochastically independent, but ordered into different groups. For example, in the medical domain many X-ray images belong to the same patient. In this case, if we do a random split over the images, different images belonging to the same patient will most end up in both the training and the validation set. The model learns the properties of a certain patient, then the performance on the validation data might be better than what we would expect in production.

Even though we acknowledge the use of validation and test data to improve and assess the performance of the model, we should also evaluate the performance of the model in production. If we realize that the model is systematically worse in production on the test data we should try to find the reason for why this is the case. If possible, the best way of improving the model is to update the test data and validation data that they actually represent what we expect to see in production.

### Size of validation and test data

How much data should we set aside as hold-out validation data and test data, or should we avoid setting aside hold-out validation data? This depends on how much data we have, which performance difference we plan to detect, and how many models we plan to compare. For example, if we have a classification model with a 99.8% accuracy and want to know if a new model is better, a validation dataset of 100 data points will not be able to tell that. Also, if we plan to compare many (say, hundreds or more) hyperparameter values and model structures using 100 validation data points, we will most likely overfit to that validation data.

If we have, 500 data points, one reasonable split could be 60%–20%–20% (that is 300–100–100 points) for training-validation-test. With such a small validation dataset, we cannot afford to compare several hyperparameter values and model structures or detecting an improvement of 0.1%. In this situation, we are better off using k-fold cross-validation to decrease the risk of overfitting the training data still even with k-fold cross-validation. We also need to test data if we want an unbiased estimate of the performance.

Many machine learning problems have substantially datasets. In this scenario, one possible split could be 98%–1%–1%, that is, leaving 10000 data points for validation and test, respectively, we really care about the last decimals in precision. Here, k-fold cross-validation is of less use in comparison to the scenario with just 500 data points, since having 99%–9%–1% (training+validation) for training would make a small difference in comparison to using only "98%”. The price for training k (instead of only one)

Another advantage of having a separate validation dataset is that we can allow the training data to come from slightly different distribution than the test, for example that would enable us to find a much larger dataset. We will discuss this in Section 11.2.

## Single number evaluation metric

In Section 4.5 we introduced additional metrics besides the misclassification rate such as precision, recall and F1-score for binary classifiers. There is no unique answer to which metric is the appropriate. What metric to pick is rather part of the problem definition. To improve the model quality and in a more automated fashion, it is advisable to choose on a single evaluation metric, especially if a team of engineers are working on the.

The single number evaluation metric together with the validation data are what we can evaluate the model on the hold-out validation data (or by k-fold cross-validation) using the metric, allows us to speed up the iterations we can quickly see if a proposed change to the model improves the performance or not. This is important in order to manage an efficient workflow of trying out and rejecting models.

That being, besides the single evaluation metric, it is useful to monitor other metrics as well to reveal the tradeoffs being made. For example, we might develop the model with different end users in mind who care about less different metrics, for practical reasons we might only use one model to accommodate them all. If we, based on these tradeoffs, realize that the single evaluation metric we have chosen does not favor the properties we want a good model to have, how we change that.

## Baseline and achievable performance level

Before working with the machine learning problem is a good idea to establish some reference points for the performance level of the model. A baseline is a very simple model that serves as a lower expected level of the performance. A baseline can be for example randomly pick any value y from the mean of all values output as the prediction. A baseline for the regression problem is to take the training data and use in the training data and as the prediction. A corresponding baseline for a classification problem is to pick the most common class label in the training data and use for that prediction. For example if we have a binary classification problem with 70% of the training data belonging to one class 30% belonging to the other and we have chosen as our performance metric, the accuracy for that baseline is 70%. The baseline is a lower threshold on the performance. We know that the baseline has to be better than this.
