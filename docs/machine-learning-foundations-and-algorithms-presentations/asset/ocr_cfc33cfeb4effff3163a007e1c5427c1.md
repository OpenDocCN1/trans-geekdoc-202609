# Feedforward Neural Networks

+   * Each layer connects $N$ input units to $M$ output units.
* In the simplest case, all input units are connected to all output units. We call this a **fully connected layer**.
* **Note**: the inputs and outputs for a layer are distinct from the inputs and outputs to the network.

+   * I.e., each layer has a M x N weight matrix **W**
* Equation in matrix form:

$$\mathbf{y} = \phi(\mathbf{Wx} + \mathbf{b})$$\ 

* Output units are a function of input units
* Feedforward neural networks are also often called **multi-layer perceptrons** (MLPs)

![](bbox=[0.606, 0.517, 0.893, 0.883])