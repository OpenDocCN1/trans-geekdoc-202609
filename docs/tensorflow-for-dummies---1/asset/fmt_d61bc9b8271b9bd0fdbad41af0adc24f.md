
`t3 = tf.constant([4, 2], tf.int16, [3], 'Const', True)`

In this case, the given shape, `[3]`, doesn't match the shape of the first argument, which is `[2]`. As a result, TensorFlow displays the following error:

`TypeError: Expected Tensor's shape: (3,), got (2,).`

### zeros, ones, and fill

The functions `zeros`, `ones`, and `fill` create tensors whose elements all have the same value. For `zeros` and `ones`, the only required argument is `shape`, which identifies the shape of the desired tensor. As an example, the following code creates a simple 1-x-3 vector whose elements equal 0.0:

`zero_tensor = tf.zeros([3])`

Similarly, the following function call creates a 4-x-4 matrix whose elements equal 1.0:

`one_tensor = tf.ones([4, 4])`

The `fill` function requires a `value` parameter, which sets the value of the tensor's elements. The following code creates a three-dimensional tensor whose values are set to 81.0:

`fill_tensor = tf.fill([1, 2, 3], 81.0)`

Unlike `zeros` and `ones`, `fill` doesn't have a `dtype` argument. It can only create tensors containing 32-bit floating point values.

### Creating sequences

The `linspace` and `range` functions create tensors whose elements change regularly between a start and end value. The difference between them is that `linspace` creates a tensor with a specific number of values. For example, the following code creates a 1-x-5 tensor whose elements range from 5.0 to 9.0:

`lin_tensor = tf.linspace(5., 9., 5)`

`# Result: [5. 6. 7. 8. 9.]`

Unlike `linspace`, `range` doesn't accept the number of elements in the tensor. Instead, it computes successive elements by adding a value called a `delta`. In the following code, `delta` is set to 0.5:

`range_tensor = tf.range(3., 7., delta=0.5)`

`# Result: [3.0 3.5 4.0 4.5 5.0 5.5 6.0 6.5]`

Like Python's `range` function, TensorFlow’s `range` function can be called without the `start` parameter. In this case, the starting value is assumed to be 0.0. The following code demonstrates this:

`range_tensor = tf.range(1.5, delta=0.3)`

`# Result: [0.0 0.3 0.6 0.9 1.2]`

If the `delta` parameter is positive, the starting value must be less than the ending value. If `delta` is negative, the starting value must be greater than the ending value.

## Creating Tensors with Random Values

Many TensorFlow applications require tensors that contain random values instead of predetermined values. The `tf` package provides many functions for creating random-valued tensors and [Table 3-3](#07_9788126592555-ch03.xhtml#c03-tbl-0003) lists five of them.

[TABLE 3-3](#07_9788126592555-ch03.xhtml#rc03-tbl-0003) Creating Tensors with Random Values

| **Function** || **Description** |
| --- | --- |
| `random_normal(shape, mean=0.0, stddev=1.0, dtype=tf.float32, seed=None, name=None)` || Creates a tensor with normally distributed values |
| --- | --- |
| `truncated_normal(shape, mean=0.0, stddev=1.0, dtype=tf.float32, seed=None, name=None)` || Creates a tensor with normally distributed values excluding those lying outside two standard deviations |
| `random_uniform(shape, minval=0, maxval=None, dtype=tf.float32, seed=None, name=None)` || Creates a tensor with uniformly distributed values between the minimum and maximum values |
| `random_shuffle(tensor, seed=None, name=None)` || Shuffles a tensor along its first dimension |
| `set_random_seed(seed)` || Set the seed value for all random number generation in the graph |

The `random_normal` and `truncated_normal` functions create tensors containing normally distributed values. Their arguments determine the characterristics of the distribution. [Figure 3-1](#07_9788126592555-ch03.xhtml#c03-fig-0001) shows what a normal distribution looks like with a mean of 0.0 and a standard deviation (*σ*) of 1.0.

![FIGURE 3-1: Values beyond three standard deviations from the mean are highly unlikely.](images/9788126592555-fg0301.png)

[FIGURE 3-1:](#07_9788126592555-ch03.xhtml#rc03-fig-0001) Values beyond three standard deviations from the mean are highly unlikely.

Standard deviation tells you how much a normally distributed variable is expected to vary from the mean. Approximately 68.2 percent of the time, a variable lies within one standard deviation from the mean, while 95.4 percent of the time, the variable lies within two standard deviations.

In the `random_normal` and `truncated_normal` functions, the default mean is 0.0, and the default standard deviation is 1.0. `random_normal` generates random values throughout the distribution, so very large and very small values are unlikely but possible. The following code calls `random_normal` to generate 20 random values:

`rnd_ints = tf.random_normal([10], dtype=tf.float64)`

In contrast, `truncated_normal` guarantees that the generated values lie within two standard deviations from the mean. Any value outside this range will be discarded and reselected. In this manner, `truncated_normal` ensures that the tensor won't contain any improbably large or small values.

`random_uniform` creates a tensor containing uniformly distributed values that lie between a minimum and maximum. Because the distribution is uniform, every value is equally likely.

`random_shuffle` doesn't create a new tensor, but randomly shuffles the values in an existing tensor. This shuffling is limited to the tensor’s first dimension.

Each function in [Table 3-3](#07_9788126592555-ch03.xhtml#c03-tbl-0003) accepts a `seed` parameter that initializes the random number generator. Setting a random seed is important to ensure that sequences aren’t repeated.

You can obtain and set a seed value by calling `set_random_seed`, which accepts a floating-point value and makes the argument the seed for every operation in the current graph. [Chapter 4](#08_9788126592555-ch04.xhtml) discusses the topic of graphs in detail.

## Transforming Tensors

An application must specify the shape of each tensor to be created. The `tf` package provides functions that update tensors and their shapes after creation. [Table 3-4](#07_9788126592555-ch03.xhtml#c03-tbl-0004) lists these transformation functions and provides a description of each.

[TABLE 3-4](#07_9788126592555-ch03.xhtml#rc03-tbl-0004) Functions for Transforming Tensors

| **Function** || **Description** |
| --- | --- |
| `cast(tensor, dtype, name=None)` || Changes the tensor's data type to the given type |
| --- | --- |
| `reshape(tensor, shape, name=None)` || Returns a tensor with the same elements as the given tensor with the given shape |
| `squeeze(tensor, axis=None, name=None, squeeze_dims=None)` || Removes dimensions of size 1 |
| `reverse(tensor, axis, name=None)` || Reverses given dimensions of the tensor |
| `slice(tensor, begin, size, name=None)` || Extracts a portion of a tensor |
| `stack(tensors, axis=0, name='stack')` || Combines a list of tensors into a tensor of greater rank |
| `unstack(tensor, num=None, axis=0, name='unstack')` || Splits a tensor into a list of tensors of lesser rank |

Despite its name, `reshape` doesn't modify an existing tensor. Instead, the function returns a tensor with the same elements as the given tensor and the specified shape. For example, the following code uses `reshape` to convert a four-element vector into a 2-x-2 matrix:

`vec = tf.constant([1., 2., 3., 4.])`

`mat = tf.reshape(vec, [2, 2])`

`# Result: [[1. 2.], [3. 4.]]`

If any dimension of a tensor has a size of 1, calling `squeeze` will remove it from the tensor, thereby reducing the tensor's rank. If the function’s `axis` parameter identifies one or more dimensions, only those dimensions will be affected by `squeeze`.

In the `reverse` function, the `axis` parameter identifies one or more dimensions to be reversed. The following code demonstrates how `reverse` works:

`mat = tf.constant([[1., 2., 3.], [4., 5., 6.]])`

`rev_mat = tf.reverse(end, [0])`

`# Result: [[4. 5. 6.], [1. 2. 3.]]`

`rev_mat = tf.reverse(end, [1])`

`# Result: [[3. 2. 1.], [6. 5. 4.]]`
