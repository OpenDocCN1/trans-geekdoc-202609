
\-rw-r--r--  1 owner  staff     1222 Aug 17 14:34 cp.ckpt.index \-rw-r--r--  1 owner  staff  4886716 Aug 17 14:34 cp.ckpt.data-00000-of-00001 \-rw-r--r--  1 owner  staff       71 Aug 17 14:34 checkpoint 

## **Summary**

This appendix introduced you to some of the features of Keras and an assortment of Keras‑based code samples involving basic neural networks with the MNIST and cifar10 datasets. You learned about some of the important namespaces (such as `tf.keras.layers`) and their contents.

Next, you saw an example of performing linear regression with Keras and a simple CSV file. Then you learned how to create a Keras‑based MLP neural network that is trained on the MNIST dataset.

In addition, you saw examples of Keras‑based models that perform “early stopping,” which is convenient when the model exhibits minimal improvement (that is specified by you) during the training process.

# A P P E N D I X E

# INTRODUCTION TO TENSORFLOW 2

Welcome to TensorFlow 2! This appendix introduces you to various features of TensorFlow 2 (abbreviated as TF 2), as well as some of the TF 2 tools and projects that are covered under the TF 2 “umbrella.” You will see TF 2 code samples that illustrate new TF 2 features (such as `tf.GradientTape` and the `@tf.function` decorator), plus an assortment of code samples that illustrate how to write code “the TF 2 way.” Despite the simplicity of many topics in this appendix, they provide you with a foundation for TF 2.

Keep in mind that the TensorFlow 1.x releases are considered legacy code after the production release of TF 2. Google will provide only security‑related updates for TF 1.x (i.e., no new code development), and support TensorFlow 1.x for at least another year beyond the initial production release of TF 2. For your convenience, TensorFlow provides a conversion script to facilitate the automatic conversion of TensorFlow 1.x code to TF 2 code in many cases (details provided later in this appendix).

As you saw in the Preface, this appendix contains several sections regarding TF 1.x, all of which are placed near the end of this appendix. If you do not have TF 1.x code, obviously these sections are optional (and they are labeled as such).

The first part of this appendix briefly discusses some TF 2 features and some of the tools that are included under the TF 2 “umbrella.” The second section of this appendix shows you how to write TF 2 code involving TF constants and TF variables.

The third section digresses a bit: you will learn about the new TF 2 Python function decorator `@tf.function` that is used in many code samples in this appendix. Although this decorator is not always required, it’s important to become comfortable with this feature, and there are some nonintuitive caveats regarding its use that are discussed in this section.

The fourth section of this appendix shows you how to perform typical arithmetic operations in TF 2, how to use some of the built‑in TF 2 functions, and how to calculate trigonometric values. If you need to perform scientific calculations, see the code samples that pertain to the type of precision that you can achieve with floating point numbers in TF 2. This section also shows you how to use for loops and how to calculate exponential values.

The fifth section contains TF 2 code samples involving arrays, such as creating an identity matrix, a constant matrix, a random uniform matrix, and a truncated normal matrix, along with an explanation about the difference between a truncated matrix and a random matrix. This section also shows you how to multiply second‑order tensors in TF 2 and how to convert Python arrays to second‑order tensors in TF 2. The sixth section contains code samples that illustrate how to use some of the new features of TF 2, such as `tf.GradientTape`. Although the TF 2 code samples in this book use Python 3.x, it’s possible to modify the code samples in order to run under Python 2.7.

## **NOTE**

*As this book goes to print,* Python *3.7 works with the TF 2 code in this book, whereas Python 3.9.x does not work with TF 2*.

With all the preceding points in mind, the next section discusses a few details of TF 2, its architecture, and some of its features.

## **What is TF 2?**

TF 2 is an open source framework from Google and the newest version of TensorFlow. The TF 2 framework is a modern framework that’s well‑suited for machine learning and deep learning, and it’s available through an Apache license. Interestingly, TensorFlow surprised many people, perhaps even members of the TF team, in terms of the creativity and plethora of use cases for TF in areas such as art, music, and medicine. For a variety of reasons, the TensorFlow team created TF 2 with the goal of consolidating the TF APIs, eliminating duplication of APIs, enabling rapid prototyping, and making debugging an easier experience.

There is good news if you are a fan of Keras: improvements in TF 2 are partially due to the adoption of Keras as part of the core functionality of TF 2. In fact, TF 2 extends and optimizes Keras so that it can take advantage of all the advanced features in TF 2.

If you work primarily with deep learning models (CNNs, RNNs, LSTMs, and so forth), you’ll probably use some of the classes in the `tf.keras` namespace, which is the implementation of Keras in TF 2. Moreover, `tf.keras.layers` provides several standard layers for neural networks. As you’ll see later, there are several ways to define Keras‑based models, via the `tf.keras.Sequential` class, a functional style definition, and via a subclassing technique. Alternatively, you can still use lower‑level operations and automatic differentiation if you wish to do so.

Furthermore, TF 2 removes duplicate functionality, provides a more intuitive syntax across APIs, and also compatibility throughout the TF 2 ecosystem. TF 2 even provides a backward compatibility module called `tf.compat.v1` (which does not include `tf.contrib`), and a conversion script `tf_upgrade_v2` to help users migrate from TF 1.x to TF 2.

Another significant change in TF 2 is eager execution as the default mode (not deferred execution), with new features such as the `@tf.function` decorator and TF 2 privacy‑related features. Here is a condensed list of some TF 2 features and related technologies:

*   support for `tf.keras`: a specification for high‑level code for ML and DL

*   tensorflow.js v1.0: TF in modern browsers

*   TensorFlow Federated: an open source framework for ML and decentralized data

*   ragged Tensors: nested variable‑length (“uneven”) lists

*   TensorFlow Probability: probabilistic models combined with deep learning

*   Tensor2Tensor: a library of DL models and datasets

TF 2 also supports a variety of programming languages and hardware platforms, including:

*   support for Python, Java, C++

*   desktop, server, mobile device (TF Lite)

*   CPU/GPU/TPU support

*   Linux and Mac OS X support

*   VM for Windows

Navigate to the TF 2 home page, where you will find links to many resources for TF 2: *[https://www.tensorflow.org](https://www.tensorflow.org)*

### **TF 2 Use Cases**

TF 2 is designed to solve tasks that arise in a plethora of use cases, some of which are listed here:

*   image recognition

*   computer vision

*   voice/sound recognition

*   time series analysis

*   language detection

*   language translation

*   text‑based processing

*   handwriting recognition

The preceding list of use cases can be solved in TF 1.x as well as TF 2, and in the latter case, the code tends to be simpler and cleaner compared to their TF 1.x counterpart.

### **TF 2 Architecture: The Short Version**

TF 2 is written in C++ and supports operations involving primitive values and tensors (discussed later). The default execution mode for TF 1.x is *deferred execution* whereas TF 2 uses *eager execution* (think “immediate mode”). Although TF 1.4 introduced eager execution, the vast majority of TF 1.x code samples that you will find online use deferred execution.
