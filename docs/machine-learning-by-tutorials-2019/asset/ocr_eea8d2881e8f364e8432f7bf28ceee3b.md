Usually coremltools is the go-package for converting models to Core ML. You used to convert your Keras model in the previous chapter. The bad news is that coremltools does not directly support TensorFlow graphs.

The good news is that Apple and Google have collaborated to bring us tfcoreml, a TensorFlow to convert Core ML. This is an additional Python package that you need to install alongside coremltools.

TensorFlow works at a lower level of abstraction than Core ML and Keras. With TensorFlow, you build computational graphs that consist of primitive operations such as addition, multiplication, matrix math, array annotations and so on.

Core ML and Keras, on the other hand, know only about neural network layers. Why it's easy to convert from Keras to Core ML. But it's not always possible to convert TensorFlow graphs to Core ML. You can only convert graphs that Core ML supports. The tf-coreml website, github.com/tf-coreml/tf-coreml, lists the supported operations.

> Note: Core ML 5 is more capable in this than its predecessors. Like TensorFlow, it supports many low-level operations in addition to the neural network layers. Thanks to this, it should now be possible to convert more complex TensorFlow models to Core ML.

We recommend that this section you use the kerasenv environment, since already has coremltools and TensorFlow installed. If you don't already have installed, you can find kerasenv.yaml in the starter folder. Use conda create -n kerasenv.yaml to create the environment, and activate it.

But this environment does not have tfcoreml, so use pip to install the latest version:

```
$ pip install -U tfcoreml
```

You may also need to install the most recent version of coremltools. If using the one from pip gives errors, here's a handy trick for installing the latest version straight from GitHub:

```
$ pip install -U git+https://github.com/apple/coremltools.git
```