Notice that NumPy uses 64-bit precision by default, while TensorFlow uses 32-bit. This is because 32-bit precision is generally more enough for neural networks, plus it runs faster and uses less RAM. So when you create a tensor from a NumPy array, make sure to set dtype=tf.float32.

# Type Conversions

Type conversions can significantly hurt performance, and they can easily go unintended when they are done automatically. To avoid this, TensorFlow does not perform any type conversions automatically: it raises an exception if you try to execute an operation on tensors in incompatible types. For example, you cannot add a float tensor and an integer tensor, and you cannot even add a 32-bit float and a 64-bit float:

```
>>> tf.constant(2.0) + tf.constant(40)
Traceback[...InvalidArgumentError:expected to be a float...]
>>> tf.constant(2.0) + tf.constant(40, dtype=tf.float64)
Traceback[...InvalidArgumentError:expected to be a double...]
```

This may be a bit of annoying, but remember that it's for your good cause! And you can use tf.cast() when you need to convert tensors:

```
>>> t2 = tf.constant(40, dtype=tf.float64)
>>> tf.constant(2.0) + tf.cast(t2, tf.float32)
<tf.Tensor: id=136, dtype=float32, numpy=42.0>
```

# Variables

So far, we have used constants: as their name suggests, you cannot modify them. The weights in a neural network need to be tweaked by backpropagation, and other parameters may also need to change over time (e.g., a momentum optimizer tracks grad parameters). What is a variable:

```
>>> v = tf.Variable([[1, 2, 3], [4, 5, 6]])
>>> v
<tf.Variable 'Variable='0' shape=(2, 3) dtype=int32, numpy=array([[1, 2, 3], [4, 5, 6]])>
```

A variable acts much like a constant tensor: you can perform the same operations with it, like with NumPy as it is just like what you picks. It can also be modified in place using the assign() method (or assign_add() or assign_sub()) which increments or decrements the variable by the given value). You can also modify individual cells (or slices), using the cell's (or slice's) assign() method (direct item assignment will not work), or using the scatter_update() and scatter_nd_:

```
v.assign(2 *) # = [[2, 4, 6], [8, 10, 12]]
v[0, 1].assign(42) # = [[2, 42, 6], [8, 10, 12]]
```

![](bbox=[0.165, 0.085, 0.265, 0.165])