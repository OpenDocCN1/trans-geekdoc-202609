Table 2.1 provides a summary of a list of tensor initializers implemented by native Python, NumPy, Tensorflow, and PyTorch. Most of these initializers are used in similar ways, where a `shape` and optionally, a `dtype` (discussed in the following section) arguments are needed to construct the tensor. There are four basic categories of tensor initializers:

+   1. **Static value initializers**: Where all the entries of the initialized tensors are filled with a single static value. They include “zeros,” “ones,” “empty,” and “full” initializers.
+   
+   2. **Random value initializers**: Where the entries of the initialized tensors are filled with random values drawn from some distribution, e.g. random uniform, random normal, or random int.
+   
+   3. **Range value initializers**: Where the entries of the initialized tensors are ordered and are within a predefined range of values. They include range and `linspace` initialization operations.
+   
+   4. **Special matrix initializers**: Where they initialize special matrices such as diagonal or identity matrices of various sizes.

# ## 2.2 Data Type and Casting

In many areas of scientific computing and machine learning applications, we need to manipulate the underlying data stored in the tensor. The value of the data may be represented and interpreted differently on the machine. I will not go into detail on how a computer represents information at the fundamental level. Interested readers can pick up an introductory computer science book or a C [Prinz and Crawford, 2005] or Java programming book to gain more understanding of computational data types. Although Python is not a strongly type-checked language like C or Java, a good understanding of fundamental data types within the libraries we use for our tasks (which often interface with numerical libraries written in C) would help us call methods and functions that efficiently implement dedicated algorithms specifically optimized for certain data types. Table 2.2 provides a list of data types implemented by Python, NumPy, Tensorflow, and PyTorch.