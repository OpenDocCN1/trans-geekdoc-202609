# 6 Neural networks and deep learning

# Dropout as bagging

As already pointed out, dropout has similarities with the ensemble method called bagging. If you have already learned about bagging in Chapter 7, there are a few important differences to point out:

+   - In bagging all models are independent in the sense that they have their own parameters.

+   - In bagging each model is trained until convergence. In most of the $U^2$ sub-networks are not trained at all (they have not been sampled), and those who have been trained have most likely only trained for one gradient step. however, since they share parameters all models will be updated when the other sub-networks are trained.

+   - Similar to bagging, in dropout we train each model on a dataset that has been randomly selected from our training data. However, in bagging we usually do on a bootstrapped version of the whole dataset where each model is trained on a randomly selected mini-batch of data.

Even though dropout differs from bagging in some aspects it has empirically shown to enjoy similar properties as bagging that in avoiding overfitting and reducing the variance of the model.

# Dropout as a regularization method

As a way to reduce the variance and overfitting, dropout can be seen as a regularization method. There are plenty of other regularization methods for neural networks including explicit regularization (like $L^1$ and $L^2$ regularization, see Chapter 5), early stopping (the training is stopped before the parameters have converged, see Chapter 5) and various sparse representations (for examples CNNs can be a regularization method where most parameters are forced to zero), just to mention few. Since its inception, dropout is one of the most popular regularization techniques due to its simplicity, it is computationally cheap, and its good performance. In fact, a good practice of designing a neural network is to extend the network until it overfits, then it a bit more and finally add a regularization like dropout to that overfitting.

> Example 6.4: Classification of hand-written digits - regularization with dropout

We return to the last model of Example 6.3 we used a CNN with an adaptive learning rate. In the results, we can see clear indications of overfitting. To reduce this overfitting we employ dropout during the training procedure. We use dropout in the final hidden layer and keep only $r=75\%$ of the 200 hidden units in that layer at iteration. In Figure 6.20 the result for this regularized model is presented. In red we show the performance on validation data for the non-regularized version which was already present in the chart of Example 6.3.

![](bbox=[0.13, 0.71, 0.85, 0.88])

In contrast to the last model of Example 6.3, the cost function evaluated for the validation data is (almost) no longer increasing and we reduce the misclassification rate by an additional 0.1% to 0.2%.

Draft (April 30, 2021) * A First Course for Engineers and Scientists. http://mlbook.org
Andreas Lindholm, Niklas Wahlström, Fredrik Lindstein, and Thomas B. Schön.