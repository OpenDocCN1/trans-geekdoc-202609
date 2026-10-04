
A `GraphDef` stores a graph's data in a special format called a *protocol buffer,* also known as a *protobuf*. This may be generated in text or binary form, and in text form, it looks like the JavaScript Object Notation (JSON).

In a `GraphDef`, every tensor and operation is represented by a `node` element. Each `node` has a `name` field, an `op` field, and one or more `attr` fields. The following text presents the general structure of a `node` element:

```
node {
 name: "…"
 op: "…"
 attr { … }
 attr { … }
 …
}
```

The last element in a `GraphDef` is a `versions` element. This element identifies the version of the `GraphDef` structure.

The best way to understand `GraphDef`s is to look at an example. Suppose that an application contains the following code:

```
a = tf.constant(2.5)
b = tf.constant(4.2)
sum = a + b;
```

In text form, the content of the `GraphDef` is given as follows:

```
node {
 name: "Const"
 op: "Const"
 attr {
 key: "dtype"
 value { type: DT_FLOAT }
 }
 attr {
 key: "value"
 value {
 tensor {
 dtype: DT_FLOAT
 tensor_shape {}
 float_val: 2.5
 }
 }
 }
}
node {
 name: "Const_1"
 op: "Const"
 attr {
 key: "dtype"
 value { type: DT_FLOAT }
 }
 attr {
 key: "value"
 value {
 tensor {
 dtype: DT_FLOAT
 tensor_shape {}
 float_val: 4.2
 }
 }
 }
}
node {
 name: "add"
 op: "Add"
 input: "Const"
 input: "Const_1"
 attr {
 key: "T"
 value { type: DT_FLOAT }
 }
}
versions {
 producer: 22
}
```

This `GraphDef` has three nodes: two that represent tensors and one that represents the operation that adds the tensors. Real-world applications may have thousands of nodes. At the end of the list of nodes, the `versions` object identifies the version as `22`.

The `write_graph` function in `tf.train` makes it possible to store a `GraphDef`'s data to a file. Its signature is given as follows:

`write_graph(graph/graph_def, logdir, name, as_text=True)`

The first argument can be set to a `Graph` or `GraphDef`. The last argument identifies if the content should be written in text or binary form. For example, the following code stores the current graph to a text file named `graph.dat`:

```
tf.train.write_graph(tf.get_default_graph(), os.getcwd(), 'graph.dat')
```

Similarly, an application can load a `GraphDef` from a file containing graph data by calling one of two routines:

* `TextFormat.Merge(data, graphdef)`: Initializes a `GraphDef` from text elements
* Creating `GraphDef`s: Converting a graph into a protocol buffer

The `TextFormat` class is provided in `google.protobuf`. For a complete discussion of accessing protocol buffers in Python, visit [`https://developers.google.com/protocol-buffers/docs/pythontutorial`](https://developers.google.com/protocol-buffers/docs/pythontutorial).

# Creating and Running Sessions

As a Python developer, you're probably accustomed to having your programs processed line by line. But in a TensorFlow application, operations involving tensors aren't executed until they’re stored in a graph and executed in a session. This section explains how you can code applications that create and execute sessions.

## Creating sessions

As with graphs, only one session can be active at a time. But there’s an important difference between sessions and graphs — every session must be explicitly created. You can create a `Session` by calling `tf.Session`, which accepts three optional arguments:

* `target`: Name of the execution engine
* `graph`: The `Graph` instance to be launched
* `config`: A `ConfigProto` that configures the session's execution

A discussion of execution engines is in [Chapter 11](#17_9788126592555-ch11.xhtml), which introduces the `target` parameter. Similarly, most of the settings in a `ConfigProto` relate to threads and devices, so [Chapter 11](#17_9788126592555-ch11.xhtml) discusses the `config` parameter.

By default, a session accesses tensors and operations in the default graph. But if you set the `graph` parameter in `tf.Session`, the session will execute that graph instead.

Applications frequently call `tf.Session` inside a `with` statement. This statement ensures that code in the `with` block can access the new `Session`. The following code shows how this works:

```
with tf.Session() as sess:
 …
```

Most of the example applications presented in this book create sessions with similar code.

## Executing a session

The most important method of the `Session` class is `run`. This method accepts four arguments, and only the first is required:

* `fetches`: Identifies one or more operations or tensors to be executed
* `feed_dict`: Data to be fed into a tensor
* `options`: Configuration options for the session's execution
* `run_metadata`: Output data from the session

The `fetches` parameter accepts a wide range of data types. Most applications set this parameter equal to an operation, a tensor, or the name of an operation or tensor. You can also assign `fetches` to a list of tensors, operations, or names.

If you assign `fetches` to a tensor, `run` will return an `ndarray` with the same values and shape. The following code calls `run` with a two-element tensor:

```
tensr = tf.constant([2, 3])
with tf.Session() as sess:
 res = sess.run(tensr)
 print(res) # Prints [2, 3]
```

If you assign `fetches` to an `Operation`, `run` will return an `ndarray` containing the values of the tensor produced by the operation. The following code calls `run` with an operation that performs addition:

```
t1 = tf.constant(7)
t2 = tf.constant(2)
with tf.Session() as sess:
 res = sess.run(t1 + t2)
 print(res) # Prints 9
```

If you assign `fetches` to a collection of elements, `run` will return a similar collection containing the processed results. The following code calls `run` with a list containing two tensors:

```
t1 = tf.constant(9)
t2 = tf.constant(5)
with tf.Session() as sess:
 res1, res2 = sess.run([t1, t2])
 print(res1) # Prints 9
 print(res2) # Prints 5
```

The `feed_dict` parameter of `run` plays an important role in applications that process training data with batches. [Chapter 5](#09_9788126592555-ch05.xhtml) discusses this parameter in detail.

## Interactive sessions

Rather than send an entire script to an interpreter, many Python developers prefer to write code interactively. In this mode, the interpreter displays feedback as each line is processed.

To support interactive development, TensorFlow provides the `InteractiveSession` class. An `InteractiveSession` serves the same role as a `Session`, but it makes itself the default session when it's constructed.

Instead of calling `sess.run`, you can evaluate tensors by calling their `eval` method. Similarly, you can execute operations by calling the `run` method of the `Operation` class.

An example clarifies how `InteractiveSession`s work. The following code is intended to be run in normal mode:

```
t1 = tf.constant(1.2)
t2 = tf.constant(3.5)
prod = tf.multiply(t1, t2)
with tf.Session() as sess:
 print("Product: ", sess.run(prod))
```

This code accomplishes the same result with an `InteractiveSession`:

```
t1 = tf.constant(1.2)
t2 = tf.constant(3.5)
prod = tf.multiply(t1, t2)
sess = tf.InteractiveSession()
print("Product: ", prod.eval())
```

The `InteractiveSession` class constructor accepts the same arguments as that of the `Session` class. Similarly, its `run` method accepts the same arguments as the `run` method of the `Session` class.

# Writing Messages to the Log

All of the example code in [Chapters 1](#05_9788126592555-ch01.xhtml) through [4](#08_9788126592555-ch04.xhtml) has relied on `print` to write data to standard output. But TensorFlow provides a logging mechanism with many more messaging capabilities than regular `print`. There are five points to know about TensorFlow logging:

* TensorFlow enables logging through the `tf.logging` package.
