```
B = tf.fill([2,3], 5.0)
```

```
with tf.Session() as sess:
    print('aconst:',sess.run(tf.rank(aconst)))
    print('rank B:',sess.run(tf.rank(B)))
```

Listing 5.8 contains the usual import statement, followed by the definition of the TF constant a. Next, the TF variable B is initialized as a 1x2 vector that is initialized with the value 5.0. Next, a with code block contains the code to display the values of aconst and the rank of B. The output from Listing 5.8 is here:

```
Tensor("Const:0", shape=(), dtype=float32)
aconst: 3.0
rank B: 2
```

# PLACEHOLDERS IN TENSORFLOW (REVISITED)

TensorFlow placeholders have the following features:

+   * they only allocate memory for future use
* they can have variable size
* used for inputting data "external" to graph
* good for unknown data size
* placeholders are from functions (not TF class instances)

The following examples of TensorFlow placeholders illustrate how to specify unconstrained shapes and higher-dimensional tensors:

```
a = tf.placeholder("float")
b = tf.placeholder(tf.int32, name='b')
c = tf.placeholder(tf.float32, shape=[3])
```

```
# Unconstrained shape:
w = tf.placeholder(tf.float32)
```