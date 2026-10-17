# 14.3  Extensions

This section lists extensions to the tutorial that you may wish to explore.

+   - **Tune Parameters.** The parameters in the above example were not tuned; try different values to improve the classification accuracy.
+   - **Different Distance Measures.** Experiment with different distance measures such as Manhattan distance and Minkowski distance.
+   - **Multiple-Pass LVQ.** The codebook vectors may be updated by multiple training runs. Experiment by training with large learning rates followed by a large number of epochs with smaller learning rates to fine tune the codebooks.
+   - **Update More BMUs.** Experiment with selecting more than one BMU when training and pushing and pulling them away from the training data.
+   - **More Problems.** Apply LVQ to more classification problems on the UCI Machine Learning Repository.

# 14.4  Review

In this tutorial, you discovered how to implement the learning vector quantization algorithm from scratch in Python. Specifically, you learned:

+   - How to calculate the distance between patterns and locate the best matching unit.
+   - How to train a set of codebook vectors to best summarize the training dataset.
+   - How to apply the learning vector quantization algorithm to a real predictive modeling problem.

# 14.4.1  Further Reading

+   - Chapter 6. Learning Vector Quantization, page 245, *Self-Organizing Maps*, 2000
+     http://amzn.to/2f77mhU

# 14.4.2  Next

In the next tutorial, you will discover how to implement and apply the Backpropagation algorithm for classification.