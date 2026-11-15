method for the output layer; that code is elsewhere in network3.py. But that code is short and simple, anyway. With all these things defined, the stage is set to define the train_mini_batch function, a Theano symbolic function which uses the updates to update the Network parameters, given a mini-batch index. Similarly, validate_mb_accuracy and test_mb_accuracy compute the accuracy of the Network on any given mini-batch of validation or test data. By averaging over these functions, we will be able to compute accuracies on the entire validation and test data sets.

The remainder of the SGD method is self-explanatory - we simply iterate over the epochs, repeatedly training the network on mini-batches of training data, and computing the validation and test accuracies.

Okay, we've now understood the most important pieces of code in network3.py. Let's take a brief look at the entire program. You don't need to read through this in detail, but you may enjoy glancing over it, and perhaps diving down into any pieces that strike your fancy. The best way to really understand it is, of course, by modifying it, adding extra features, or refactoring anything you think could be done more elegantly. After the code, there are some problems which contain a few starter suggestions for things to do. Here's the code*:

```
"""network3.py
~~~~~~~~~~~~~~~~

A Theano-based program for training and running simple neural networks.

Supports several layer types (fully connected, convolutional, max pooling, softmax), and activation functions (sigmoid, tanh, and rectified linear units, with more easily added).

When run on a CPU, this program is much faster than network.py and network2.py. However, unlike network.py and network2.py it can also be run on a GPU, which makes it faster still.

Because the code is based on Theano, the code is different in many ways from network.py and network2.py. However, where possible I have tried to maintain consistency with the earlier programs. In particular, the API is similar to network2.py. Note that I have focused on making the code simple, easily readable, and easily modifiable. It is not optimized, and omits many desirable features.

This program incorporates ideas from the Theano documentation on convolutional neural nets (notably, http://deeplearning.net/tutorial/lenet.html ), from Misha Denil's implementation of dropout (https://github.com/mdenil/dropout ), and from Chris Olah (http://colah.github.io ).

"""
```

> *Using Theano on a GPU can be a little tricky. In particular, it's easy to make the mistake of pulling data off the GPU, which can slow things down a lot. I've tried to avoid this, but wouldn't be surprised if this code can be sped up further. I'd appreciate hearing any tips for further improvement (mnn@michaielsen.org).