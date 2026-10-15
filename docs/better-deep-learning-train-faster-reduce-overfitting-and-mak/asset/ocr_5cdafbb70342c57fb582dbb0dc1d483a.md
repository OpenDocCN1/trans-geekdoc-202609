The analysis shows that increasing the capacity of the model via increasing depth is a very effective tool that must be used with caution as it can quickly result in a model with a large capacity that may not be capable of learning the training dataset easily.

# 2.4 Extensions

This section lists some ideas for extending the tutorial that you may wish to explore.

+   - **Too Many Nodes**. Update the experiment of increasing nodes to find the point where the learning algorithm is no longer capable of learning the problem.
+   - **Repeated Evaluation**. Update an experiment to use the repeated evaluation of each configuration to counter the stochastic nature of the learning algorithm.
+   - **Harder Problem**. Repeat the experiment of increasing layers on a problem that requires the increased capacity provided by increased depth in order to perform well.

If you explore any of these extensions, I’d love to know.

# 2.5 Further Reading

This section provides more resources on the topic if you are looking to go deeper.

# 2.5.1 Books

+   - *Neural Smithing: Supervised Learning in Feedforward Artificial Neural Networks*, 1999.
+     https://amzn.to/2vhyW8j
+   - *Deep Learning*, 2016.
+     https://amzn.to/2IXzUIY

# 2.5.2 APIs

+   - Keras Core Layers API.
+     https://keras.io/layers/core/
+   - Keras Convolutional Layers API.
+     https://keras.io/layers/convolutional/
+   - Keras Recurrent Layers API.
+     https://keras.io/layers/recurrent/
+   - Keras Utility Functions.
+     https://keras.io/utils/
+   - sklearn.datasets.make_blobs API.
+     http://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_blobs.html