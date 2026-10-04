
In the `map` method, the function receives each element of the input dataset and produces an element to be inserted in the output dataset. In the following code, the lambda multiplies each element of the input dataset by 2 and inserts the resulting element into the output dataset.

```
vals = tf.constant([[2., 3.], [4., 5.], [6., 7.]])
ds1 = tf.data.Dataset.from_tensor_slices(vals)
ds2 = ds1.map(lambda x: x*2)
# ds2 contains [[4., 6.], [8., 10.], [12., 14.]]
```

`flat_map` is like `map`, but instead of returning an element of the output dataset, the function returns an entire dataset. `flat_map` concatenates the output datasets together and returns the flattened result.

```
vals = tf.constant([2, 3], dtype=tf.int64)
ds1 = tf.data.Dataset.from_tensor_slices(vals)
ds2 = ds1.flat_map(lambda x: tf.data.Dataset.range(x))
# ds2 contains [0, 1, 0, 1, 2]
```

As with `flat_map`, the function in `interleave` returns a dataset for each element of the input dataset. Unlike `flat_map`, it doesn't necessarily concatenate the resulting datasets. The `cycle_length` parameter identifies how many elements should be interleaved.

For example, if you set `cycle_length` to 2, the output dataset will contain the first elements of the first two datasets, then the next two elements of the first two datasets, and so on. The following code shows how `interleave` works.

```
vals = tf.constant([2, 3, 4], dtype=tf.int64)
ds1 = tf.data.Dataset.from_tensor_slices(vals)
ds2 = ds1.interleave(lambda x: tf.data.Dataset.range(x), cycle_length=3)
# ds2 contains [0, 0, 0, 1, 1, 1, 2, 2, 3]
```

This code provides three elements to the lambda and sets the `cycle_length` to 3. As a result, the output dataset contains the first three elements of the three datasets, then the next three elements of the three datasets, and so on.

The `zip` method also interleaves multiple datasets, but it doesn't accept a function or `cycle_length` parameter. This method always takes the first value from the first element, then the first value from the second element, and proceeds onward. The following code demonstrates how `zip` can be used.

```
ds1 = tf.data.Dataset.range(0, 3)
ds2 = tf.data.Dataset.range(10, 13)
ds3 = tf.data.Dataset.range(20, 23)
ds4 = tf.data.Dataset.zip((ds1, ds2, ds3))
# ds4 contains (0, 10, 20), (1, 11, 21), (2, 12, 22)
```

The `datasets` parameter of `zip` accepts the input datasets in a nested structure. An application can set this equal to a tuple, but not a list.

## Iterators

An `Iterator` lets you iterate through the elements of one or more `Dataset`s. TensorFlow provides four types of iterators:

*   `One-shot`: Iterates once through the dataset, can't be parameterized
*   `Initializable`: Requires special initialization, can be parameterized
*   `Reinitializable`: Can be associated with multiple datasets, must be initialized before each iteration
*   `Feedable`: Can be associated with multiple datasets, doesn’t need to be initialized before each iteration

### One-shot iterators

One-shot iterators are the simplest of the four, but they can iterate only once through a dataset’s elements. An application can create a one-shot iterator for a dataset by calling a dataset’s `make_one_shot_iterator` method.

After you create an iterator, you can access the next available element by calling `get_next`. This method resembles the `next` method of a regular Python iterator. To demonstrate how `get_next` is used, the following code creates a dataset with one element and calls `get_next` to print the element's value:

```
# Create the dataset and iterator
tensor = tf.constant([1, 2, 3])
dset = tf.data.Dataset.from_tensors(tensor)
iterator = dset.make_one_shot_iterator()

# Access the next element
next_elem = iterator.get_next()

# Print the element's value
with tf.Session() as sess:
    print('Element: ', sess.run(next_elem))

# Output: 'Element: [1 2 3]'
```

When a session evaluates a tensor returned by `get_next`, the tensor takes the value of the dataset’s next element. To demonstrate, the following code creates a dataset with five elements and repeatedly evaluates the tensor returned by `get_next`:

```
# Create the dataset and iterator
dset = tf.data.Dataset.range(5)
iterator = dset.make_one_shot_iterator()

# Access the next element
next_elem = iterator.get_next()

# Print the values of the elements
with tf.Session() as sess:
    for i in range(5):
        print('Element: ', sess.run(next_elem))
```

In this code, `Dataset.range` creates a dataset with five elements. The iterator loops through the dataset, and the session prints the value of each. The resulting output is as follows:

```
Element: 0
Element: 1
Element: 2
Element: 3
Element: 4
```

A one-shot iterator can iterate through a dataset only once. If an application attempts to execute a second loop through the dataset, TensorFlow will raise an `OutOfRangeError`: End of sequence.

### Initializable iterators

In addition to creating datasets from constant tensors, you can create datasets from placeholders. These kind of datasets are called *parameterized datasets*, and they receive their content when the application executes a session that feeds data to the placeholder.

One-shot iterators can't iterate through parameterized datasets, but initializable iterators can. To create an initializable iterator and iterate through a parameterized dataset, you need to perform six steps:

1.  **Create a dataset from a placeholder by calling `from_tensors` or `from_tensor_slices`.**
2.  **Create an iterator for the dataset by calling the dataset's `make_initializable_iterator` method.**
3.  **Obtain the next element by calling the iterator’s `get_next` method.**
4.  **Initialize the iterator by running its initializer property in a session.**
5.  **Associate the iterator's placeholder with data by setting the `feed_dict` parameter in the session’s run method.**
6.  **Access the iterators elements in a session by evaluating the result of the `get_next` method.**

This process may seem complicated, but parameterized datasets can be very helpful. To demonstrate how these datasets can be used, the following code creates a dataset from a placeholder that holds four floating-point values. Then it accesses the dataset using an initializable iterator:

```
# Create a placeholder and parameterized dataset
holder = tf.placeholder(tf.float32, shape=[4])
dset = tf.data.Dataset.from_tensor_slices(holder)

# Create the iterator and access its first element
iter = dset.make_initializable_iterator()
next_elem = iter.get_next()

with tf.Session() as sess:

    # Initialize the iterator
    sess.run(iter.initializer,
             feed_dict={holder: [0., 1., 2., 3.]})
    for _ in range(4):
        print('Element: ', sess.run(next_elem))
```

Looking at this code, it's important to see that the first call to `sess.run` initializes the iterator and feeds values to the parameterized dataset through the placeholder. After this initialization, the application can access the iterator’s values through the value returned by `get_next`.

### Reinitializable iterators

If you need to associate an iterator with multiple datasets, one-shot iterators and initializable iterators won't be sufficient. Instead, the application can create a *reinitializable iterator* by calling `Iterator.from_structure`:

```
Iterator.from_structure(output_types, output_shapes=None, shared_name=None)
```

A reinitializable iterator doesn’t need to know about specific datasets in advance, but it needs to know about the types and shapes of their elements. An application can set `output_types` and `output_shapes` by accessing the identically named properties of a `Dataset` instance.
