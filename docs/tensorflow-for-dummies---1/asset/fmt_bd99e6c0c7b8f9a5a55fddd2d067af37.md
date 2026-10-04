
`img_tensor = tf.image.convert_image_dtype(img_tensor, tf.float32)`

# Remove noise using a box filter

```
conv_filter = np.zeros([3, 3, 1, 1])
conv_filter[0, 0, :, :] = 0.1111
conv_filter[0, 1, :, :] = 0.1111
conv_filter[0, 2, :, :] = 0.1111
conv_filter[1, 0, :, :] = 0.1111
conv_filter[1, 1, :, :] = 0.1111
conv_filter[1, 2, :, :] = 0.1111
conv_filter[2, 0, :, :] = 0.1111
conv_filter[2, 1, :, :] = 0.1111
conv_filter[2, 2, :, :] = 0.1111
img_tensor = tf.nn.conv2d(img_tensor, conv_filter, [1, 1, 1, 1], 'SAME')
```

# Increase contrast

```
img_tensor = tf.reshape(img_tensor, [232, 706, 1])
img_tensor = tf.image.adjust_contrast(img_tensor, 0.8)
```

# Flip horizontal

```
img_tensor = tf.image.flip_left_right(img_tensor)
```

# Create summary data and FileWriter

```
img_tensor = tf.reshape(img_tensor, [1, 232, 706, 1])
img_tensor = tf.image.convert_image_dtype(img_tensor, tf.uint8)
summary_op = tf.summary.image('Output', img_tensor)
file_writer = tf.summary.FileWriter('log')
```

# Store result to PNG

```
img_tensor = tf.reshape(img_tensor, [232, 706, 1])
img_tensor = tf.image.encode_png(img_tensor)
with tf.Session() as sess:
    coord = tf.train.Coordinator()
    threads = tf.train.start_queue_runners(coord=coord)
    
    # Execute session
    output_data, summary = sess.run([img_tensor, summary_op])
    
    # Write output PNG data to file
    output_file = open('output_aircraft.png', 'wb+')
    output_file.write(output_data)
    output_file.close()
    
    # Print summary data
    file_writer.add_summary(summary)
    file_writer.flush()
    
    # Wait for threads to terminate
    coord.request_stop()
    coord.join(threads)
```

As you look at this code, it’s important to keep track of the image’s shape and data type. After the application decodes the input image, the tensor’s shape is `[232, 706, 1]`, and its elements are 8-bit unsigned integers. But before the convolution can be performed, the application converts the tensor’s shape to `[1, 232, 706, 1]` and its elements to 32-bit floating-point values.

Before it can update the image’s contrast, the application converts the image tensor’s shape back to `[232, 706, 1]`. Later on, the module converts the image’s shape to `[1, 232, 706, 1]` and its type to `tf.uint8` so that the module can generate summary data. Lastly, the application converts the tensor’s shape to `[232, 706, 1]` so that it can encode the data to PNG format.

The process of generating summary data for an image is similar to that of generating data for a tensor. The only difference is that the application needs to call `tf.summary.image` instead of `tf.summary.scalar` or `tf.summary.histogram`. The function's signature is given as follows:

`tf.summary.image(name, tensor, max_outputs=3, collections=None, family=None)`

The `name` parameter provides the label that TensorFlow will associate with the image. The function accepts the image data through the `tensor` parameter, and the tensor's shape must be `[batch_size, height, width, num_channels]`.

As an example, the `ch8/img_proc.py` module creates an operation that generates summary data for `img_tensor` with the following code:

`summary_op = tf.summary.image('Output', img_tensor)`

After creating this operation, the application executes it in a session and uses a `FileWriter` to print the protocol buffer to an event file. When launched, TensorBoard will read this event file and display the graphical content of `img_tensor`.

# Chapter 9

# Analyzing Sequential Data with Recurrent Neural Networks (RNNs)

IN THIS CHAPTER

![check](images/check.png)**Analyzing sequential data with Recurrent Neural Networks (RNNs)**

![check](images/check.png)**Improving performance with Long Short-Term Memory (LSTM)**

![check](images/check.png)**Improving performance further with Gated Recurrent Units (GRUs)**

Suppose that you want a neural network to predict the next word in the phrase “My hovercraft is full of….” As any Monty Python fan (or a casual web search) will tell you, the obvious answer is “eels.” But how can you train a neural network to arrive at the answer?

You can feed the network every sentence ever written on the Internet, but there’s still a problem. To make the prediction, the neural network needs to recognize that the words form an *ordered sequence*. That is, the network needs to understand that the phrase “My hovercraft is full of” is a different phrase than “full is My of hovercraft.”

None of the neural networks discussed in [Chapters 1](#05_9788126592555-ch01.xhtml) through [8](#13_9788126592555-ch08.xhtml) of this book are capable of recognizing sequences. As a consequence, they can't use past analysis to solve future problems. For example, a CNN can classify an image, but it can't classify later images based on previous classifications. To make up for these shortcomings, machine learning researchers invented recurrent neural networks, or RNNs.

## Recurrent Neural Networks (RNNs)

Most neural networks, such as convolutional neural networks, transfer data in one direction: from the input layer to the output layer. For this reason, they’re called *feed-forward* networks. In contrast with feed-forward networks, recurrent neutral networks, or RNNs, make use of *feedback*. That is, they send data from a later node to an earlier node in the network.

[Figure 9-1](#14_9788126592555-ch09.xhtml#c09-fig-0001) depicts a simple RNN. The overall structure resembles that of a regular network, but the result of the output node is delayed and fed back into the output node. This feedback is the primary characteristic that distinguishes RNNs from other neural networks.

![FIGURE 9-1: A recursive neural network feeds past data back into one or more nodes.](images/9788126592555-fg0901.png)

[FIGURE 9-1:](#14_9788126592555-ch09.xhtml#rc09-fig-0001) A recursive neural network feeds past data back into one or more nodes.

Another important characteristic of RNNs is that they execute in *stages*. For example, if an RNN needs to parse words in audio or text, it will execute one stage for each word. With each stage, the RNN receives new data to process. It’s important to see the difference between training steps and stages: One training step may require multiple processing stages.

In [Figure 9-1](#14_9788126592555-ch09.xhtml#c09-fig-0001), the network’s stage is identified by t. This doesn’t measure clock time, as in 1.37 seconds, but measures discrete time, which starts at 0 and increments by 1 with each new stage. Therefore, the initial input values are denoted x[i](0), the next set of inputs are denoted x[i](1), and so on.

An RNN makes use of previous processing stages by accessing delayed values. In [Figure 9-1](#14_9788126592555-ch09.xhtml#c09-fig-0001), delayed values are provided by the Delay element. If the current stage is 4, the value leaving the Delay element will be y(3). If the current stage is 5, the value leaving the element will be y(4).

Just as the network’s values change from stage to stage, their associated weights also change. For example, if the RNN in [Figure 9-1](#14_9788126592555-ch09.xhtml#c09-fig-0001) has N stages, the application needs to compute a different set of weights for y(0) through y(N-1). If an RNN has many delayed values, computing the weight of each value can dramatically increase the time needed for training.

### RNNs and recursive functions

To better understand how RNNs work, it helps to see how they relate to recursive functions. For example, the following function computes the factorial of N using recursion:

```
def factorial(N):
    if n == 1:
        return 1
    else:
        return N * factorial(N-1)
```

This function calls itself repeatedly and provides a new input value with each call. Recursive functions can be rewritten using loops, as demonstrated in the following function:

```
def factorial(N):
    x = 1
    for i in range(2, N+1):
        x *= i
    return x
```
