
# Chapter 5: Sample Code in TensorFlow

In this chapter we are going to examine the code at:

[https://github.com/lazyprogrammer/machine\_learning\_examples/blob/master/cnn\_class/cnn\_tf.py](https://github.com/lazyprogrammer/machine_learning_examples/blob/master/cnn_class/cnn_tf.py)

We are going to do a similar thing that we did with Theano, which is examine each part of the code more in depth before putting it all together.

Hopefully it helps you guys isolate each of the parts and gain an understanding of how they work.

This is the ConvPool in TensorFlow. It’s almost the same as what we did with Theano except that the `conv2d()` function takes in a new parameter called `strides`.

```
def convpool(X, W, b):
    # just assume pool size is (2,2) because we need to augment it with 1s
    conv_out = tf.nn.conv2d(X, W, strides=[1, 1, 1, 1], padding='SAME')
    conv_out = tf.nn.bias_add(conv_out, b)
    pool_out = tf.nn.max_pool(conv_out, ksize=[1, 2, 2, 1], strides=[1, 2, 2, 1], padding='SAME')
    return pool_out
```

In the past we just assumed that we had to drag the filter along every point of the signal, but in fact we can move with any size step we want, and that’s what `stride` is. We’re also going to use the `padding` parameter to control the size of the output.

Remember that the bias is a 1-D vector, and we used the `dimshuffle` function in Theano to add it to the convolution output. Here we can just use a function that TensorFlow built called `bias_add()`.

Next we call the `max_pool()` function. Notice that the `ksize` parameter is kind of like the `poolsize` parameter we had with Theano, but it’s now 4-D instead of 2-D. We just add ones at the ends. Notice that this function ALSO takes in a `strides` parameter, meaning we can `max_pool` at EVERY step, but we’ll just use non-overlapping sub-images like we did previously.

The next step is to rearrange the inputs. Remember that convolution in Theano is not the same as convolution in TensorFlow. That means we have to adjust not only the input dimensions but the filter dimensions as well. The only change with the inputs is that the color now comes last.

```
def rearrange(X):
    # input is (32, 32, 3, N)
    # output is (N, 32, 32, 3)
    N = X.shape[-1]
    out = np.zeros((N, 32, 32, 3), dtype=np.float32)
    for i in xrange(N):
        for j in xrange(3):
            out[i, :, :, j] = X[:, :, j, i]
    return out / 255
```

The next step is unique to the TensorFlow implementation. If you recall, TensorFlow allows us to not have to specify the size of each dimension in its input.

This is great and allows for a lot of flexibility, but I hit a snag during development, which is my RAM started swapping when I did this. If you haven’t noticed yet the size of the SVHN data is pretty big, about 73k samples.

So one way around this is to make the shapes constant, which you’ll see later. That means we’ll always have to pass in `batch_sz` number of samples each time, which means the total number of samples we use has to be a multiple of it. In the code I used exact numbers but you can also calculate it using the data.

`X = tf.placeholder(tf.float32, shape=(batch_sz, 32, 32, 3), name='X')`

`T = tf.placeholder(tf.float32, shape=(batch_sz, K), name='T')`

Just to reinforce this idea, the filter is going to be in a different order than before. So now the dimensions of the image filter come first, then the number of color channels, then the number of feature maps.

`# (filter_width, filter_height, num_color_channels, num_feature_maps)`

`W1_shape = (5, 5, 3, 20)`

`W1_init = init_filter(W1_shape, poolsz)`

`b1_init = np.zeros(W1_shape[-1], dtype=np.float32) # one bias per output feature map`

`# (filter_width, filter_height, old_num_feature_maps, num_feature_maps)`

`W2_shape = (5, 5, 20, 50)`

`W2_init = init_filter(W2_shape, poolsz)`

`b2_init = np.zeros(W2_shape[-1], dtype=np.float32)`

`# vanilla ANN weights`

`W3_init = np.random.randn(W2_shape[-1]*8*8, M) / np.sqrt(W2_shape[-1]*8*8 + M)`

`b3_init = np.zeros(M, dtype=np.float32)`

`W4_init = np.random.randn(M, K) / np.sqrt(M + K)`

`b4_init = np.zeros(K, dtype=np.float32)`

For the vanilla ANN portion, also notice that the outputs of the convolution are now a different size. So now it’s 8 instead of 5.

For the forward pass, the first 2 parts are the same as Theano.

One thing that’s different is TensorFlow objects don’t have a `flatten` method, so we have to use `reshape`.

`Z1 = convpool(X, W1, b1)`

`Z2 = convpool(Z1, W2, b2)`

`Z2_shape = Z2.get_shape().as_list()`

`Z2r = tf.reshape(Z2, [Z2_shape[0], np.prod(Z2_shape[1:]])`

`Z3 = tf.nn.relu( tf.matmul(Z2r, W3) + b3 )`

`Yish = tf.matmul(Z3, W4) + b4`

Luckily this is pretty straightforward EVEN when you pass in `None` for the input shape parameter. You can just pass in `-1` in `reshape` and it will be automatically be calculated. But as you can imagine this will make your computation take longer.

The last step is to calculate the output just before the softmax. Remember that with TensorFlow the cost function requires the logits without softmaxing, so we won’t do the softmax at this point.

The full code is as follows:

```
import numpy as np
import tensorflow as tf
import matplotlib.pyplot as plt
from datetime import datetime
from scipy.signal import convolve2d
from scipy.io import loadmat
from sklearn.utils import shuffle

def y2indicator(y):
    N = len(y)
    ind = np.zeros((N, 10))
    for i in xrange(N):
        ind[i, y[i]] = 1
    return ind

def error_rate(p, t):
    return np.mean(p != t)

def convpool(X, W, b):
    # just assume pool size is (2,2) because we need to augment it with 1s
    conv_out = tf.nn.conv2d(X, W, strides=[1, 1, 1, 1], padding='SAME')
    conv_out = tf.nn.bias_add(conv_out, b)
    pool_out = tf.nn.max_pool(conv_out, ksize=[1, 2, 2, 1], strides=[1, 2, 2, 1], padding='SAME')
```
