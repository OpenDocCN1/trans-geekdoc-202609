# ### 2.2.7 The notion of data batches

In general, the first axis (axis 0, because indexing starts at 0) in all data tensors you'll come across in deep learning will be the *samples* axis (sometimes called the *samples dimension*). In the MNIST example, “samples” are images of digits.

In addition, deep learning models don’t process an entire dataset at once; rather, they break the data into small batches. Concretely, here’s one batch of our MNIST digits, with a batch size of 128:

```
batch = train_images[:128]
```

And here’s the next batch:

```
batch = train_images[128:256]
```

And the *n*th batch:

```
n = 3
batch = train_images[128 * n:128 * (n + 1)]
```

When considering such a batch tensor, the first axis (axis 0) is called the *batch axis* or *batch dimension*. This is a term you’ll frequently encounter when using Keras and other deep learning libraries.

# ### 2.2.8 Real-world examples of data tensors

Let’s make data tensors more concrete with a few examples similar to what you'll encounter later. The data you’ll manipulate will almost always fall into one of the following categories:

+   Vector data—Rank-2 tensors of shape `(samples, features)`, where each sample is a vector of numerical attributes (“features”)

+   *Timeseries data or sequence data*—Rank-3 tensors of shape `(samples, timesteps, features)`, where each sample is a sequence (of length *timesteps*) of feature vectors

+   Images—Rank-4 tensors of shape `(samples, height, width, channels)`, where each sample is a 2D grid of pixels, and each pixel is represented by a vector of values (“channels”)

+   Video—Rank-5 tensors of shape `(samples, frames, height, width, channels)`, where each sample is a sequence (of length *frames*) of images

# ### 2.2.9 Vector data

This is one of the most common cases. In such a dataset, each single data point can be encoded as a vector, and thus a batch of data will be encoded as a rank-2 tensor (that is, an array of vectors), where the first axis is the *samples axis* and the second axis is the *features axis*.