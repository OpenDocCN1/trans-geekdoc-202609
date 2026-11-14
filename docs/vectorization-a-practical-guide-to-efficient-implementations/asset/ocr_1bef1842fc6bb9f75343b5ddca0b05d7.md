```
# although the following does not throw the error
replaced_values = [mapping.get(v, "") for v in values.numpy()])
# the replaced results are incorrect
# ["00", "00", "00"]
```

Therefore, additional casting is needed. Typically, we can use the `.astype(str)` method to cast from bytes to string. To illustrate,

```
tf_string_array = tf.constant((["A", "B", "C"]), dtype=tf.string)
# <tf.Tensor: shape=(3,), dtype=string, numpy=array([b'A', b'B', b'C'],
~ dtype=object)>

# Numpy array of bytes (object dtype)
np_string_array_bytes = tf_string_array.numpy()
# array([b'A', b'B', b'C'], dtype=object)

# Casting to string
np_string_array_str = tf_string_array.numpy().astype(str)
# array(['A', 'B', 'C'], dtype='<U1')
```

This may seem inconvenient, but Tensorflow's `bytes` data type can be quite versatile. In the last section of the chapter (Section 6.7), we will examine how Tensorflow can represent structured data using byte strings.

# 6.1.4 PyTorch

PyTorch's `torch.Tensor` does not handle string or bytes data types, so it relies on external libraries like NumPy and Pandas to prepare and transform the string data into numerical representations first before passing it to the main model. PyTorch has an extension, `torchtext`, which hosts a collection of routines to prepare text for NLP tasks.

# 6.2 String Operations

Table 6.1 provides a list of string tensor operations that help vectorize string preprocessing during machine learning tasks. It can be seen that typical string processing tasks in native Python have corresponding operations implemented in Pandas and Tensorflow, thus saving the users from writing for loops when processing a batch of string values.