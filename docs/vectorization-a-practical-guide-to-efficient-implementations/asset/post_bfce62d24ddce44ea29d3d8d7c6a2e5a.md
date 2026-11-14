

![](img/e891acaacd4fb5b80dab2ed824618203_321_0.png)

### Figure 9.2 Schematic illustration of reshape and reduce operations used to implement groupby-aggregate.

```python
import numpy as np
import matplotlib.pyplot as plt

# Simulate time series
x = np.linspace(0, 10, 500)
y = np.sin(x) + np.random.random(len(x))

# Downsample by averaging groups of 10 elements
x_downsample = x[::10]
y_reshaped = y.reshape((-1, 10))
y_downsample = y_reshaped.mean(axis=1)
y__mean_removed = y_reshaped - y_downsample[:, None]
y__mean_removed = y__mean_removed.reshape((-1, ))

# Plot out the results
fig, ax = plt.subplots(1, 1, figsize=(8, 4))
ax.plot(x, y, label="original", zorder=0)
ax.plot(x, y__mean_removed, label="mean-removed", zorder=1)
ax.set_xlabel("time")
ax.set_ylabel("Value")
ax.legend()
```

Up to Line 11, we compute the groupwise mean just like in the previous example. Then, in Line 12, we remove the mean by broadcasting the y_downsample array to y_reshaped along the second dimension (i.e. the dimension that contains each group). Line 13 flattens the grouped values back to a 1D time series vector. See Figure 9.3 for the results of the plot. See also Figure 9.4 for a schematic illustration of the concept of combining reshaping, reduction, and broadcasting operations to implement the groupby-apply pattern.

Groupwise operation on dense tensor inputs is seen in many computer vision models including You Only Look Once (YOLO) [Terven and Cordova-Esparza, 2023], Visual Transformer(ViT) [Dosovitskiy et al., 2021], and Masked AutoEncoders (MAE)[He et al., 2021]. In the subsequent case study, we will implement ViT from scratch to illustrate how this idea is being used in an application.

![](img/e891acaacd4fb5b80dab2ed824618203_322_0.png)

### Figure 9.3 Mean-removed time series from the code example.

### Figure 9.4 Schematic illustration of broadcasting used to implement groupby-apply.

![](img/e891acaacd4fb5b80dab2ed824618203_322_1.png)

A more general operation than the reshape operation is the sliding window operation: instead of discretely separating each group of values into chunks, a sliding window operation allows the groups to overlap with each other between the start and end of the sequence of value groups. See Figure 9.5 for an illustration.

NumPy creates sliding window views via np.lib.stride_tricks.sliding_window_view, while PyTorch implements equivalent operations torch.Tensor.unfold and torch.nn.functional.unfold. To the best of my knowledge, Tensorflow does not have a ready-to-use sliding window operation, but one can achieve the same effect using tf.gather (see Figure 9.6 for an illustration).

![](img/e891acaacd4fb5b80dab2ed824618203_323_0.png)

![](img/e891acaacd4fb5b80dab2ed824618203_323_1.png)

### Figure 9.6 Illustration of implementation logic of `sliding_window_tf` using Tensorflow's `tf.gather`. (a) We first need to determine the starting indices based on the valid indices of the input, stride, and window size. Notice that we eliminated the last index since the window it will create will exceed the valid indices of the input. (b) Then, we gather indices based on the start index offset and within-window index by summing the two indices together via broadcasting. (c) Finally, we use `tf.gather` to take elements from the original input, based on the indices created from (b).

```python
import tensorflow as tf

def sliding_window_tf(X, window_size, stride, axis=0):
    """Sliding window."""
    start_indices = tf.range(0, tf.shape(X)[axis] - window_size + 1, stride)
    start_indices = tf.reshape(start_indices, (-1, 1))
    slicing_indices = tf.range(window_size)
    slicing_indices = start_indices + slicing_indices
    # use tf.gather to extract slices
    windowed = tf.gather(X, slicing_indices, axis=axis)
    # Change axis so that it follows the np conventions
    windowed = tf.experimental.numpy.moveaxis(windowed, axis+1, -1)

    return windowed
```

- Line 5 creates the expected starting index of each window. The valid window should start and end within valid indices of the input. Therefore, the last start index that would create a valid window only covering the valid indices would end at len(input) - window_size + 1.
- Line 6 reshapes start_indices to a column vector for broadcasting later.
- Lines 7 and 8 create the slicing indices. Within each slice, we will take the window_size number of values. The starting index of each window is offset by the values in start_indices.
- Line 10 gathers the values based on the window-slicing indices.
- Line 12 fixes the order of axes, making it equivalent to the order of NumPy and PyTorch's sliding window outputs.

The following code block illustrates how to use these operations to create groups of sliding windowed values in NumPy, PyTorch, and Tensorflow.

```python
import numpy as np
import tensorflow as tf
import torch

X = np.arange(1, 12)
# Sliding window of size 3, and stride/step 2
windowed_np = np.lib.stride_tricks.sliding_window_view(
    X, window_shape=(3, ), axis=0
)[:,:2]
windowed_torch = torch.tensor(X).unfold(dimension=0, size=3, step=2)
windowed_tf = sliding_window_tf(X, window_size=3, stride=2, axis=0)
assert np.allclose(windowed_np, windowed_torch.numpy())
assert np.allclose(windowed_np, windowed_tf.numpy())
```

An example application of creating a sliding window is to compute the moving average over a time series.

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Simulate time series
x = np.linspace(0, 10, 500)
y = np.sin(x) + np.random.rand(len(x))

# Create sliding window
x_windowed = np.lib.stride_tricks.sliding_window_view(x, (25, ), 0)[:2]
y_windowed = np.lib.stride_tricks.sliding_window_view(y, (25, ), 0)[:2]

# Compute moving average
x_moving_avg = x_windowed.mean(axis=1)
y_moving_avg = y_windowed.mean(axis=1)

# Equivalently in Pandas
y_moving_avg_pd = pd.Series(y).rolling(window=25, step=2).mean()
y_moving_avg_pd.dropna(inplace=True)

# Plot out the results
fig, ax = plt.subplots(1, 1, figsize=(8, 4))
ax.plot(x, y, label="original", zorder=0)
ax.plot(x_moving_avg, y_moving_avg, label="moving-average", zorder=1, c="r")
ax.set_xlabel("Time")
ax.set_ylabel("Value")
ax.legend()
```

Note that in Lines 17 and 18, I have also included an example of using pandas.Series.rolling(...).mean() to compute moving average as well.

![](img/e891acaacd4fb5b80dab2ed824618203_325_0.png)

### Figure 9.7 Moving average of the time series from the code example.

pandas.Series.rolling and pandas.DataFrame.rolling are Pandas' implementation of sliding window operation. See Figure 9.7 for the result of the plot.

## 9.3 Case Study: Vision Transformer (ViT)

The transformer [Vaswani et al., 2017] model is a powerful sequence representation model that is responsible for the subsequent advancements in natural language processing, computer vision, audio processing, and time series forecasting. The transformer model was originally developed around the context of natural language processing, focusing on the task of sequence-to-sequence neural machine translation. However, in the current case study, we will look at a research paper on how to apply a transformer model in computer vision tasks. Specifically, we will look at the use of Vision Transformer, or ViT [Dosovitskiy et al., 2021], to classify images. Figure 9.9 illustrates how ViT works. Conceptually, a transformer model can be seen as a backbone architecture to represent and extract information from a sequence of embeddings of discrete tokens. It takes an input of shape (sequence_length, embed_size) and then outputs a tensor of identical shape. Since image data typically come in the shape of (num_channels, height, width), we need to come up with a strategy to reshape the image inputs to sequences of embeddings. (Here, I am using PyTorch's convention for input image shape; for Tensorflow/Keras convention, it would typically be (width, height, num_channels), but this should not prevent us from generalizing our implementation in the current study using PyTorch to Tensorflow or other libraries.) ViT converts images into sequences by first breaking the 2D images into smaller, fixed-size patches, which are then flattened along the channel, height, and width dimensions to form a sequence

![](img/e891acaacd4fb5b80dab2ed824618203_326_0.png)

### Figure 9.8 Sinusoidal positional encoding of the transformer architecture.

