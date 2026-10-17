If your data is not normally distributed, consider normalizing it prior to applying your machine learning algorithm. It is good practice to record the minimum and maximum values for each column used in the normalization process, again, in case you need to normalize new data in the future to be used with your model.

# ## 2.3 Extensions

There are many other data transforms you could apply. The idea of data transforms is to best expose the structure of your problem in your data to the learning algorithm. It may not be clear what transforms are required upfront. A combination of trial and error and exploratory data analysis (plots and stats) can help tease out what may work. Below are some additional transforms you may want to consider researching and implementing:

+   - Normalization that permits a configurable range, such as -1 to 1 and more.
+   - Standardization that permits a configurable spread, such as 1, 2 or more standard deviations from the mean.
+   - Exponential transforms such as logarithm, square root and exponents.
+   - Power transforms such as Box-Cox for fixing the skew in normally distributed data.

# ## 2.4 Review

In this tutorial, you discovered how to rescale your data for machine learning from scratch. Specifically, you learned:

+   - How to normalize data from scratch.
+   - How to standardize data from scratch.
+   - When to use normalization or standardization on your data.

# ## 2.4.1 Further Reading

+   - Chapter 3 Data Pre-processing, page 27, Applied Predictive Modeling, 2013 http://amzn.to/2e31NXF

# ## 2.4.2 Next

In the next tutorial, you will discover how to estimate the skill of a predictive modeling algorithm on unseen data.