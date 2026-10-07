# 164 Mastering Classification Algorithms for Machine Learning

Now to make the subsets of data, we have two options. The first option is to create the subsets by sampling the original data set with replacement. When we create ensemble models using this this technique of creating subsets of data and using the same algorithm for creating the models, it is called Bagging ensemble models.

The second option is to create subsets by sampling the original data set without replacement. Ensemble models created by using such a technique for creating subsets of the original data set and using the same algorithm for creating the models are called Pasting ensemble models.

![](bbox=[0.179, 0.291, 0.821, 0.545])

Each of the subsets are created by randomly picking the data from the original data set. In Bagging/Pasting Ensemble Models, the same algorithm is used to create models using the data from one of the subsets

Figure 6.3: Illustration of how data sets are formed for Bagging/Pasting ensemble models

> Note: Let us understand sampling with replacement and sampling without replacement. Suppose we have a data set that contains the elements 1, 2, 3, 4, and 5. From this data set, let us say that we need to draw a sample with two elements. Suppose we pick 2 elements from this data set, and the elements are 1 and 4. Now, before we pick the next sample of 2 elements, if we put the elements 1 and 4 back in the data set and then sample, this would be called sampling with replacement. In other words, each time we sample from this data set, we would always make a selection from the original 5 elements in the data set. On the other hand, after we have picked our first sample containing 1 and 4, we do not put these elements back in the data set. Then, for the next sample, we have to select from elements 2, 3, and 5. This is called sampling without replacement.