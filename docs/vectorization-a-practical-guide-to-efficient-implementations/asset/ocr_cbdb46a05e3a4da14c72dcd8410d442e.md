```
# array([[1, 2, 3],   # 123
#        [1, 3, 2],   # 132
#        [2, 1, 3],   # 213
#        [2, 3, 1],   # 231
#        [3, 1, 2],   # 312
#        [3, 2, 1]])) # 321
```

We can also apply the sorting to string data

```
B = np.array([
    ["a", "c", "b"],
    ["b", "a", "c"],
    ["c", "b", "a"]
])
B_sorted_lex, _ = sort_rows_lex(B)
B_sorted_unique, _ = sort_rows_unique(B)
assert np.all(B_sorted_lex == B_sorted_unique)
# array([['a', 'c', 'b'],
#        ['b', 'a', 'c'],
#        ['c', 'b', 'a']], dtype='<U1')
```

An example application of the sort_rows functions that we implemented above is to sort the xy-coordinates of a set of points that we want to fit a single-exponential curve on, using the method introduced by Jean Jacquellin (Chapter-4). In that specific case study, we have assumed that the data points are already sorted in the correct order. But, in practice, we would need to use sort_rows to preprocess the data before fitting the curve.

# 10.4 Case Study: Reverse Padded Sequence

Tensorflow has a rather magical function tf.reverse_sequence when I need to process my sequence backward. It reverses padded sequence batchwise. For example,

```
import tensorflow as tf
sequence = tf.constant([
    [3, 4, 7, 8, 0, 0, 0, 0],
    [2, 3, 5, 0, 0, 0, 0, 0],
    [8, 7, 6, 5, 4, 0, 0, 0],
])
seq_lengths = tf.constant([4, 6, 5])
reversed_sequence = tf.reverse_sequence(
```