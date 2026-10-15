# Chapter 15

# Force Small Weights with Weight Constraints

Weight regularization methods like weight decay introduce a penalty to the loss function when training a neural network to encourage the network to use small weights. Smaller weights in a neural network can result in a model that is more stable and less likely to overfit the training dataset, in turn having better performance when making a prediction on new data. Unlike weight regularization, a weight constraint is a trigger that checks the size or magnitude of the weights and scales them so that they are all below a pre-defined threshold. The constraint forces weights to be small and can be used instead of weight decay and in conjunction with more aggressive network configurations, such as very large learning rates. In this tutorial, you will discover the use of weight constraint regularization as an alternative to weight penalties to reduce overfitting in deep neural networks.

After reading this tutorial, you will know:

+   - Weight penalties encourage but do not require neural networks to have small weights.
+   - Weight constraints, such as the L2 norm and maximum norm, can be used to force neural networks to have small weights during training.
+   - Weight constraints can improve generalization when used in conjunction with other regularization methods like dropout.

Let’s get started.

# 15.1  Weight Constraints

In this section you will discover the problem with neural networks that have large weighs, a technique that you can use to force the development of models with small weights called weight constraints and tips for using this technique in your own projects.

# 15.1.1  Alternative to Penalties for Large Weights

Large weights in a neural network are a sign of overfitting. A network with large weights has very likely learned the statistical noise in the training data. This results in a model that is