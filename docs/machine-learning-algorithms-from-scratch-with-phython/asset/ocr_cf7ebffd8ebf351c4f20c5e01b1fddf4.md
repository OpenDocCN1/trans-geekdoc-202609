Now that we know how to create and initialized a network, let's see how we can use it to calculate an output.

# ## 15.2.2 Forward-Propagate

We can calculate an output from a neural network by propagating an input signal through each layer until the output layer outputs its values. We call this forward-propagation. It is the technique we will need to generate predictions during training that will need to be corrected, and it is the method we will need after the network is trained to make predictions on new data. We can break forward-propagation down into three parts:

+   1. Neuron Activation.
+   2. Neuron Transfer.
+   3. Forward-Propagation.

# ### Neuron Activation

The first step is to calculate the activation of one neuron given an input. The input could be a row from our training dataset, as in the case of the hidden layer. It may also be the outputs from each neuron in the hidden layer, in the case of the output layer. Neuron activation is calculated as the weighted sum of the inputs. Much like linear regression.

\(activation = bias + \sum_{i=1}^{n} weight_i \times input_i \quad (15.1)\)

Where `weight` is a network weight, `input` is an input value, i is the index of a weight or an input and `bias` is a special weight that has no input to multiply with (or you can think of the input as always being 1.0). Below is an implementation of this in a function named `activate()`. You can see that the function assumes that the bias is the last weight in the list of weights. This helps here and later to make the code easier to read.

```
# Calculate neuron activation for an input
def activate(weights, inputs):
    activation = weights[-1]
    for i in range(len(weights)-1):
        activation += weights[i] * inputs[i]
    return activation
```

Listing 15.4: Function To Activate a Neuron.

Now, let's see how to use the neuron activation.

# ### Neuron Transfer

Once a neuron is activated, we need to transfer the activation to see what the neuron output actually is. Different transfer functions can be used. It is traditional to use the sigmoid activation function, but you can also use the tanh (hyperbolic tangent) function to transfer outputs. More recently, the rectifier transfer function has been popular with large deep learning networks.