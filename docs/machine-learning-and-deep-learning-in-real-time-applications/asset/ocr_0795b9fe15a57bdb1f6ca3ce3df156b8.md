# BASICS OF CODING IN TENSORFLOW

The main object of the TensorFlow program is the tf.Tensor that manipulate and pass around. A tf.Tensor has the following characteristics:

+   - A data type (for example int32, float32, or string)
- A shape

The data type of each element in the tensor should be the same and is always known. The shape (i.e., the number of dimensions and the size of each dimension) might be partially known. Some special kinds of tensors are as follows that will be discussed in the next section of this chapter:

+   - tf.Variable
- tf.constant
- tf.placeholder

TensorFlow core program consists of two distinct sections

+   - Building the computational graph
- Running the computational graph

**Building the computational graph (using tf.Graph):** TensorFlow uses a dataflow graph or computational graph to denote the computation in terms of association between individual operations. In this step, tf.Operation (node) and tf.Tensor (edge) objects are constructed using TensorFlow API functions and add them to tf.Graph instance.

For example: tf.constant(32.0) creates a tf.Operation that produces the value 32.0 and added to the default graph, and returns a tf.Tensor that represents the value of the defined constant.

Let's understand with the help of python code. Here, a and b are two floating-point constants:

Figure 7. Python code to add two TensorFlow constants

```
import tensorflow as tf
a = tf.constant(3.0, dtype=tf.float32)
b = tf.constant(4.0) # also tf.float32 implicitly
total = a + b
print(a)
print(b)
print(total)
```