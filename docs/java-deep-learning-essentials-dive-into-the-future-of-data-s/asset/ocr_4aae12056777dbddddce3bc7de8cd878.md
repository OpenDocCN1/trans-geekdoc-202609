```
return y

def loss(y, label_placeholder):
    with tf.name_scope('loss') as scope:
        cross_entropy = - tf.reduce_sum(label_placeholder *
        tf.log(y))

        tf.scalar_summary("Cross Entropy", cross_entropy)

    return cross_entropy

def training(loss):
    with tf.name_scope('training') as scope:
        train_step =
        tf.train.GradientDescentOptimizer(0.01).minimize(loss)

    return train_step
```

tf.scalar_summary() in loss() makes the variable show up in the EVENTS menu. To enable visualization, we need the following code:

```
summary_step = tf.merge_all_summaries()
init = tf.initialize_all_variables()

summary_writer = tf.train.SummaryWriter('data',
graph_def=sess.graph_def)
```

Then the process of variables can be added with the following code:

```
summary = sess.run(summary_step, feed_dict=feed_dict)
summary_writer.add_summary(summary, i)
```

This feature of visualization will be much more useful when we're using more complicated models.

# Caffe

Caffe is a library famous for its speed. The official project page is http://caffe.berkeleyvision.org/ and the GitHub page is https://github.com/BVLC/caffe. Similar to TensorFlow, Caffe has been developed mainly with C++, but it provides a Python and MATLAB API. In addition, what is unique to Caffe is that you don't need any programming experience, you just write the configuration or protocol files, that is .prototxt files, to perform experiments and research with deep learning. Here, we focus on the protocol-based approach.