# 11 User aspects of machine learning

All available data

![](bbox=[0.118, 0.093, 0.878, 0.239])

Figure 11.4: Revising the training-validation-test data split by carving out a separate train-validation data from the training data.

# Extending the training data with slightly different data

As mentioned, there are situations where we can accept the training data from a slightly different distribution than the validation and test data. One reason to accept this is if we would have access to a substantially larger training dataset.

Consider a problem with 10000 data points representing the data that we would also expect to get when the model is deployed in production. We call this Dataset A. We have another dataset with 200000 data points that come from a slightly different distribution, but which is similar to what we think exploiting information from data can improve the model. We call this Dataset B. Some options to proceed with the following:

+   **Option 1** Use only Dataset A and split it into training, validation, and test data.

Dataset A

![](bbox=[0.412, 0.534, 0.627, 0.603])

The advantage of this option is that we only train, validate, and evaluate on Dataset A, which is also the type of data we want our model to perform well on. The disadvantage is that we have quite few data points and we do not exploit potentially useful information in the larger Dataset B.

+   **Option 2** Use both Dataset A and Dataset B. Randomly shuffle the data and split it in training, validation and test data.

Dataset A + B

![](bbox=[0.163, 0.743, 0.877, 0.812])

The advantage over option 1 is that we have more data available for training. However, the disadvantage is that we mainly evaluate the model on data from Dataset B, which we want our model to perform well on data from Dataset A.

+   **Option 3** Use both Dataset A and Dataset B. Use data points from Dataset A for validation and test data and some in the training data. Dataset B only goes into the training data.

Draft (April 30, 2021) of Machine Learning - A First Course for Engineers and Scientists. http://mlbook.org © Andreas Lindholm, Niklas Wahlström, Fredrik Lindson, and Thomas B. Schön. 2021.