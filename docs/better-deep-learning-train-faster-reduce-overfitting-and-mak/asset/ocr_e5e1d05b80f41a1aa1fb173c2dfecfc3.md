# Chapter 19

# Reduce Model Variance with Ensemble Learning

Deep learning neural networks are nonlinear methods. They offer increased flexibility and can scale in proportion to the amount of training data available. A downside of this flexibility is that they learn via a stochastic training algorithm which means that they are sensitive to the specifics of the training data and random initialization, which in turn produce different predictions. Generally, this is referred to as neural networks having a high variance and it can be frustrating when trying to develop a final model to use for making predictions.

A successful approach to reducing the variance of neural network models is to train multiple models instead of a single model and to combine the predictions from these models. This is called ensemble learning and not only reduces the variance of predictions but also can result in predictions that are better than any single model. In this tutorial, you will discover methods for deep learning neural networks to reduce variance and improve prediction performance. After reading this tutorial, you will know:

+   - Neural network models are nonlinear and have a high variance, which can be frustrating when preparing a final model for making predictions.
+   - Ensemble learning combines the predictions from multiple neural network models to reduce the variance of predictions and reduce generalization error.
+   - Techniques for ensemble learning can be grouped by the element that is varied, such as training data, the model, and how predictions are combined.

Let’s get started.



Training deep neural networks can be very computationally expensive. Very deep networks trained on millions of examples may take days, weeks, and sometimes months to train.

> Google’s baseline model [...] was a deep convolutional neural network [...] that had been trained for about six months using asynchronous stochastic gradient descent on a large number of cores.