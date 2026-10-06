The output of the above code is:

Figure 8.

```
Tensor("Const:0", shape=(), dtype=float32)
Tensor("Const_1:0", shape=(), dtype=float32)
Tensor("add:0", shape=(), dtype=float32)
```

Note that the above tensors do not print the values 3.0, 4.0, and 7.0 that you might expect. It only builds the computational graph. A unique name is assigned to each operation in a graph. This name is independent of the names of the objects that are assigned to Python. Tensors are named after the operation that produces them followed by an output index, as in "add:0".

**Running the computational graph (using tf.Session):** In TensorFlow, everything has to be run within a session. We have to explicitly tell the program to run the command or object within the TensorFlow session. We can run the computational graph with the help of session runtime in two ways:

# Method 1

Figure 9.

```
import tensorflow as tf
hello_constant=tf.constant('Hello World')

#Run the session
with tf.Session() as sess:
output=(sess.run(hello_constant).decode())
print(output)
```

Hello World

# Method II

If we are specifying the session by this particular fashion, then we have to close the session at the end explicitly. If we are not closing the session, it may create a problem at runtime to provide the results.