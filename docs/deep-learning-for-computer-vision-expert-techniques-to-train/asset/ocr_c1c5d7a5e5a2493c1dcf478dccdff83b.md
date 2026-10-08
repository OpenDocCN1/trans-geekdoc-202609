# Getting Started

+   3. Next, define a constant with the string Hello, TensorFlow. This is different from the usual Python assignment operations as the value is not yet initialized:

```
```
>>> hello = tf.constant('Hello, TensorFlow!')
```
```

+   4. Create a session to initialize the computational graph, and give a name to the session:

```
```
>>> session = tf.Session()
```
```

The session can be run with the variable hello as the parameter.

+   5. Now the graph executes and returns that particular variable is printed:

```
```
>>> print(session.run(hello))
```
```

It should print the following:

Hello, TensorFlow!

Let us look at one example to understand how the session and graph work.

> Visit https://github.com/rajacheers/
DeepLearningForComputerVision to get the code for all the examples presented in the book. The code will be organised according to chapters. You can raise issues and get help in the repository.

# TensorFlow example for adding two numbers

Here is another simple example of how TensorFlow is used using the following code:

+   1. Create a Python file and import tensorflow using the following:

```
```
import tensorflow as tf
```
```

The preceding import will be necessary for all the latter examples. It is assumed that the reader has imported the library for all the examples. A placeholder can be defined in the following manner. The placeholders are not loaded when assigned. Here, a variable is defined as a placeholder with a type of float32. A placeholder is an empty declaration and can take values when a session is run.

+   2. Now we define a placeholder as shown in the following code:

```
```
x = tf.placeholder(tf.float32)
y = tf.placeholder(tf.float32)
```
```