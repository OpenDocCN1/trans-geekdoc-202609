# # Chapter 6

# # NumPy Array Broadcasting

Arrays with different sizes cannot be added, subtracted, or generally be used in arithmetic. A way to overcome this is to duplicate the smaller array so that it has the dimensionality and size as the larger array. This is called array broadcasting and is available in NumPy when performing array arithmetic, which can greatly reduce and simplify your code. In this tutorial, you will discover the concept of array broadcasting and how to implement it in NumPy. After completing this tutorial, you will know:

+   - The problem of arithmetic with arrays with different sizes.
+   - The solution of broadcasting and common examples in one and two dimensions.
+   - The rule of array broadcasting and when broadcasting fails.

Let's get started.

# ## 6.1 Tutorial Overview

This tutorial is divided into 4 parts; they are:

+   1. Limitation with Array Arithmetic
+   2. Array Broadcasting
+   3. Broadcasting in NumPy
+   4. Limitations of Broadcasting

# ## 6.2 Limitation with Array Arithmetic

You can perform arithmetic directly on NumPy arrays, such as addition and subtraction. For example, two arrays can be added together to create a new array where the values at each index are added together. For example, an array a can be defined as [1, 2, 3] and array b can be defined as [1, 2, 3] and adding together will result in a new array with the values [2, 4, 6].