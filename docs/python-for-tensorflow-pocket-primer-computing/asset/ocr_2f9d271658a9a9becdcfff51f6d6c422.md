2 contains more information about "one hot" encoding, which you will encounter when you train neural networks.

# LISTING 5.20: tf-onehot2.py

```
import tensorflow as tf

# Generate one-hot array using idx
idx = tf.get_variable("idx",
initializer=tf.constant([2, 0, -1, 0])

target = tf.one_hot(idx, 3, 2, 0)

init = tf.global_variables_initializer()

with tf.Session() as sess:
sess.run(init)
print(sess.run(target))
```

Listing 5.20 starts by defining the variable idx that is initialized as a TF constant that is a one-dimensional TF tensor with four integer values. Notice that the second and third elements are equal, which means their one-hot encoding will be the same. The next portion of Listing 5.20 defines target, which will contain the one-hot encoded values for idx. Next, the code block initializes the TF variable idx and then prints the contents of target, which is a 4x3 tensor. The output from Listing 5.20 is:

```
[[0 0 2]
[2 0 0]
[0 0 0]
[2 0 0]]
```

# ARRAYS IN TENSORFLOW (1)