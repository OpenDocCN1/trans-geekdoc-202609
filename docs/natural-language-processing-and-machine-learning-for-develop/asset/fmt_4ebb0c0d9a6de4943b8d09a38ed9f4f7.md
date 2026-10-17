
TF 2 tf.data.Datasets are well-suited for creating asynchronous and optimized data pipelines. In brief, the TF 2 Dataset API loads data from the disk (both images and text), applies optimized transformations, creates batches, and sends the batches to the GPU. In fact, the TF 2 Dataset API is well-suited for better GPU utilization. In addition, use tf.functions in TF 2.0 to fully utilize dataset asynchronous prefetching/streaming features.

According to the TF 2 documentation: “A Dataset can be used to represent an input pipeline as a collection of elements (nested structures of tensors) and a “logical plan” of transformations that act on those elements.”

A TF 2 tf.data.Dataset is designed to handle very large datasets. A TF 2 Dataset can also represent an input pipeline as a collection of elements (i.e., a nested structure of tensors), along with a “logical plan” of transformations that act on those elements. For example, you can define a TF 2 Dataset that initially contains the lines of text in a text file, then extract the lines of text that start with a “#” character, and then display only the first three matching lines. Creating this pipeline is easy: create a TF 2 Dataset and then chain the lazy operators filter() and take(), which is similar to an example that you will see later in this appendix.

### **Creating a Pipeline**

Think of a dataset as a pipeline that starts with a source, which can be a NumPy array, tensors in memory, or some other source. If the source involves tensors, use tf.data.Dataset.from_tensors() to combine the input, otherwise use tf.data.Dataset.from_tensor_slices() if you want a separate row for each input tensor. On the other hand, if the input data is located on disk in a TFRecord format (which is recommended), construct a tf.data.TFRecordDataset.

The difference between the first two APIs is shown below:

#combine the input into one element => [[1, 2], [3, 4]] t1 = tf.constant([[1, 2], [3, 4]]) ds1 = tf.data.Dataset.from_tensors(t1) #a separate element for each item: [1, 2], [3, 4] t2 = tf.constant([[1, 2], [3, 4]]) ds2 = tf.data.Dataset.from_tensor_slices(t2) for item in ds1: 
    print("1item:",item) 
    print("--------------") 
    for item in ds2: 
        print("2item:",item) 
The output from the preceding code block is here: 1item: tf.Tensor([[1 2] [3 4]], shape=(2, 2), dtype=int32) 
-------------- 
2item: tf.Tensor([1 2], shape=(2,), dtype=int32) 
2item: tf.Tensor([3 4], shape=(2,), dtype=int32) 

The TF 2 from_tensors() API also requires compatible dimensions, which means that the following code snippet causes an error:

# exception: ValueError: Dimensions 10 and 9 are not compatible ds1 = tf.data.Dataset.from_tensor_slices( 
    (tf.random_uniform([10, 4]), tf.random_uniform([9]))) 

However, the TF 2 from_tensor_slices() API does not have a compatibility restriction, so the following code snippet works correctly:

ds2 = tf.data.Dataset.from_tensors( 
    (tf.random_uniform([10, 4]), tf.random_uniform([9]))) 

Another situation in which there are differences in these two APIs involves the use of lists, as shown here:

ds1 = tf.data.Dataset.from_tensor_slices( 
    [tf.random_uniform([2, 3]), tf.random_uniform([2, 3])]) 
ds2 = tf.data.Dataset.from_tensors( 
    [tf.random_uniform([2, 3]), tf.random_uniform([2, 3])]) 
print(ds1) # shapes: (2, 3) 
print(ds2) # shapes: (2, 2, 3) 

In the preceding code block, the TF 2 from_tensors() API creates a 3D tensor whose shape is (2,2,3), whereas the TF 2 from_tensor_slices() API merges the input tensor and produces a tensor whose shape is (2,3).

As a further illustration of these two APIs, consider the following code block:

import tensorflow as tf 
ds1 = tf.data.Dataset.from_tensor_slices( 
    (tf.random.uniform([3, 2]), tf.random.uniform([3]))) 
ds2 = tf.data.Dataset.from_tensors( 
    (tf.random.uniform([3, 2]), tf.random.uniform([3]))) 
print('-----------------------------') 
for i, item in enumerate(ds1): 
    print('elem1: ' + str(i + 1), item[0], item[1]) 
print('-----------------------------') 
for i, item in enumerate(ds2): 
    print('elem2: ' + str(i + 1), item[0], item[1]) 
print('-----------------------------') 
Launch the preceding code and you will see the following output: 
----------------------------- 
elem1: 1 tf.Tensor([0.965013  0.8327141], shape=(2,), dtype=float32) tf.Tensor(0.03369963, shape=(), dtype=float32) elem1: 2 tf.Tensor([0.2875235  0.11409616], shape=(2,), dtype=float32) tf.Tensor(0.05131495, shape=(), dtype=float32) elem1: 3 tf.Tensor([0.08330548 0.13498652], shape=(2,), dtype=float32) tf.Tensor(0.3145547, shape=(), dtype=float32) 
----------------------------- 
elem2: 1 tf.Tensor([[0.9139079  0.13430142] [0.9585271  0.58751714] [0.4501326  0.8380357]], shape=(3, 2), dtype=float32) tf.Tensor([0.00776255 0.2655964  0.61935973], shape=(3,), dtype=float32) 
----------------------------- 
zzzzz 

Perform the following three steps in order to create and process the contents of a TF 2 Dataset:

1. Create or import data.

2. Define a generator (Python function).

3. Consume the data.

There are many ways to populate a TF 2 Dataset from multiple sources. For simplicity, the code samples in the first part of this appendix perform the following steps: start by creating a TF 2 Dataset instance with an initialized NumPy array of data; second, define a Python function in order to iterate through the TF 2 Dataset; and third, access the elements of the dataset (and in some cases, supply those elements to a TF 2 model).

TF 2 uses *generators* with Datasets. TF 2 uses generators because eager execution (the default execution mode for TF 2) does not support iterators.

### **A Simple TF 2** tf.data.Dataset

[Listing E.29](#appE.xhtml#listE.29) displays the contents of tf2_numpy_dataset.py that illustrates how to create a very basic TF 2 tf.data.Dataset from a NumPy array of numbers. Although this code sample is minimalistic, it’s the initial code block that appears in other code samples in this appendix.

***LISTING E.29: tf2_numpy_dataset.py***

import tensorflow as tf import numpy as np 
x = np.arange(0, 10) 
# make a dataset from a numpy array ds = tf.data.Dataset.from_tensor_slices(x) 

[Listing E.29](#appE.xhtml#listE.29) contains two familiar import statements and then initializes the variable x as a NumPy array with the integers from 0 through 9 inclusive. The variable ds is initialized as a TF 2 Dataset that’s based on the contents of the variable x.

Note that nothing else happens in [Listing E.29](#appE.xhtml#listE.29), and no output is generated. Later you will see more meaningful code samples involving TF 2 Datasets.
