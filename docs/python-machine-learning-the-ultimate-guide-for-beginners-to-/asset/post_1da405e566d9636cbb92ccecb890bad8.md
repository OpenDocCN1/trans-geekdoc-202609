
times we perform it. This way we will always be able to recreate the dataset if needed. Now let's apply the decision tree classifier:

```
dtc = DecisionTreeClassifier()
dtc.fit(train_inputs, train_classes)
dtc.score(test_inputs, test_classes)
```

The result should look something like this:

0.95555555

We have managed to obtain 95% accuracy, which is quite an excellent result considering that we haven't performed any cleaning and we decided to ignore the outliers. This is why decision trees are so powerful and therefore popular in training various models. You can achieve high accuracy without performing too many operations.

## Chapter 6: Machine Learning & Neural Networks

Neural networks started appearing in the 50s as a new technique to create computer systems that seek to mimic the human learning process. Keep in mind that there is very little connection between a human neural network and an artificial one. Unfortunately, the human brain is still too complex to turn into an artificial version. However, the name of the machine learning technique is mostly used for inspiration.

Neural network neurons have nodes, which actually are a form of processing code that is meant to execute repeatedly until a solution to a problem is found. When the solution is known, then the result is sent to the next node within the same layer. When all the nodes within a layer have finished processing, the final one will communicate the result to the first node in the next layer. The human neural network does pose a number of similarities, however, it is also capable of establishing real time communication between all the nodes in every single layer at the same time. This is what makes the human brain truly special and powerful and why it cannot yet be replicated. The concept behind it is known as parallel processing. In artificial neural networks processing is linear, going from one node to the next.

A neural network isn't a particular machine learning algorithm. Instead, it is a subfield within machine learning, which contains certain systems that attempt to emulate some aspects of human thought processing. Neural networks transmit information through a network of nodes. Once the information is analyzed and classified, it is communicated to the neighboring node. Once there, another round of analysis and classification will take place and the cycle repeats itself. Take note that neural networks consist of a number of layers. The usual structure contains an input layer and an output layer. The most basic form of a neural network can even have only one layer, however, that is a fairly primitive model that is never used in practice. In addition, between the two layers we have a number of hidden layers, anywhere from none to as many as you need. These layers are the ones that handle the data that is sent from the input layer. Keep in mind that a standard network contains three layers, while those that have hundreds of layers are referred to as Deep Learning systems.

In this chapter we will focus on the classic feedforward neural network, as well as the recurrent neural network.

## Feedforward Neural Networks

This is the most basic type of neural network. Data is transmitted in a linear fashion and it can only go in one direction. It is passed from the input layer to the hidden layer and finally to the output layer. That's it. This type of network doesn't even iterate over the data like the more modern systems. Once the process is over, it's over. Data doesn't loop through a cycle. Once the operation is complete, we have the result. However, there are two types of feedforward networks.

The first is known as the single layer perceptron and this is as basic as it gets. There is only one layer and the data is passed in a linear fashion from the first node to the last. When the input passes through one node it is weighted and if the next node determines the weight passes a minimal limit, it will either be activated or deactivated.

The multi-layer perceptron, on the other hand, needs to have at least two layers, though in reality it consists of more than two. The data transmission is still linear, however the output of a previous layer becomes the input of the current layer. Take note that when there are more than two layers involved, this type of neural network will usually make use of the concept of backpropagation. This means that the actual output will be compared to the output that was expected. The difference between the two is then calculated and the degree of error is established. This error value is then sent throughout the neural net in order to adjust it as it passes through all of the nodes again. These adjustments will lead to a closer result, and the process is then repeated until the result matches as accurately as possible. Keep in mind that depending on how many layers there are, a large number of iterations may take place in order to establish a satisfactory state. Furthermore, multi-layer perceptrons that take advantage of backpropagation cannot be called true feedforward neural networks anymore. They become multi-layer networks that can be some of the most powerful and versatile algorithms in the entire field of Machine Learning.

## Recurrent Neural Networks

In order to understand recurrent neural networks you first need to understand the concept of sequence modeling. Keep in mind that machine learning is often applied to sequences and when we do so we often change the input sequence to the output sequence. For instance, you might want to convert the sequence of various sound pressures into a sequence of words. This means that when we don't have a specific target sequence, we can attempt to predict the next word in the input sequence by using a teaching signal. Then the output sequence becomes the input sequence with an additional step. This is a fairly natural process, and it makes a lot of sense in this case. However, it could be problematic when applying the same principle to an image. Imagine predicting a section of a picture by using another section which you already know. Predicting a simple term will make use of both supervised and unsupervised machine learning and therefore eliminate any barriers between them. What's special though, is the fact that both types of techniques can be used, but without requiring two different teaching signals.

Models that are considered without memory are best suited for this task. To be more precise, it's the autoregressive models we are referring to because they can predict the next word based on the previous known words by using what's known as delay taps. Feedforward neural networks that have at least one layer with hidden units are in general considered to be autoregressive. However, if we introduce some kind of hidden state to the generative model we will obtain a new model that can store information inside the hidden state.

With all that in mind, let's switch back to the topic of recurrent neural networks. In essence they are perceptrons. However, keep in mind that perceptrons have specific states. Recurrent neural networks create connections between the passes and they are more powerful due to the combination of two features. First, they hold distributed hidden states and therefore they can store a lot more information that can be later passed forward. Secondly, the hidden state can be updated due to non-linear dynamics. In other words, as long as a recurrent neural network has plenty of time and a large enough number of neurons, it can calculate anything, provided the computer can handle it. This type of network is capable of a lot of things because it has the ability to implement a number of components that are each designed to contain some data. These components can then run and interact simultaneously in order to perform complex operations.

However, there is one downside when it comes to recurrent neural networks, namely the disappearing gradient problem. Over a long enough period of time information can eventually be lost. Take note that in this case the information refers to the weights, meaning that only the past information is lost, not the current neuron states. For instance, if a weight reaches a value of zero or a million, the previous state will be eliminated.

In conclusion, we can determine that recurrent neural networks are used in many fields because they essentially offer the ability to autocomplete missing information.

## Convolutional Neural Networks

Finally, we have the convolutional neural networks that appeared in the late 90s when a method was devised to recognize handwritten digits. This new concept relies on feedforward networks with backpropagation and a large number of hidden layers. These layers
