block that displays the values of the initialized values. The output from Listing 5.15 is here:

```
a: 2.7182817
b: 0.13533528
s1: 0.8807997
s2: 0.8807997
t2: 0.9640276
```

The next section contains a simple example of using a for loop in TF, followed by another example that uses a for loop in TF.

# USING FOR LOOPS IN TF

Listing 5.16 displays the contents of tf-forloop1.py illustrates how to use a for loop in a TF graph.

# LISTING 5.16: tf-forloop1.py

```
import tensorflow as tf

x = tf.Variable(0, name='x')

init = tf.global_variables_initializer()

with tf.Session() as session:
    session.run(init)
    for i in range(5):
        x = x + 1
        print(session.run(x))
```

Listing 5.16 initializes the TF variable x with the value 0 and then defines the model variable that is used for initializing the variables in this code sample (which is just the variable x). With this code block contains a loop that iterates through the values 1 through