# Chapter 4

# Evaluation Metrics

After you make predictions, you need to know if they are any good. There are standard measures that we can use to summarize how good a set of predictions actually is. Knowing how good a set of predictions is allows you to make estimates about the skill of a given machine learning model of your problem. In this tutorial, you will discover how to implement four standard prediction evaluation metrics from scratch in Python.

After reading this tutorial, you will know:

+   - How to implement classification accuracy.
+   - How to implement and interpret a confusion matrix.
+   - How to implement mean absolute error for regression.
+   - How to implement root mean squared error for regression.

Let’s get started.

# 4.1  Description

You must estimate the quality of a set of predictions when training a machine learning model. Performance metrics like classification accuracy and root mean squared error can give you a clear objective idea of how good a set of predictions is, and in turn how good the model is that generated them. This is important as it allows you to tell the difference and select among:

+   - Different transforms of the data used to train the same machine learning model.
+   - Different machine learning models trained on the same data.
+   - Different configurations for a machine learning model trained on the same data.

As such, performance metrics are a required building block in implementing machine learning algorithms from scratch.