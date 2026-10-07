Here we've got a recurrent neural network. With unraveled temporal loop.

![](bbox=[0.503, 0.028, 0.882, 0.193])

This is what it looks like if you dig inside the RNN. The images are taken from Christopher Olah.

![](bbox=[0.095, 0.246, 0.882, 0.497])

Here is his blog Very well-written blog with amazing images.

# Understanding LSTM Networks
Posted on August 27, 2015



Traditional neural networks can't do this, and it seems like a major shortcoming. For example,
imagine you are trying to predict the next word in a sentence. A traditional neural network could have no reasoning about previous events in
the past.

Recurrent neural networks address this issue. They are networks with loops, allowing
information to persist.

![](bbox=[0.197, 0.743, 0.407, 0.803])

struggle to away
All recurrent neural networks have the form of a chain of repeating modules of neural network.
in standard RNN, this module will have a very simple structure, like a single layer.

![](bbox=[0.557, 0.597, 0.837, 0.683])

The repeating module in a standard RNN contains a single layer.
LSTM is a more complex type of recurrent neural network with four interacting layers
instead of a single layer, these four interact in a very special way.

![](bbox=[0.557, 0.743, 0.837, 0.803])

The repeating module in an LSTM contains four interacting layers.
Don't worry about the details of what goes on. We will walk through the LSTM diagram later.

# 2.2.2 RNN vs LSTM-RNN

In following images the first one represents the Simple RNN and 2nd image represents "RNN with LSTM". Here LSTM is a special kind of network applied to RNN.