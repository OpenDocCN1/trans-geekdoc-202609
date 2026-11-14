```
# to conform to the label
dur_adj = apply_duration_constraints(
    dur_pred, dur_true, index, rounding="strict"
)
# <tf.Tensor: shape=(2, 20), dtype=int32, numpy=
# array([[ 68, 232, 74, 147, 79, 159, 366, 81, 70, 229, 70, 148, 152,
# 81, 76, 289, 79, 0, 0, 0],
# [ 79, 141, 80, 77, 151, 79, 68, 83, 367, 74, 76, 249, 63,
# 63, 74, 76, 451, 74, 0, 0]], dtype=int32)>
dur_adj_group = scatter_batch_2d(index, dur_adj)
# <tf.Tensor: shape=(2, 20), dtype=int32, numpy=
# array([[[300, 525, 450, 300, 525, 0, 0, 0, 0, 0, 0,
# 0, 0, 0, 0, 0, 0, 0],
# [300, 375, 450, 150, 375, 150, 525, 0, 0, 0, 0, 0, 0, 0,
# 0, 0, 0, 0, 0, 0]], dtype=int32)>
```

Of course, if we arrange the data inputs as a Pandas DataFrame and use its `DataFrame.groupby.apply` pattern, we can also solve the problem of adding duration constraints. Nonetheless, this case study illustrates that the “groupby-apply” pattern can be implemented using libraries like Tensorflow and PyTorch from scratch when needed.

# ## 9.8 Case Study: Filling of Missing Values in a Sequence

Pandas implement a well-known `.fillna` method for its `pandas.DataFrame` and `pandas.Series` classes to fill in missing values represented by NaNs. In addition to filling the missing values with a constant value like 0, it can also do sequence-based filling based on the value either before or after it, corresponding to the `ffill` and `bfill` methods, respectively. In many neural network implementations, we may sometimes need to fill in missing entries such that a set of features all have exactly the same lengths. Consider the following example with a pair of features `event_type` and `event_timestamp`:

```
import tensorflow as tf

event_type = tf.constant(
[
    [
        "view",
        "click",
        "click",
        "add to cart",
        "buy",
```