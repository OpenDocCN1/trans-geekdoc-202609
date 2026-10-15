# Chapter 16

# Decouple Layers with Dropout

Deep learning neural networks are likely to quickly overfit a training dataset with few examples. Ensembles of neural networks with different model configurations are known to reduce overfitting, but require the additional computational expense of training and maintaining multiple models. A single model can be used to simulate having a large number of different network architectures by randomly dropping out nodes during training. This is called dropout and offers a very computationally cheap and remarkably effective regularization method to reduce overfitting and generalization error in deep neural networks of all kinds. In this tutorial, you will discover the use of dropout regularization for reducing overfitting and improving the generalization of deep neural networks. After reading this tutorial, you will know:

+   - Large weights in a neural network are a sign of a more complex network that has overfit the training data.
+   - Probabilistically dropping out nodes in the network is a simple and effective regularization method.
+   - A large network with more training epochs and the use of a weight constraint are suggested when using dropout.

Let’s get started.

# 16.1 Dropout

In this section you will discover that you can simulate the development of a large ensemble of neural network models in a single model called dropout, how you can use it to reduce overfitting, and tips for using this technique on your own projects.

# 16.1.1 Problem With Overfitting

Large neural nets trained on relatively small datasets can overfit the training data. This has the effect of the model learning the statistical noise in the training data, which results in poor performance when the model is evaluated on new data, e.g. a test dataset. Generalization error increases due to overfitting. One approach to reduce overfitting is to fit all possible different neural networks on the same dataset and to average the predictions from each model. This is