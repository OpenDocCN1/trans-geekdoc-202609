```
inc = row_length * tf.range(tf.shape(inputs)[0]+1)
# Compute flat indices for each element
indices = tf.cast(index, index.dtype) + tf.reshape(inc[:-1], (-1, 1))
# Flatten to column vector
indices = tf.reshape(indices, (-1, 1))
# Flatten updates
updates = tf.reshape(inputs, (-1,))
shape = (inc[-1], )
out = tf.scatter_nd(indices, updates, shape)
# reshape: (batch_size, row_length)
out = tf.reshape(out, (tf.shape(index)[0], -1))
return out
```

+   - Lines 5 and 6 compute the length of each row of the output. This is determined as the larger of the maximum index values from `index` and the number of columns of the `inputs`. In essence, we would like to return an output that has just enough number of columns to accommodate all the indices; we also want to return no fewer than the number of columns from the input. Note that this is in preparation for a case study in Chapter 9. Alternatively, we can specify an argument `output_shape` to let the user control the size of the output.
+   - Line 9 computes the start and end indices for each row as a 1D vector. In the above example, we will have `inc = [0, 10, 20, 30, 40]`, where `0:10` is the slice for the first row, `10:20` is the slice for the second row, etc.
+   - Line 11 offsets the row-specific flat indices by the start of the row index. For example, if an index 4 occurs on the second row of the original index matrix, then the corresponding flat index will be `4 + inc[1] = 4 + 10 = 14`.
+   - Line 13 flattens the indices with offset, as a column vector.
+   - Lines 15-17 scatter the 1D array of values to the target 1D array, given the indices.
+   - Line 19 reshapes the 1D tensor back to the desired 2D matrix, with shape `(batch_size, row_length)`.

# Bibliography

Martín Abadi, Ashish Agarwal, Paul Barham, Eugene Brevdo, Zhifeng Chen, Craig Citro, Greg S. Corrado, Andy Davis, Jeffrey Dean, Matthieu Devin, Sanjay Ghemawat, Ian Goodfellow, Andrew Harp, Geoffrey Irving, Michael Isard, Yangqing Jia, Rafal Jozefowicz, Lukasz Kaiser, Manjunath Kudlur, Josh Levenberg, Dan Mane, Rajat Monga, Sherry Moore, Derek Murray, Chris Olah, Mike Schuster, Jonathon Shlens, Benoit Steiner, Ilya Sutskever, Kunal Talwar, Paul