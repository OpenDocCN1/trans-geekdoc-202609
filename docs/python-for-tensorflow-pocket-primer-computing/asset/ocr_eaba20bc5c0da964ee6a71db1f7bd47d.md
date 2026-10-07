```
c = tf.multiply(a,b)

# initialize a and b:
feed_dict = {a:2, b:3}
```

```
# multiply a and b:
with tf.Session() as sess:
print(sess.run(c, feed_dict))
```

Listing 5.4 defines two TF placeholders a and b, followed by the TF variable c that is the product of a and b. The output of Listing 5.4 is 6, which is the product of the values assigned to the TF placeholders a and b.

There is another important detail about TF variables and how they are initialized in TensorFlow, which is the subject of the next section.

# CONSTANTS AND VARIABLES IN A TF SESSION

Listing 5.5 displays the contents of tf-variables-init.py that illustrates how to compute values involving TF placeholders in a with code block in TensorFlow.

# LISTING 5.5: tf-variables-init.py

```
import tensorflow as tf

x = tf.constant(5,name="x")
y = tf.constant(8,name="y")
z = tf.Variable(2*x+3*y, name="z")
```

```
init = tf.global_variables_initializer()

with tf.Session() as session:
session.run(init)
```