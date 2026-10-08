# # Core components of TensorFlow

The TensorFlow library provides a rich set of features for different machine learning steps, from data preparation to model serving. The following diagram shows the core building blocks of the TensorFlow library:

![](bbox=[0.1406, 0.1935, 0.8574, 0.3535])

Figure 5.5 – TensorFlow components

Training a machine model using TensorFlow 2.x involves the following main steps:

+   * **Preparing the dataset:** TensorFlow 2.x provides a `tf.data` for efficiently loading data from sources (such as files), transforming data (such as changing the values of the dataset), and setting up the dataset for training (such as configuring batch size or data prefetching). These data classes provide efficient ways to pass data to the training algorithms for optimized model training.The TensorFlow Keras** API also provides a list of built-in classes (MNIST, CIFAR, IMDB, MNIST Fashion, and Reuters News wires) for building simple deep learning models. You can also use a NumPy array or Python generator (a function that behaves like an iterator) to a model in **TensorFlow** for model training, but `tf.data` is the recommended approach.

+   *Defining the neural network:** TensorFlow 2.x provides multiple ways to use or build a neural network for model training. You can use the premade estimators (`tf.estimator` class) as DNNRegressor and DNNClassifier to train models. Or create custom neural networks using the keras class, which provides a list of primitives as `tf.keras.layers` for constructing neural network layers and `tf.keras.activation` as ReLU, **Sigmoid**, and **Softmax** for building neural networks. Softmax is usually used as the last output of a neural network for a multiclass problem. It takes a vector of real numbers (positive and negative) as input and normalizes the vector as a probability distribution to represent the probabilities of different class labels, such as the different types of hand-written digits. For binary classification problems, Sigmoid is normally used and it returns a value between 0 and 1.