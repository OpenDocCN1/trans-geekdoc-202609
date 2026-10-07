with tf.Session() as session:
result = session.run(y, feed_dict={x: [1, 2, 3])
print('y', result)

Listing 5.9 defines the TF placeholder x as a float data type, followed by the variable y is twice the value of x. The with code block calculates the value of y by specifying an array of values for feed_dict. If you expected merely a scalar value for x, this example illustrates the fact that a TF placeholder can take whatever shape is required (i.e., not just a scalar value). The output from Listing 5.9 is here:

('y':array([2., 4., 6.], dtype=float(32)))

Listing 5.10 displays the contents of tf-feeddict-values2.py that illustrates how to use feed_dict to supply values to a placeholder.

# LISTING 5.10: tf-feeddict-values2.py

```
import tensorflow as tf

x = tf.placeholder("float", [None, 3])
y = x * 2
z = x ** 3

with tf.Session() as session:
x_data = [[1, 2, 3],
          [4, 5, 6]]

result1 = session.run(y, feed_dict={x: x_data})
print('y',result1.eval())

result2 = session.run(z, feed_dict={x: x_data})
print('z',result2.eval())
```