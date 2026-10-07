respectively. Due to the nested square brackets, m1 has shape 1x2, whereas m2 has shape 2x1. Hence, the product of m1 and m2 has shape (1,1).

The three print() statements display the value of m1, m2, and p1. The output from Listing 5.24 is here:

```
m1: [[3. 3.]]
m2: [[2.]]
[2.]]
p1: [[12.]]
```

# MULTIPLYING TWO ARAYS IN TF (GPU)

Listing 5.25 displays the contents of tf-gpu.py that illustrates how to define a TF array and access elements in that array.

# LISTING 5.25: tf-gpu.py

```
import tensorflow as tf

with tf.Session() as sess:
    with tf.device("/gpu:1"):

m1 = tf.constant([[3., 3.]]) # 1x2
m2 = tf.constant([[2.],[2.]]) # 2x1
p1 = tf.matmul(m1,m2)               # 1x1
print('m1:',sess.run(m1))
print('m2:',sess.run(m2))
print('p1:',sess.run(p1))
```

Listing 5.25 contains the same code as Listing 5.24, with the exception of the second with code statement (shown in bold) that specifies the GPU where the TensorFlow code will be executed.
Since the TensorFlow code is the same, the output is also the same.