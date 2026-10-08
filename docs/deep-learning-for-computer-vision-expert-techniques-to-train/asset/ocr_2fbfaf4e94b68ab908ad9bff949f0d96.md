# Similarity Learning

# Chapter 6

```
inputs=dense_layer_bottleneck,
rate=0.4,
training=dropout_bool
logits = dense_layer(dropout, no_classes)
```

```
with tf.name_scope('loss'):
    softmax_cross_entropy = tf.nn.softmax_cross_entropy_with_logits(
        labels=y_input, logits=logits)
    loss_operation = tf.reduce_mean(softmax_cross_entropy, name='loss')
    tf.summary.scalar('loss', loss_operation)
```

```
with tf.name_scope('optimiser'):
    optimizer = tf.train.AdamOptimizer().minimize(loss_operation)
```

```
with tf.name_scope('accuracy'):
    with tf.name_scope('correct_prediction'):
        predictions = tf.argmax(logits, 1)
        correct_predictions = tf.equal(predictions, tf.argmax(y_input))
    with tf.name_scope('accuracy'):
        accuracy_operation = tf.reduce_mean(
            tf.cast(correct_predictions, tf.float32))
    tf.summary.scalar('accuracy', accuracy_operation)
```

```
session = tf.Session()
session.run(tf.global_variables_initializer())
```

```
merged_summary_operation = tf.summary.merge_all()
train_summary_writer = tf.summary.FileWriter('/tmp/train', session.graph)
test_summary_writer = tf.summary.FileWriter('/tmp/test')
```

test_images, test_labels = mnist_data.test.images, mnist_data.test_labels

The data has be fed separately for left and right models as:

```
for batch_no in range(total_batches):
    mnist_batch = mnist_data.train.next_batch(batch_size)
    train_images, train_labels = mnist_batch[0], mnist_batch[1]
    merged_summary = session.run([optimiser, merged_summary_operation),
        feed_dict={
            left_input: train_images,
            right_input: train_images,
            y_input: train_labels,
            dropout_bool: True
        })
```

```
train_summary_writer.add_summary(merged_summary, batch_no)
if batch_no % 10 == 0:
    merged_summary, _ = session.run({merged_summary_operation,
```

[ 160 ]