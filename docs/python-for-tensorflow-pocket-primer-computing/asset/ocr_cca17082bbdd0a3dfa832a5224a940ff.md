```
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

As another example, x2 specifies row_splits with the value [0, 4, 7, 10], which determines three vectors: the vector whose values are from index 0 through index 3 of x1, the vector whose values are from index 4 through index 6 of x1, and the vector whose values are from index 7 through index 9 of x1. The contents of those