
any other software (such as Github repositories) that you also installed in any previous session.

## OTHER CLOUD PLATFORMS

GCP (Google Cloud Platform) is a cloud-based service that enables you to train TensorFlow code in the code. GCP provides Deep Learning DL images (similar in concept to Amazon AMIs) that are available here:

https://cloud.google.com/deep-learning-vm/docs

The preceding line provides documentation, and also a link to DL images based on different technologies, including TensorFlow and PyTorch, with GPU and CPU versions of those images. Along with support for multiple versions of Python, you can work in a browser session or from the command line.

## GCP SDK

Install GCloud SDK on a Mac-based laptop by downloading the software at this:

https://cloud.google.com/sdk/docs/quickstart-macos

You will also receive $300 USD worth of credit (over one year) if you have never used Google cloud.

## SUMMARY

This chapter introduced you to TensorFlow, its architecture, and all of the tools that are part of the TensorFlow “family.” Then you learned how to create a TensorFlow graph containing TensorFlow constants, placeholders, and variables. You also learned how to perform TensorFlow arithmetic operations, along with some built-in functions.

Next, you learned how to calculate trigonometric values, how to use for loops, while loops, and how to calculate exponential values. You also saw how to perform various operations on arrays, such as creating an identity matrix and a constant matrix.

Finally, you learned how to save a TensorFlow graph and then view its contents in a browser using the built-in TensorBoard utility that is launched from the command line.

## TENSORFLOW DATASETS

This chapter contains various code samples that illustrate how to use TensorFlow Datasets, which support a rich set of operators that can simplify your TensorFlow code and enable you to process large datasets (i.e., datasets that are too large to fit in memory). You will learn about operators (such as filter() and map()) that you can specify via "method chaining" as part of the definition of a TF dataset. In addition, you'll learn about TF estimators (in the tf.estimator namespace), TF layers (in the tf.layers namespace), and TFRecords.

Familiarity with lambda expressions (discussed later) and Reactive Programming will be very helpful for this chapter. In fact, this chapter will be very straightforward if you already have experience with Observables in RxJS, RxAndroid, RxJava, or some other environment that involves lazy execution.

The first part of this chapter briefly introduces you to TF Datasets and lambda expressions, along with some simple code samples. This section also introduces you to several types of iterators in TensorFlow, including "one-shot" and "reiterable" iterators.

The second part of this chapter discusses TextLineDatasets that are very convenient for working with text files. The code samples in this section also use two of the four types of iterators that are discussed in the previous section.

The third part of this chapter discusses so-called "intermediate" or "lazy" operators, such as filter(), flatmap(), and map() operators. You can use method chaining in order to combine these operators, resulting in powerful code combinations that can significantly reduce the complexity of your TensorFlow code.

The final portion of the chapter briefly discusses TF estimators, which are implementations of various Machine Learning algorithms, as well as TF layers that provide an assortment of classes for DNNs (Dense Neural Networks) and CNNs (Convolutional Neural Networks).

## TENSORFLOW DATASETS

TensorFlow Datasets (accessible via the namespace tf.data.Dataset) are well suited for creating asynchronous and optimized data pipelines. In brief, the TF Dataset API loads data from the disk (both images and text), applies optimized transformations, creates batches, and sends the batches to the GPU. Hence, the TF Dataset API is good for better GPU utilization. In addition, use tf.functions in TF 2.0 to fully utilize dataset asynchronous prefetching/streaming features.

A TF Dataset acts as a container-like “wrapper” around a dataset, somewhat analogous to a Pandas DataFrame. A very large dataset can also represent an input pipeline as a collection of elements (i.e., a nested structure of tensors), along with a “logical plan” of transformations that act on those elements. For example, you can define a TF Dataset that initially contains the lines of text in a text file, then extract the lines of text that start with a “#” character, and then display only the first three lines. Creating this pipeline is easy: create a TF Dataset and then chain the lazy operators filter() and take(), which is similar to an example you will see later in this chapter.

## Basic Steps for TensorFlow Datasets

Perform the following three steps to create and process the contents of a TF Dataset:

- 1. Import Data
- 2. Create an Iterator
- 3. Consume the Data

There are many ways to populate a TF Dataset with data that can be retrieved from multiple sources. For simplicity, the code samples in the first part of this chapter perform the following steps: first create a TF Dataset instance with an initialized NumPy array of data; second, define an iterator instance in order to iterate through the TF Dataset; and third, use the iterator to access the elements of the dataset (and in some cases, supply those elements to a TF model).

## A Simple TensorFlow Dataset

Listing 6.1 displays the contents of tf-numpy-dataset.py that illustrates how to create a TF Dataset from a NumPy array of numbers. Although this code sample is minimalistic, it is the starting point in other code samples in this chapter.

> LISTING 6.1: tf-numpy-dataset.py

```
import tensorflow as tf
import numpy as np

x = np.arange(0, 10)

# make a dataset from a numpy array
dataset = tf.data.Dataset.from_tensor_slices(x)
```

Listing 6.1 contains two import statements and then initializes the variable x as the integers from 0 through 9 inclusive. The variable dataset is initialized as a TF Dataset is based on the contents of the variable x.

Note that nothing else happens in Listing 6.1; later you will see more meaningful code samples involving TF Datasets.

## TENSORFLOW RAGGED CONSTANTS AND TENSORS
(OPTIONAL)

The section is marked “optional” because the code samples require TF 2. If you launch the code samples using TF 1.x, you will see the following error message:

AttributeError: 'module' object has no attribute 'RaggedTensor'

As you probably know, every element in a multidimensional array has the same dimensions. For example, a 2x3 array contains two rows and three columns: each row is a 1x3 vector. As another example, a 2x34 array contains two 3x4 arrays (and the same logic applies each 3x4 array).

On the other hand, a ragged constant is a set of elements that have different lengths. You can think of ragged constants as a generalization of “regular” datasets.

Listing 6.2 displays the contents of tf-raggedtensors.py that illustrates how to define a ragged dataset and then iterate through its contents.

# LISTING 6.2: tf-raggedtensors.py

```
import tensorflow as tf
digits = tf.ragged.constant([[3, 1, 4, 1], []], [5, 9, 2], [6], []])
words = tf.ragged.constant(["Bye", "now"], ["thank", "you", "again", "sir"]])

print(tf.add(digits, 3))
print(tf.reduce_mean(digits, axis=1))
print(tf.concat([digits, [[5, 3]]], axis=0))
print(tf.tile(digits, [1, 2]))
print(tf.strings.substr(words, 0, 2))
```

Listing 6.2 defines two ragged constants digits and words consisting of integers and strings, respectively. The remaining portion of Listing 6.2 consists of five print() statements that apply various operations to these two datasets and display the results.

The first print() statement adds the value 3 to every number in the digits dataset, and the second print() computes the row-wise average of the elements of the digits dataset because axis=0 performs column-wise operations.

The third print() statement appends the element [5, 3] to the digits dataset, and performs this operation in a column-wise fashion (because axis=0). each non-empty element of the digits dataset. Finally, the fifth print() statement extracts the first two characters from every string in the words dataset.

The output from launching the code in Listing 6.2 is here:

```
<tf.RaggedTensor [[6, 4, 7, 4], []], [8, 12, 5],
[9], []]>
tf.Tensor([[2.25 nan], [5.33333333]], (5,)], dtype=float64)
<tf.RaggedTensor [[3, 1, 4, 1], []], [5, 9, 2], [6],
[], [5, 3]]>
<tf.RaggedTensor [[3, 1, 4, 1, 3, 1, 4, 1], []], [5, 9, 2, 5, 9], [6, 6], []]>
<tf.RaggedTensor [[b'8y', b'no'], [b'th', b'yo',
b'ag', b'si']]]
```

Listing 6.3 displays the contents of tf-ragged-tensors.py that illustrates how to define a ragged tensor in TensorFlow.
