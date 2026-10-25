
to unseen data. In many methods that involve coefficients, such as regression methods and artificial neural networks, simpler models are often characterized by models that have smaller coefficient values. A technique that is often used to encourage a model to minimize the size of coefficients while it is being fit on data is called regularization. Common implementations include the L^2 and L^1 forms of regularization. Both of these forms of regularization are in fact a measure of the magnitude or length of the coefficients as a vector and are methods lifted directly from linear algebra called the vector norm.

## 3.7 Principal Component Analysis

Often a dataset has many columns, perhaps tens, hundreds, thousands or more. Modeling data with many features is challenging, and models built from data that include irrelevant features are often less skillful than models trained from the most relevant data. It is hard to know which features of the data are relevant and which are not. Methods for automatically reducing the number of columns of a dataset are called dimensionality reduction, and perhaps the most popular method is called the principal component analysis or PCA for short. This method is used in machine learning to create projections of high-dimensional data for both visualization and for training models. The core of the PCA method is a matrix factorization method from linear algebra. The eigendecomposition can be used and more robust implementations may use the singular-value decomposition or SVD.

## 3.8 Singular-Value Decomposition

Another popular dimensionality reduction method is the singular-value decomposition method or SVD for short. As mentioned and as the name of the method suggests, it is a matrix factorization method from the field of linear algebra. It has wide use in linear algebra and can be used directly in applications such as feature selection, visualization, noise reduction and more. We will see two more cases below of using the SVD in machine learning.

## 3.9 Latent Semantic Analysis

In the sub-field of machine learning for working with text data called natural language processing, it is common to represent documents as large matrices of word occurrences. For example, the columns of the matrix may be the known words in the vocabulary and rows may be sentences, paragraphs, pages or documents of text with cells in the matrix marked as the count or frequency of the number of times the word occurred. This is a sparse matrix representation of the text. Matrix factorization methods such as the singular-value decomposition can be applied to this sparse matrix which has the effect of distilling the representation down to its most relevant essence. Documents processed in this way are much easier to compare, query and use as the basis for a supervised machine learning model. This form of data preparation is called Latent Semantic Analysis or LSA for short, and is also known by the name Latent Semantic Indexing or LSI.

## 3.10 Recommender Systems

Predictive modeling problems that involve the recommendation of products are called recommender systems, a sub-field of machine learning. Examples include the recommendation of books based on previous purchases and purchases by customers like you on Amazon, and the recommendation of movies and TV shows to watch based on your viewing history and viewing history of subscribers like you on Netflix. The development of recommender systems is primarily concerned with linear algebra methods. A simple example is in the calculation of the similarity between sparse customer behavior vectors using distance measures such as Euclidean distance or dot products. Matrix factorization methods like the singular-value decomposition are used widely in recommender systems to distill item and user data to their essence for querying and searching and comparison.

## 3.11 Deep Learning

Artificial neural networks are nonlinear machine learning algorithms that are inspired by elements of the information processing in the brain and have proven effective at a range of problems not least predictive modeling. Deep learning is the recent resurged use of artificial neural networks with newer methods and faster hardware that allow for the development and training of larger and deeper (more layers) networks on very large datasets. Deep learning methods routinely achieve state-of-the-art results on a range of challenging problems such as machine translation, photo captioning, speech recognition and much more.

At their core, the execution of neural networks involves linear algebra data structures multiplied and added together. Scaled up to multiple dimensions, deep learning methods work with vectors, matrices and even tensors of inputs and coefficients, where a tensor is a matrix with more than two dimensions. Linear algebra is central to the description of deep learning methods via matrix notation to the implementation of deep learning methods such as Google's TensorFlow Python library that has the word "tensor" in its name.

## 3.12 Summary

In this chapter, you discovered 10 common examples of machine learning that you may be familiar with that use and require linear algebra. Specifically, you learned:

- The use of linear algebra structures when working with data such as tabular datasets and images.
- Linear algebra concepts when working with data preparation such as one hot encoding and dimensionality reduction.
- The ingrained use of linear algebra notation and methods in sub-fields such as deep learning, natural language processing and recommender systems.

## 3.12.1 Next

This is the end of the first part, in the next part you will discover how to manipulate arrays of data in Python using NumPy.

## Part III

### NumPy

## Chapter 4

### Introduction to NumPy Arrays

Arrays are the main data structure used in machine learning. In Python, arrays from the NumPy library, called N-dimensional arrays or the `ndarray`, are used as the primary data structure for representing data. In this tutorial, you will discover the N-dimensional array in NumPy for representing numerical and manipulating data in Python. After completing this tutorial, you will know:

- What the `ndarray` is and how to create and inspect an array in Python.
- Key functions for creating new empty arrays and arrays with default values.
- How to combine existing arrays to create new arrays.

Let's get started.

### 4.1 Tutorial Overview

This tutorial is divided into 3 parts; they are:

- 1. NumPy N-dimensional Array
- 2. Functions to Create Arrays
- 3. Combining Arrays

### 4.2 NumPy N-dimensional Array

NumPy is a Python library that can be used for scientific and numerical applications and is the tool to use for linear algebra operations. The main data structure in NumPy is the `ndarray`, which is a shorthand name for N-dimensional array. When working with NumPy, data in an `ndarray` is simply referred to as an array. It is a fixed-sized array in memory that contains data of the same type, such as integers or floating point values.

The data type supported by an array can be accessed via the `dtype` attribute on the array. The dimensions of an array can be accessed via the `shape` attribute that returns a tuple describing the length of each dimension. There are a host of other attributes. A simple way to create an array from data or simple Python data structures like a list is to use the array() function. The example below creates a Python list of 3 floating point values, then creates an ndarray from the list and access the arrays’ shape and data type.

```
# create array
from numpy import array
# create array
l = [1.0, 2.0, 3.0]
a = array(l)
# display array
print(a)
# display array shape
print(a.shape)
# display array data type
print(a.dtype)
```

Listing 4.1: Example of creating an array with the array() function.

Running the example prints the contents of the ndarray, the shape, which is a one-dimensional array with 3 elements, and the data type, which is a 64-bit floating point.

```
[ 1. 2. 3.]
(3,)
float64
```

Listing 4.2: Sample output of creating an array with the array() function.

### 4.3 Functions to Create Arrays

There are more convenience functions for creating fixed-sized arrays that you may encounter or be required to use. Let’s look at just a few.

### 4.3.1 Empty

The empty() function will create a new array of the specified shape. The argument to the function is an array or tuple that specifies the length of each dimension of the array to create. The values or content of the created array will be random and will need to be assigned before use. The example below creates an empty 3 × 3 two-dimensional array.

```
# create empty array
from numpy import empty
a = empty([3,3])
print(a)
```

Listing 4.3: Example of creating an array with the empty() function.

Running the example prints the content of the empty array. Your specific array contents will vary.

```
[[ 0.0000000e+000 0.0000000e+000 2.20802703e-314]
 [ 2.20803350e-314 2.20803353e-314 2.20803356e-314]
 [ 2.20803359e-314 2.20803362e-314 2.20803366e-314]]
```

Listing 4.4: Sample output of creating an array with the empty() function.
