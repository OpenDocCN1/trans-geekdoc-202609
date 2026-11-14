Furthermore, to sample multiple items simultaneously without replacement, instead of obtaining the argmax of the perturbed logits, we can obtain top-k indices from the list of perturbed logits for all classes.

In the following code sample, we will implement a function that solves the negative sampling problem when training a multi-label classification model, where the positive labels may include multiple classes. For example, in object detection tasks, a single image may contain multiple objects (e.g. an apple and a cup on a table), so the label will be ["apple", "cup", "table"]. We would like to create negative labels so that the model can learn the image does not contain certain items, such as ["cat", "cereal", "spoon", "fork"]. Since an image may contain a variable number of objects, we therefore use a ragged sparse tensor to represent the labels (recall in Chapter 8). We also assume the labels are already converted from string to 1-based indices (recall in Chapter 6).

```
import numpy as np
import tensorflow as tf
def gumbel_max_sample_without_replacement(
     true_labels: tf.SparseTensor,
     num_neg_samples: int,
     vocab_size: int,
     vocab_freq: tf.Tensor = None,
     shuffle: bool = True,
 ):
 """
 Use Gumbel-Max trick to select negative samples.
 * true_labels: (batch_size, None)
 * Positive / label class indices, 1-based indexing
 num_nega_samples:
 Number of negative samples to take
 * vocab_size:
 Number of items in the categorical variable
 * vocab_freq:
 The distribution of the classes to take samples from.
 Does not have to be normalized.
 If None, assuming uniform sampling.
 * shuffle:
 Whether or not to shuffle the results so that the
 positive labels are not always at the beginning of
 the resulting sample.
 """
 # Default to uniform sampling if vocab_freq is None
 if vocab_freq is None:
     vocab_freq = tf.ones((vocab_size,), tf.float32)
 # Compute proba for the batch
 true_proba = tf.sparse.to_indicator(
     true_labels, vocab_size + 1
 )
 )
```