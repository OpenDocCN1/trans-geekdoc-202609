
```python
import tensorflow as tf

x1 = tf.RaggedTensor.from_row_splits(
    values=[1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
    row_splits=[0, 5, 10])
print("x1",x1)

x2 = tf.RaggedTensor.from_row_splits(
    values=[1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
    row_splits=[0, 4, 7, 10])
print("x2",x2)

x3 = tf.RaggedTensor.from_row_splits(
    values=[1, 2, 3, 4, 5, 6, 7, 8],
    row_splits=[0, 4, 4, 7, 8, 8])
print("x3",x3)
```

Listing 6.3 defines the TF ragged tensors x1, x2, and x3 that are based on the integers from 0 to 10 inclusive. The values parameter specifies a set of values that will be "split" into a set of vectors, using the numbers in the row_splits parameter for the start index and the end index of each vector.

For example, x1 specifies row_splits with the value [0, 5, 10], which determines two vectors: the vector whose values are from index 0 through index 4 of x1, and the vector whose values are from index 5 through index 9 of x1. The contents of these two vectors are [1, 2, 3, 4, 5] and [6, 7, 8, 9, 10], respectively (see the output below).

As another example, x2 specifies row_splits with the value [0, 4, 7, 10], which determines three vectors: the vector whose values are from index 0 through index 3 of x1, the vector whose values are from index 4 through index 6 of x1, and the vector whose values are from index 7 through index 9 of x1. The contents of those two vectors are [1,2,3,4], [5,6,7], and [8, 9, 10], respectively (see the output below).

You can perform a similar analysis for x3, keeping in mind the vector whose start index and end index are [4,4] is an empty vector. The output from launching the code in Listing 6.3 is here:

```
x1: <tf.RaggedTensor [[1, 2, 3, 4, 5], [6, 7, 8, 10]]>
x2: <tf.RaggedTensor [[1, 2, 3, 4], [5, 6, 7], [8, 9, 10]]>
x3: <tf.RaggedTensor [[1, 2, 3, 4], []], [5, 6, 7], [8], []]]
```

If you want to generate a list of values, invoke the to_list() operator. For instance, suppose you define x4 as follows:

```python
x4 = tf.RaggedTensor.from_row_splits(values=[1, 2, 3, 4, 5, 6, 7, 8, 9], row_splits=[0, 5, 10]).to_list()
print("x4:", x4)
```

The output from the preceding code snippet is here (which you can compare with the output for x1 in the preceding output block):

```
x4: [[1, 2, 3, 4, 5], [6, 7, 8, 9, 10]]
```

You can also create higher-dimensional ragged tensors in TF. For example, the following code snippet creates a two-dimensional ragged tensor in TF:

```python
RaggedTensor.from_nested_row_splits(flat_values=[3, 1, 4, 1, 5, 9, 2, 6], nested_row_splits=([0, 3, 3, 5], [0, 4, 4, 7, 8, 8])).to_list()
```

The preceding code snippet generates the following output:

```
[[3, 1, 4, 1], [], [5, 9, 2]], [], [[6], []]]
```

# WHAT ARE LAMBDA EXPRESSIONS?

In brief, a lambda expression is an anonymous function. Use lambda expressions to define local functions that can be passed as arguments or returned as the value of function calls.

Informally, a lambda expression takes an input variable and performs some type of operation (specified by you) on that variable. For example, here is a "bare bones" lambda expression that adds the number 1 to an input variable x:

```python
lambda x: x + 1
```

You can use the preceding lambda expression in a valid TensorFlow code snippet, as shown here (dx is a TensorFlow Dataset that is defined elsewhere):

```python
dx.map(lambda x: x + 1)
```

Even if you are unfamiliar with TensorFlow Datasets or the map() operator, you can still understand the preceding code snippet. The next section contains a complete TensorFlow code sample that illustrates how to use the preceding lambda expression.

# A LAMBDA EXPRESSION IN TENSORFLOW

Listing 6.4 illustrates how to use a lambda expression.

# LISTING 6.4: tf-plus.py

```python
import tensorflow as tf
# (Example code for listing 6.4)
```

The next section contains a complete TensorFlow code sample that illustrates how to use the preceding lambda expression.

# WHAT ARE ITERATORS?

An iterator is similar to a cursor in other languages. You can think of an iterator as something that points to the next element in a dataset. TensorFlow supports four types of iterators:

- One-shot
- Initializable
- Reinitializable
- Feedable

A one-shot iterator can iterate only once. After we reach the end of the dataset, it will raise an Exception; it will not yield more elements.

An initializable iterator can be dynamically updated: invoke its initializer and pass new data via the feed_dict. If dx is an instance of tf.Dataset.

A reinitializable iterator can be initialized from a different Dataset. This type of iterator is very useful when datasets require some additional transformation.

A feedable iterator allows you to select from a collection of items this type of iterator is essentially a selector.

Working with iterators involves the following steps:

1. create a dataset
2. create an iterator
3. point the iterator
4. advance the iterator
5. handle the end of the dataset

Notice that TensorFlow provides several types of iterators, as listed above.

# TensorFlow Iterators

Listing 6.5 displays the contents of tf-init-iterator.py that illustrates how to define a reusable iterator.

# LISTING 6.5: tf-init-iterator.py

```python
import tensorflow as tf
import numpy as np
x = np.arange(0, 10)
dx = tf.data.Dataset.from_tensor_slices(x)
# create an initializable iterator
iterator = dx.make_initializable_iterator()
# extract an element
next_element = iterator.get_next()
with tf.Session() as sess:
    sess.run(iterator.initializer)
    for i in range(15):
        val = sess.run(next_element)
        if i % 5 == 0 and i > 0:
            sess.run(iterator.initializer)
```

Listing 6.5 initializes the variable x as NumPy array. The next section will explain how to define a reusable iterator in TensorFlow. The output from launching the code in Listing 6.5 is here:

```
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 0, 1, 2, 3, 4]
```
