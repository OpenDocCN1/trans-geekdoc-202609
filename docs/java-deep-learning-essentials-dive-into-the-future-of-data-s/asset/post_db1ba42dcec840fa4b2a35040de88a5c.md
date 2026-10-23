
## Other Important Deep Learning Libraries

First, what we have to consider is fetching the MNIST data. Thankfully, TensorFlow also provides the code to fetch the data in `https://github.com/tensorflow/tensorflow/blob/master/tensorflow/examples/tutorials/mnist/input_data.py` and we put the code into the same directory. Then, by writing the following code, you can import the MNIST data:

```python
import input_data
```

MNIST data can be imported using the following code:

```python
mnist = input_data.read_data_sets("MNIST_data/", one_hot=True)
```

Similar to Theano, we define the variable with no actual values as the placeholder:

```python
x_placeholder = tf.placeholder("float", [None, 784])
label_placeholder = tf.placeholder("float", [None, 10])
```

Here, 784 is the number of units in the input layer and 10 is the number in the output layer. We do this because the values in the placeholder change in accordance with the mini-batches. Once you define the placeholder you can move on to the model building and training. We set the non-linear activation with the `softmax` function in `inference()` here:

```python
def inference(x_placeholder):

    W = tf.Variable(tf.zeros([784, 10]))
    b = tf.Variable(tf.zeros([10]))

    y = tf.nn.softmax(tf.matmul(x_placeholder, W) + b)

    return y
```

Here, W and b are the parameters of the model. The loss function, that is, the `cross_entropy` function, is defined in `loss()` as follows:

```python
def loss(y, label_placeholder):

    cross_entropy = - tf.reduce_sum(label_placeholder * tf.log(y))

    return cross_entropy
```

With the definition of `inference()` and `loss()`, we can train the model by writing the following code:

```python
def training(loss):
    train_step = tf.train.GradientDescentOptimizer(0.01).minimize(loss)

    return train_step
```

GradientDescentOptimizer() applies the gradient descent algorithm. But be careful, as this method just defines the method of training and the actual training has not yet been executed. TensorFlow also supports AdagradOptimizer(), MomentumOptimizer(), and other major optimizing algorithms.

The code and methods explained previously are to define the model. To execute the actual training, you need to initialize a session of TensorFlow:

```python
init = tf.initialize_all_variables()
sess.run(init)
```

Then we train the model with mini-batches. All the data in a mini-batch is stored in `feed_dict` and then used in `sess.run()`:

```python
for i in range(1000):
    batch_xs, batch_ys = mnist.train.next_batch(100)
    feed_dict = {x_placeholder: batch_xs, label_placeholder: batch_ys}

    sess.run(train_step, feed_dict=feed_dict)
```

That's it for the model training. It's very simple, isn't it? You can show the result by writing the following code:

```python
def res(y, label_placeholder, feed_dict):
    correct_prediction = tf.equal(
        tf.argmax(y, 1), tf.argmax(label_placeholder, 1)
    )

    accuracy = tf.reduce_mean(
        tf.cast(correct_prediction, "float")
    )

    print sess.run(accuracy, feed_dict=feed_dict)
```

TensorFlow makes it super easy to implement deep learning and it is very useful. Furthermore, TensorFlow has another powerful feature, TensorBoard, to visualize deep learning. By adding a few lines of code to the previous code snippet, we can use this useful feature.

Let's see how the model is visualized first. The code is in `DLW/src/resources/tensorflow/1_3_mnist_TensorBoard.py`, so simply run it. After you run the program, type the following command:

```bash
$ tensorboard --logdir=<ABSOLUTE_PATH>/data
```

Here, `<ABSOLUTE_PATH>` is the absolute path of the program. Then, if you access `http://localhost:6006/` in your browser, you can see the following page:

![](img/9315e45972ec0fbaf15f9144035bca79_231_0.png)

This shows the process of the value of `cross_entropy`. Also, when you click **GRAPH** in the header menu, you see the visualization of the model:

![](img/9315e45972ec0fbaf15f9144035bca79_231_1.png)

When you click on **inference** on the page, you can see the model structure:

![](img/9315e45972ec0fbaf15f9144035bca79_232_0.png)

Now let's look inside the code. To enable visualization, you need to wrap the whole area with the scope: `with tf.Graph().as_default()`. By adding this scope, all the variables declared in the scope will be displayed in the graph. The displayed name can be set by including the name label as follows:

```python
x_placeholder = tf.placeholder("float", [None, 784], name="input")
label_placeholder = tf.placeholder("float", [None, 10], name="label")
```

Defining other scopes will create nodes in the graph and this is where the definitions of `inference()`, `loss()`, and `training()` reveal their real values. You can define the respective scope without losing any readability:

```python
def inference(x_placeholder):
    with tf.name_scope('inference') as scope:
        W = tf.Variable(tf.zeros([784, 10]), name="W")
        b = tf.Variable(tf.zeros([10]), name="b")

        y = tf.nn.softmax(tf.matmul(x_placeholder, W) + b)

    return y

def loss(y, label_placeholder):
    with tf.name_scope('loss') as scope:
        cross_entropy = - tf.reduce_sum(label_placeholder * tf.log(y))

        tf.scalar_summary("Cross Entropy", cross_entropy)

    return cross_entropy

def training(loss):
    with tf.name_scope('training') as scope:
        train_step = tf.train.GradientDescentOptimizer(0.01).minimize(loss)

    return train_step
```

tf.scalar_summary() in loss() makes the variable show up in the EVENTS menu. To enable visualization, we need the following code:

```python
summary_step = tf.merge_all_summaries()
init = tf.initialize_all_variables()

summary_writer = tf.train.SummaryWriter('data', graph_def=sess.graph_def)
```

Then the process of variables can be added with the following code:

```python
summary = sess.run(summary_step, feed_dict=feed_dict)
summary_writer.add_summary(summary, i)
```

This feature of visualization will be much more useful when we're using more complicated models.

### Caffe

Caffe is a library famous for its speed. The official project page is http://caffe.berkeleyvision.org/ and the GitHub page is https://github.com/BVLC/caffe. Similar to TensorFlow, Caffe has been developed mainly with C++, but it provides a Python and MATLAB API. In addition, what is unique to Caffe is that you don't need any programming experience, you just write the configuration or protocol files, that is `.prototxt` files, to perform experiments and research with deep learning. Here, we focus on the protocol-based approach.

Caffe is a very powerful library that enables quick model building, training, and testing; however, it's a bit difficult to install the library to get a lot of benefits from it. As you can see from the installation guide at http://caffe.berkeleyvision.org/installation.html, you need to install the following in advance:

- CUDA
- BLAS (ATLAS, MKL, or OpenBLAS)
- OpenCV
- Boost
- Others: snappy, leveldb, gflags, glog, szip, lmdb, protobuf, and hdf5

Then, clone the repository from the GitHub page and create the `Makefile.config` file from `Makefile.config.example`. You may need Anaconda, a Python distribution, beforehand to run the make command. You can download this from https://www.continuum.io/downloads. After you run the `make`, `make test`, and `make runtest` commands (you may want to run the commands with a `-jN` option such as `make -j4` or `make -j8` to speed up the process) and pass the test, you'll see the power of Caffe. So, let's look at an example. Go to `$CAFFE_ROOT`, the path where you cloned the repository, and type the following commands:

```bash
$ ./data/mnist/get_mnist.sh
$ ./examples/mnist/train_lenet.sh
```

That's all you need to solve the standard MNIST classification problem with CNN. So, what happened here? When you have a look at `train_lenet.sh`, you will see the following:

```sh
#!/usr/bin/env sh

./build/tools/caffe train --solver=examples/mnist/lenet_solver.prototxt
```
