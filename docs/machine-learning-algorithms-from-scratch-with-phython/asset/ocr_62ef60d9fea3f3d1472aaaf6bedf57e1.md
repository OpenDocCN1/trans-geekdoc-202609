# Transfer Derivative

Given an output value from a neuron, we need to calculate it’s slope. We are using the sigmoid transfer function, the derivative of which can be calculated as follows:

$$derivative = output \times (1.0 - output)$$  (15.3)

Below is a function named `transfer_derivative()` that implements this equation.

```
```python
# Calculate the derivative of a neuron output
def transfer_derivative(output):
    return output * (1.0 - output)
```
```

Listing 15.9: Function To Calculate the Derivative of a Neuron’s Output.

Now, let’s see how this can be used.

# Error Backpropagation

The first step is to calculate the error for each output neuron; this will give us our error signal (input) to propagate backwards through the network. The error for a given neuron can be calculated as follows:

$$error = (expected - output) \times transfer\_derivative(output)$$  (15.4)

Where expected is the expected output value for the neuron, output is the output value for the neuron and `transfer_derivative()` calculates the slope of the neuron’s output value, as shown above. This error calculation is used for neurons in the output layer. The expected value is the class value itself. In the hidden layer, things are a little more complicated.

The error signal for a neuron in the hidden layer is calculated as the weighted error of each neuron in the output layer. Think of the error traveling back along the weights of the output layer to the neurons in the hidden layer. The backpropagated error signal is accumulated and then used to determine the error for the neuron in the hidden layer, as follows:

$$error = (weight_k \times error_j) \times transfer\_derivative(output)$$  (15.5)

Where `error_j` is the error signal from the jth neuron in the output layer, `weight_k` is the weight that connects the kth neuron to the current neuron and output is the output for the current neuron. Below is a function named `backward_propagate_error()` that implements this procedure.

You can see that the error signal calculated for each neuron is stored with the name `delta`. You can see that the layers of the network are iterated in reverse order, starting at the output and working backwards. This ensures that the neurons in the output layer have delta values calculated first that neurons in the hidden layer can use in the subsequent iteration. I chose the name delta to reflect the change the error implies on the neuron (e.g. the weight delta).

You can see that the error signal for neurons in the hidden layer is accumulated from neurons in the output layer where the hidden neuron number j is also the index of the neuron’s weight in the output layer `neuron['weights'][j]`.

```
```python
# Backpropagate error and store in neurons
def backward_propagate_error(network, expected):
    for i in reversed(range(len(network))):
```
```