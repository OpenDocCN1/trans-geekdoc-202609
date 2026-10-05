# Data Mining with Skewed Data 69

important for the model outcome to indicate the probability6 of the event rather than providing a simple yes/no response. By having the outcome as a probability, models can be compared for use, cutoffs that keep the selecting rate equal to the capacity rate. In fraud detection, comparing models detection rate and hit rate fixing for example 1000 transaction to be investigated.

# PARAMETRIC OPTIMISATION

Once we have the data and the optimisation criteria, the following questions have to be answered:

+   Which classification method is recommended for producing the best model for any given application?

+   Which parameter set should be used?

For instance, we can apply any classification methods such as: Neural Networks (NN), Bayesian Networks (BN), Naïve Bayes (NB), Artificial Immune Systems (AIS) and Decision Trees (DT), Support Vector Machines (SVM), Logistic Regression and others. In fact, there is no final and unique answer to this first question. Support Vector Machines, for instance, is known to be effective with a very large number of characteristics and is reported to perform well in categorisation problems in Information Retrieval. However, our experience with SVM on fraud data did not meet our expectations. For many parameter sets, the method did not even converge to a final model and this behaviour for unbalanced data is reported to not uncommon.

In order to assess methods many factors can be used including the chosen optimisation criteria, scalability, time for classification and time spent in training, and sometimes more abstract criteria as to understand how the method works. Most of the time, when a method is published, or when an implementation is done, the method depends on parameter choices that may influence the final results significantly. Default parameters, in general, are a good start. However, most of the time, they are far from producing the best model. This comprises with our experience with many methods in many areas of Computer Science. This is particular for classification problems with skewed data.

Quite often we see comparisons against known methods where the comparison is done by applying a special parameter variation strategy (sometimes a parameter optimisation) for the chosen method while not