# Table 2.8 List of array/tensor reversing operations in Python, NumPy, Tensorflow, and PyTorch.

| Operations | Python | NumPy | Tensorflow | PyTorch |
| :--- | :--- | :--- | :--- | :--- |
| Reverse | `list[::-1]` | `np.flip` | `tf.reverse` | `torch.flip` |
| Reverse left-right (axis=0) | N/A | `np.fliplr` | `tf.experimental.numpy.fliplr` | `torch.fliplr` |
| Reverse up-down (axis=1) | N/A | `np.flipud` | `tf.experimental.numpy.flipud` | `torch.flipud` |
| Reverse padded sequence^a | N/A | N/A | `tf.reverse_sequence` | N/A |

Notes:
a) The padded sequence reverse in Tensorflow `tf.reverse_sequence` is not the same as simple `tf.reverse`. It will reverse only part identified as part of the sequence and leave the padding on the right as is. For example, suppose we have a zero-padded sequence `s=[1, 2, 3, 4, 0, 0, 0]`. `tf.reverse` will reverse the entire sequence including the padding, as `[0, 0, 0, 4, 3, 2, 1]`, whereas `tf.reverse_sequence` can reverse the sequence at the non-padding entries as `[4, 3, 2, 1, 0, 0, 0]`, when given expected sequence length. At the time of writing this book, Tensorflow is the only library that implements this padded sequence reverse method. In Chapter 10, we will see how to implement this method using NumPy as well.