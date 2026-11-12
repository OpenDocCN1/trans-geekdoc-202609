
Figure 2.3 demonstrates the visualization of the dataset in machine learning:

![](img/7e519fee1b702b91799cdf1664598392_99_0.png)

Figure 2.3: Dataset visualization in machine learning

The following are some of the most commonly used datasets in machine learning.

### ImageNet

ImageNet is a database that follows the WordNet hierarchy. WordNet is a vocabulary database of English words. It groups the words into synsets (a set of synonyms) and has a record of relations among these synonyms.

WordNet contains a set of about 100,000 phrases, and ImageNet has about 10,000 images for each phrase. Its size is about 150 GB and contains around 1,500,000 images with respective class labels. Figure 2.4 shows a sample of the ImageNet dataset:

![](img/7e519fee1b702b91799cdf1664598392_100_0.png)

Figure 2.4: ImageNet dataset
(https://gluon-cv.mxnet.io/build/examples_classification/demo_cifar10.html)

### Modified National Institute of Standards and Technology database (MNIST)

It is one of the popular datasets for machine learning algorithms. This dataset contains handwritten digits with a training set of about 60,000 examples and a testing set of about 10,000 examples. It can be used in almost every machine learning technique, and also it requires less effort and time in the pre-processing of data. Figure 2.5 shows a sample of the MNIST dataset:

![](img/7e519fee1b702b91799cdf1664598392_101_0.png)

Figure 2.5: MNIST dataset

Its size is about 50 MB and contains around 70,000 images in 10 classes.

## Machine learning libraries

Libraries are defined as sets of functions and routines that are written in a specific programming language. A vigorous set of libraries makes it easier for researchers and developers to execute complex programs without writing several lines of code.

Most of the deep learning libraries are based on the graph-based module, as all the concepts of deep learning algorithms are based on computational graphs. Python libraries that are used in implementing machine learning and deep learning algorithms are as follows:

- Numpy
- Theano
- Keras
- TensorFlow
- Pandas
- SciPy
- PyTorch
- Matplotlib
- NLTK

Let us discuss some of the most commonly used libraries in machine learning.

### Numpy

Numpy is a library consisting of general-purpose array-processing packages. It is written in Python programming language with aided support for large multi-dimension arrays and mathematical functions to support these arrays.

It supports tools for the integration of Fortran and C/C++. It has useful mathematical capabilities such as the Fourier transform and linear algebra. Numpy can be integrated with a wide range of databases as it can be used to define arbitrary data types.

At the core, Numpy provides excellent ndarray objects, short for n-dimensional arrays. ndarray is an array object which can be used to store multiple objects of the same data type.

Numpy consists of the following features:

- A large array objects
- Easy integration with Fortran and C/C++ language
- Broadcasting functions
- Useful Fourier transforms and linear algebra capabilities

### Arrays in Numpy

The main object of Numpy is the multi-dimensional array of homogeneous nature. The array is a table of elements, mostly numbers, of the same data type. In Numpy, dimensions are denoted as axes, and the total number of axes is known as rank. The array class of Numpy is known as an n-dimensional array. We will discuss how to create arrays in Numpy in the hands-on section.

### Array indexing

The basics of array indexing are very important to analyze and manipulate the array object. Following are the common ways to do the array indexing in Numpy:

- **Slicing**: Arrays in Numpy can be sliced similar to the slicing of the lists in Python. For slicing the array, define a slice for each dimension of the array.
- **Boolean array indexing**: It is commonly used when the user wants to pick elements from an array satisfying certain conditions.

### Theano

Theano is a library written in Python language that allows users to define and optimize the multi-dimensional array of mathematical expressions. It is one of the most commonly used deep learning libraries and works as a neural network building block.

Theano library helps the user to optimize the utilization of the central processing unit/graphical processing unit (CPU/GPU), resulting in the improved performance of data computation capacity.

### Keras

Keras is a neural network-based open-source library and is written in Python. It was designed by Google engineer Francois Chollet to enable the fast execution of programs with deep neural networks. It is a user-friendly, extensible, and modular library.

This library can be run on top of Theano and TensorFlow. It wraps around the functionalities of other libraries, such as Theano and TensorFlow.

Keras is a high-level application programming interface (API) and deals with defining layers, model creation, and setting-up multiple input/output (I/O) models. However, it does not deal with low-level API, such as the making of tensors, computational graphs, and so on.

### TensorFlow

TensorFlow is an open-source and free library for dataflow and programming for different types of tasks. This library was released in November 2015 by Google. It is the most commonly used library for deep learning applications like neural networks.

TensorFlow is a symbolic math library and is written in Python programming language, but now a JavaScript port tensorflow.js is available for the same.

### Pandas

Pandas is a popular Python library designed for data analytics. It is an open-source, free-to-use library designed by Wes McKinney. It is written in C and Python programming languages.

It provides expressive data structures that can be used while working with time series and structured data. It provides label-based slicing, subsetting, and fancy indexing of large datasets.

### SciPy

SciPy is the most common library used to implement machine learning algorithms. It consists of several modules for linear algebra, integration, and optimization. It is a **Berkeley Source Distribution** (BSD) licensed library for science, mathematics, and engineering.

The BSD license is a family of free software licenses which imposes negligible restrictions on the use and distribution of the covered software. This library depends on Numpy, as the main reason for building this library was to integrate it with Numpy arrays.

### PyTorch

PyTorch is an open-source library for machine learning which is based on the Torch library. It is most commonly used for applications such as natural language processing and computer vision.

It is written in Python and C++ programming languages. It has the following features:

- It provides deep neural networks built on an autodiff system.
- It supports tensor computing via GPUs.

### Matplotlib

Matplotlib is a plotting library designed for the Python programming language and Numpy. It was developed by *Michael Droettboom* in 2003.

It provides an object-oriented API to embed the plots into different applications using GPUs. There is a Pyplot module in Matplotlib that provides a MATLAB-like interface.

Table 2.1 shows a comparison among the most commonly used machine learning libraries:

| Name | Developer | Interface | Suitable model | Multi-GPU support | Distributed |
| :--- | :--- | :--- | :--- | :--- | :--- |
| NumPy | Travis Oliphant | Python, C | RNN*, CNN**, DNN*** | Yes | Yes |
| Theano | Universite de Montreal | Python | RNN, CNN, DNN | No | No |
| Keras | Francois Chollet | Python | RNN, CNN, DNN | No | No |
| TensorFlow | Google | Python, C++, JAVA | RNN, CNN, DNN | Yes | Yes |
| Pandas | Wes McKinney | Python, C | RNN, CNN, DNN | Yes | No |
| SciPy | Travis Oliphant | Python, C, C++, Fortran | RNN, CNN, DNN | Yes | Yes |
| PyTorch | Ronan Collobert | C++, R, Python, MATLAB, JavaScript | RNN, CNN, DNN | Yes | No |
| Matplotlib | John D. Hunter | Python | RNN, CNN, DNN | Yes | No |

Table 2.1: Comparison of machine learning libraries

*RNN → Recurrent Neural Network.
**CNN → Convolutional Neural Network.
***DNN → Deep Neural Network.

## Neural network

The neural network can be defined as a network of neurons or circuits of neurons designed to recognize patterns. A neural network can be of two types: a biological neural network, which consists of real biological neurons, and an artificial neural network, which is designed to solve AI problems.
