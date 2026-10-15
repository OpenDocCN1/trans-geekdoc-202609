# Understanding Feedforward Networks

# Overview

Feedforward networks, often simply referred to as neural networks, form the backbone of many modern machine learning models. They are called "feedforward" because information travels through them in one direction: from the input layer, through any number of hidden layers, to the output layer. No information loops back within the network, which differentiates them from recurrent neural networks where such loops are allowed.

A basic feedforward network consists of at least three types of layers: an input layer, which receives the initial data; one or more hidden layers, where the actual processing is done via a system of weighted connections; and an output layer, which produces the final result. Each layer consists of multiple neurons (also called nodes), and each neuron in a layer is connected to all neurons in the previous and next layers. The "depth" of a neural network refers to the number of hidden layers it has.