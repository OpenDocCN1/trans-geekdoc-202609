statement that enables us to enable eager execution (via the second statement in bold).

In addition, the definition of the TF variable is modified slightly to reference the Variable class in the tf.contrib.eager package instead of the tf package. The output from Listing 5.17 is here:

```
<tf.Variable 'x':0' shape=(), dtype=int32, numpy=0>
tf.Tensor(1, shape=(), dtype=int32)
tf.Tensor(2, shape=(), dtype=int32)
tf.Tensor(3, shape=(), dtype=int32)
tf.Tensor(4, shape=(), dtype=int32)
```

# USING WHILE LOOPS WITH EAGER EXECUTION IN TF

Listing 5.18 displays the contents of tf-while-eager2.py which illustrates how to use a for loop in a TF graph.

# LISTING 5.18: tf-while-eager2.py

```
import tensorflow as tf
import tensorflow.contrib.eager as tfe

tfe.enable_eager_execution()

a = tf.constant(12)

while not tf.equal(a, 1):
    if tf.equal(a % 2, 0):
        a = a / 2
    else:
        a = 3 * a + 1
print(a)
```