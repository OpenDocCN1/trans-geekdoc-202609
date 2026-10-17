
The default behavior for `tf.GradientTape` is to “play once and then discard.” However, it’s possible to specify a persistent tape, which means that the values are persisted and therefore the tape can be “played” multiple times. The next section contains several examples of `tf.GradientTape`, including an example of a persistent tape.

## **Examples of tf.GradientTape**

[Listing E.24](#appE.xhtml#listE.24) displays the contents of `tf2_gradient_tape1.py` that illustrates how to invoke `tf.GradientTape` in TF 2. This example is one of the simplest examples of using `tf.GradientTape` in TF 2.

***LISTING E.24: tf2_gradient_tape1.py***

```python
import tensorflow as tf
w = tf.Variable([[[1.0]]])
with tf.GradientTape() as tape:
    loss = w * w
    grad = tape.gradient(loss, w)
print("grad:", grad)
```

[Listing E.24](#appE.xhtml#listE.24) defines the variable `w`, followed by a with statement that initializes the variable `loss` with expression `w*w`. Next, the variable `grad` is initialized with the derivative that is returned by the tape, and then evaluated with the current value of `w`.

As a reminder, if we define the function `z = w*w`, then the first derivative of `z` is the term `2*w`, and when this term is evaluated with the value `1.0` for `w`, the result is `2.0`. Launch the code in [Listing E.24](#appE.xhtml#listE.24) and you will see the following output:

grad: tf.Tensor([[[2.]], shape=(1, 1), dtype=float32)

Using the watch() Method of tf.GradientTape

[Listing E.25](#appE.xhtml#listE.25) displays the contents of `tf2_gradient_tape2.py` that also illustrates the use of `tf.GradientTape` with the watch() method in TF 2.

***LISTING E.25: tf2_gradient_tape2.py***

```python
import tensorflow as tf
x = tf.constant(3.0)
with tf.GradientTape() as g:
    g.watch(x)
    y = 4 * x * x
    dy_dx = g.gradient(y, x)
```

[Listing E.25](#appE.xhtml#listE.25) contains a similar with statement as [Listing E.24](#appE.xhtml#listE.24), but this time a watch() method is also invoked to “watch” the tensor `x`. As you saw in the previous section, if we define the function `y = 4*x*x`, then the first derivative of `y` is the term `8*x`; when the latter term is evaluated with the value `3.0`, the result is `24.0`.

Launch the code in [Listing E.25](#appE.xhtml#listE.25) and you will see the following output:

dy_dx: tf.Tensor(24.0, shape=(), dtype=float32)

### **Using Nested Loops with tf.GradientTape**

[Listing E.26](#appE.xhtml#listE.26) displays the contents of `tf2_gradient_tape3.py` that also illustrates how to define nested loops with `tf.GradientTape` in order to calculate the first and the second derivative of a tensor in TF 2.

***LISTING E.26: tf2_gradient_tape3.py***

```python
import tensorflow as tf
x = tf.constant(4.0)
with tf.GradientTape() as t1:
    with tf.GradientTape() as t2:
        t1.watch(x)
        t2.watch(x)
        z = x * x * x
    dz_dx = t2.gradient(z, x)
    d2z_dx2 = t1.gradient(dz_dx, x)
print("First dz_dx:", dz_dx)
print("Second d2z_dx2:", d2z_dx2)
x = tf.Variable(4.0)
with tf.GradientTape() as t1:
    with tf.GradientTape() as t2:
        z = x * x * x
    dz_dx = t2.gradient(z, x)
    d2z_dx2 = t1.gradient(dz_dx, x)
print("First dz_dx:", dz_dx)
print("Second d2z_dx2:", d2z_dx2)
```

The first portion of [Listing E.26](#appE.xhtml#listE.26) contains a nested loop, where the outer loop calculates the first derivative and the inner loop calculates the second derivative of the term `x*x*x` when `x` equals 4. The second portion of [Listing E.26](#appE.xhtml#listE.26) contains another nested loop that produces the same output with slightly different syntax.

In case you’re a bit rusty regarding derivatives, the next code block shows you a function `z`, its first derivative `z'`, and its second derivative `z''`:

z = x*x*x  
z' = 3*x*x  
z'' = 6*x  

When we evaluate `z`, `z'`, and `z''` with the value 4.0 for `x`, the result is 64.0, 48.0, and 24.0, respectively. Launch the code in [Listing E.25](#appE.xhtml#listE.25) and you will see the following output:

First dz_dx: tf.Tensor(48.0, shape=(), dtype=float32)  
Second d2z_dx2: tf.Tensor(24.0, shape=(), dtype=float32)  
First dz_dx: tf.Tensor(48.0, shape=(), dtype=float32)  
Second d2z_dx2: tf.Tensor(24.0, shape=(), dtype=float32)

### **Other Tensors with tf.GradientTape**

[Listing E.27](#appE.xhtml#listE.27) displays the contents of `tf2_gradient_tape4.py` that illustrates how to use `tf.GradientTape` in order to calculate the first derivative of an expression that depends on a 2×2 tensor in TF 2.

***LISTING E.27: tf2_gradient_tape4.py***

```python
import tensorflow as tf
x = tf.ones((3, 3))
with tf.GradientTape() as t:
    t.watch(x)
    y = tf.reduce_sum(x)
    print("y:", y)
    z = tf.multiply(y, y)
    print("z:", z)
    z = tf.multiply(z, y)
    print("z:", z)
    # the derivative of z with respect to y
    dz_dy = t.gradient(z, y)
    print("dz_dy:", dz_dy)
```

In [Listing E.27](#appE.xhtml#listE.27), `y` equals the sum of the elements in the 3×3 tensor `x`, which is 9.

Next, `z` is assigned the term `y*y` and then multiplied again by `y`, so the final expression for `z` (and its derivative) is here:

z = y*y*y  
z' = 3*y*y  

When `z'` is evaluated with the value 9 for `y`, the result is 3*9*9, which equals 243. Launch the code in [Listing E.27](#appE.xhtml#listE.27) and you will see the following output (slightly reformatted for readability):

y: tf.Tensor(9.0, shape=(), dtype=float32)  
z: tf.Tensor(81.0, shape=(), dtype=float32)  
z: tf.Tensor(729.0, shape=(), dtype=float32)  
dz_dy: tf.Tensor(243.0, shape=(), dtype=float32)

### **A Persistent Gradient Tape**

[Listing E.28](#appE.xhtml#listE.28) displays the contents of `tf2_gradient_tape5.py` that illustrates how to define a persistent gradient tape in order to calculate the first derivative of a tensor in TF 2.

***LISTING E.28: tf2_gradient_tape5.py***

```python
import tensorflow as tf
x = tf.ones((3, 3))
with tf.GradientTape(persistent=True) as t:
    t.watch(x)
    y = tf.reduce_sum(x)
    print("y:", y)
    w = tf.multiply(y, y)
    print("w:", w)
    z = tf.multiply(y, y)
    print("z:", z)
    z = tf.multiply(z, y)
    print("z:", z)
    # the derivative of z with respect to y
    dz_dy = t.gradient(z, y)
    print("dz_dy:", dz_dy)
    dw_dy = t.gradient(w, y)
    print("dw_dy:", dw_dy)
```

[Listing E.28](#appE.xhtml#listE.28) is almost the same as [Listing E.27](#appE.xhtml#listE.27): the new sections are displayed in bold. Note that `w` is the term `y*y` and therefore the first derivative `w'` is `2*y`. Hence, the values for `w` and `w'` are 81 and 18, respectively, when they are evaluated with the value 9.0. Launch the code in [Listing E.28](#appE.xhtml#listE.28) and you will see the following output (slightly reformatted for readability), where the new output is shown in bold:

y: tf.Tensor(9.0, shape=(), dtype=float32)  
w: tf.Tensor(81.0, shape=(), dtype=float32)  
z: tf.Tensor(81.0, shape=(), dtype=float32)  
z: tf.Tensor(729.0, shape=(), dtype=float32)  
dz_dy: tf.Tensor(243.0, shape=(), dtype=float32)  
dw_dy: tf.Tensor(18.0, shape=(), dtype=float32)

## **What is Trax?**

Trax is a deep learning library (maintained by the Google Brain team) that “focuses on clear code and speed,” and the Trax documentation is here:

*[https://trax.readthedocs.io/en/latest/](https://trax.readthedocs.io/en/latest/)*

Trax is similar to Keras, and can handle resources such as Jax and TF-NumPy. Moreover, Trax models can be easily converted to Keras‑based models. The Trax code samples are available in this Github repository:

*[https://github.com/Sirsirious/trax_start/blob/colabs/TraxStart.ipynb](https://trax_start/blob/colabs/TraxStart.ipynb)*

In particular, the Trax repository provides code samples that implement the following:

* Seq2Seq models  
* Transformer models  
* BERT  
* Reformer (based on Transformer)  
