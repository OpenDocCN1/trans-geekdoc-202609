However, if we introduce some kind of hidden state to the generative model we will obtain a new model that can store information inside the hidden state.

With all that in mind, let's switch back to the topic of recurrent neural networks. In essence they are perceptrons. However, keep in mind that perceptrons have specific states. Recurrent neural networks create connections between the passes and they are more powerful due to the combination of two features. First, they hold distributed hidden states and therefore they can store a lot more information that can be later passed forward. Secondly, the hidden state can be updated due to non-linear dynamics. In other words, as long as a recurrent neural network has plenty of time and a large enough number of neurons, it can calculate anything, provided the computer can handle it. This type of network is capable of a lot of things because it has the ability to implement a number of components that are each designed to contain some data. These components can then run and interact simultaneously in order to perform complex operations.

However, there is one downside when it comes to recurrent neural networks, namely the disappearing gradient problem. Over a long enough period of time information can eventually be lost. Take note that in this case the information refers to the weights, meaning that only the past information is lost, not the current neuron states. For instance, if a weight reaches a value of zero or a million, the previous state will be eliminated.

In conclusion, we can determine that recurrent neural networks are used in many fields because they essentially offer the ability to autocomplete missing information.

# Convolutional Neural Networks

Finally, we have the convolutional neural networks that appeared in the late 90s when a method was devised to recognize handwritten digits. This new concept relies on feedforward networks with backpropagation and a large number of hidden layers. These layers