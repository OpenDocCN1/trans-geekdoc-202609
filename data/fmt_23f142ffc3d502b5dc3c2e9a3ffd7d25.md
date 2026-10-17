
### 张量变换函数

| `cast(tensor, dtype, name=None)` || Changes the tensor's data type to the given type |

| --- | --- |

| `reshape(tensor, shape, name=None)` || Returns a tensor with the same elements as the given tensor with the given shape |

| `squeeze(tensor, axis=None, name=None, squeeze_dims=None)` || Removes dimensions of size 1 |

| `reverse(tensor, axis, name=None)` || Reverses given dimensions of the tensor |

| `slice(tensor, begin, size, name=None)` || Extracts a portion of a tensor |

| `stack(tensors, axis=0, name='stack')` || Combines a list of tensors into a tensor of greater rank |

| `unstack(tensor, num=None, axis=0, name='unstack')` || Splits a tensor into a list of tensors of lesser rank |

尽管名称如此，`reshape` 并不会修改现有张量。相反，该函数返回一个与给定张量具有相同元素且形状指定的张量。例如，以下代码使用 `reshape` 将一个四元素向量转换为 2-x-2 矩阵：

```
vec = tf.constant([1., 2., 3., 4.])
mat = tf.reshape(vec, [2, 2])
# Result: [[1. 2.], [3. 4.]]
```

如果张量的某个维度大小为 1，调用 `squeeze` 将会将其从张量中移除，从而降低张量的秩。如果函数的 `axis` 参数标识一个或多个维度，则只有这些维度会受到 `squeeze` 的影响。

在 `reverse` 函数中，`axis` 参数标识要反转的一个或多个维度。以下代码演示了 `reverse` 的工作原理：

```
mat = tf.constant([[1., 2., 3.], [4., 5., 6.]])
rev_mat = tf.reverse(end, [0])
# Result: [[4. 5. 6.], [1. 2. 3.]]
rev_mat = tf.reverse(end, [1])
# Result: [[3. 2. 1.], [6. 5. 4.]]
rev_mat = tf.reverse(end, [0, 1])
# Result: [[6. 5. 4.], [3. 2. 1.]]
```

The `slice` function extracts subtensors from a tensor. The `begin` parameter identifies the index of the first element to be extracted, and `size` identifies the shape of the tensor to be extracted, starting from the `begin` location.

For example, suppose that you want to extract the lower-right 2-x-2 matrix from a 3-x-3 matrix. The index of the first extracted element is `[1, 1]` and the size of the desired tensor is `[2, 2]`. The following code uses `slice` to perform this extraction:

```
mat = tf.constant([[1., 2., 3.], [4., 5., 6.], [7., 8., 9.]])
slice_mat = tf.slice(mat, [1, 1], [2, 2])
```

`# Result: [[5. 6.] [7. 8.]]`

`stack` accepts a list of tensors of rank N and returns a single tensor of rank N+1. In addition to having the same rank, the input tensors must have the same shape. The following code demonstrates how `stack` can be used. The function combines three one-dimensional tensors into a two-dimensional tensor:

```
t1 = tf.constant([1., 2.])
t2 = tf.constant([3., 4.])
t3 = tf.constant([5., 6.])
t4 = tf.stack([t1, t2, t3])
```

When these operations execute, `t4` will equal `[[1. 2.] [3. 4.] [5. 6.]]`. If the `axis` parameter is set to 1, stacking will be performed along the second dimension, so `t4` will set to `[[1. 3. 5.] [2. 4. 6.]]`.

`unstack` performs the inverse operation of `stack`. That is, `unstack` accepts a tensor of rank N and returns a list of tensors of rank N-1. The `num` parameter determines how many tensors should be unpacked, and if this isn't set, `unstack` infers the number from the tensor's shape.

## Creating Operations

Machine learning applications are fundamentally mathematical, and TensorFlow provides a wealth of routines for performing mathematical operations on tensors. Each routine is represented by a function of the `tf` package, and each function returns a tensor. This section presents a large portion of the operations available, but the `tensorflow` package provides many more functions than those discussed here.

To describe these functions, I use statements like "function X performs operation Y." But these statements aren't completely accurate. These functions, like the transformation functions discussed in the preceding section, don't actually perform their corresponding operations — at least, not directly.

For example, `tf.multiply` doesn't immediately multiply its arguments and return a product. Instead, it adds a multiplication operation to the current graph, and when a session executes the graph, the multiplication will be performed along with the rest of the graph's operations. This process may seem confusing, but don't be concerned. Chapter 4 looks at graphs and sessions in detail.

### Basic math operations

When it comes to TensorFlow operations, its best to start simple. Table 3-5 lists 12 functions that perform basic math operations.

TABLE 3-5 Basic Math Operations

| **Function** || **Description** |

| --- | --- |

| `add(x, y, name=None)` || Adds two tensors |

| --- | --- |

| `subtract(x, y, name=None)` || Subtracts two tensors |

| `multiply(x, y, name=None)` || Multiplies two tensors |

| `divide(x, y, name=None)` || Divides the elements of two tensors |

| `div(x, y, name=None)` || Divides the elements of two tensors |

| `add_n(inputs, name=None)` || Adds multiple tensors |

| `scalar_mul(scalar, x)` || Scales a tensor by a scalar value |

| `mod(x, y, name=None)` || Performs the modulo operation |

| `abs(x, name=None)` || Computes the absolute value |

| `negative(x, name=None)` || Negates the tensor's elements |

| `sign(x, name=None)` || Extracts the signs of the tensor's element |

| `reciprocal(x, name=None)` || Computes the reciprocals |

The first four functions perform element-wise arithmetic. The following code demonstrates how they work:

```
a = tf.constant([3., 3., 3.])
b = tf.constant([2., 2., 2.])
sum = tf.add(a, b) # [ 5. 5. 5. ]
diff = tf.subtract(a, b) # [ 1. 1. 1. ]
prod = tf.multiply(a, b) # [ 6. 6. 6. ]
quot = tf.divide(a, b) # [ 1.5 1.5 1.5 ]
```

Applications can perform identical operations by using regular Python operators, such as `+`, `-`, `*`, `/`, and `//`. For example, the following two lines of code create the same tensor:

```
total = tf.add(a, b) # [ 5. 5. 5. ]
total2 = a + b # [ 5. 5. 5. ]
```

When operating on floating-point values, `div` and `divide` produce the same result. But for integer division, `divide` returns a floating-point result, and `div` returns an integer result. The following code demonstrates the difference between them:

```
a = tf.constant([3, 3, 3])
b = tf.constant([2, 2, 2])
div1 = tf.divide(a, b) # [ 1.5 1.5 1.5 ]
div2 = a / b # [ 1.5 1.5 1.5 ]
div3 = tf.div(a, b) # [ 1 1 1 ]
div4 = a // b # [ 1 1 1 ]
```

The `div` function and the `/` operator both perform element-wise division. In contrast, the `divide` function performs Python-style division.

### Rounding and comparison

Most of the mathematical routines in this book accept floating-point values as input and return floating-point values as output. But many applications need to convert floating-point values into integer values. For this reason, TensorFlow provides the rounding operations listed in Table 3-6.

TABLE 3-6 Rounding and Comparison Operations

| **Function** || **Description** |

| --- | --- |

| `round(x, name=None)` || Rounds to the nearest integer, rounding up if there are two nearest integers |

| --- | --- |

| `rint(x, name=None)` || Rounds to the nearest integer, rounding to the nearest even integer if there are two nearest integers |

| `ceil(x, name=None)` || Returns the smallest integer greater than the value |

| `floor(x, name=None)` || Returns the greatest integer less than the value |

| `maximum(x, y, name=None)` || Returns a tensor containing the larger element of each input tensor |

| `minimum(x, y, name=None)` || Returns a tensor containing the smaller element of each input tensor |

| `argmax(x, axis=None, name=None, dimension=None)` || Returns the index of the greatest element in the tensor |

| `argmin(x, axis=None, name=None, dimension=None)` || Returns the index of the smallest element in the tensor |

Table 3-6 also lists functions that perform comparisons. These functions return maximum and minimum values, both within a tensor and across two tensors.

The `round` function examines each element of a tensor and returns the closest integer. If two closest integers are equally close, it returns the one further from zero. `rint` is similar, but rounds to the nearest even value. The following code demonstrates how you can use `round`, `rint`, `ceil`, and `floor`:
