+   counts of the number of occurrences of the item in the unique set. In NumPy and PyTorch, this is to set `return_counts=True`. In TensorFlow, this is to call `tf.unique_with_counts` and use the third returned output. In the case study where we implement a function to sort rows of a matrix, we will use `np.unique` to sort the rows lexicographically.

+   d) These operations get the maximum or minimum values (or the index of it) of an array. They correspond to the mathematical notations max, min, argmax, and argmin.

+   e) The top-k operation returns the top-k values from an array along with the indices of the top-k values. Although NumPy does not have a ready-to-use function to extract top-k values, as we will see in one of the studies in Section 10.2, we can use `np.argpartition` to implement the top-k operation.

+   f) `np.partition` is unique to NumPy. It partitions an array into two parts, based on the kth value of the final sorted array (but not actually doing the sorting on the whole array). The values in the left partition are all smaller, while the values in the right partition are all larger than this value. See Figure 10.1 in the following case study section for an illustration. `np.argpartition` gets the indices to partition and reorder the array.

+   g) Given a sorted array, the `searchsorted` operation finds the index where a new value can be inserted while the sorting order of the new array is still maintained (i.e. still from smallest to largest). If the value is equal to one of the values already existing in the array, then it is either inserted to the left or right of the original number, depending on the argument set for `side="left"` or `side="right"`, respectively. The implementations of the `searchsorted` method by NumPy, Tensorflow, and PyTorch vectorize the search for multiple insertion values simultaneously. To illustrate,

```
import numpy as np

X = np.array([1, 3, 6, 8, 10])
insertion_values = np.array([2, 5, 9, 10, 11])
insertion_indices = np.searchsorted(X, insertion_values)
# array([1, 2, 4, 4, 5])
# Insert the values based on the search sorted indices
y = np.insert(X, insertion_indices, insertion_values)
# array([ 1, 2, 3, 5, 6, 8, 9, 10, 10, 11])
```