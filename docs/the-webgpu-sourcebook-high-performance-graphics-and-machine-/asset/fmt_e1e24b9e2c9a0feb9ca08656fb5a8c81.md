
A layer is *dense* or *fully-connected* if each of its nodes is connected to each node in the following layer. In [Figure 9.10](#chapter9.xhtml#fig9_10), every layer in the network is dense.
The nodes in a hidden layer are denoted `h^x[y]`, where `x` is the index of the layer and `y` is the index of the node in the layer. For example, `h²[1]` identifies the second node (1) in the third (2) layer.
The output of each node is computed by summing the weighted inputs and passing the sum into the activation function. For simplicity, we'll refer to a node's output using the node's name. For example, if the activation function of Node `h²[1]` is `ReLU`, its output is obtained by passing the sum of its weighted inputs into the `ReLU` function. This can be expressed with the following equation:
`h[1]² = ReLU(w[01]¹h[0]¹ + w[11]¹h[1]¹ + w[21]¹h[2]¹)`
As illustrated, each weight is identified by three indexes. Denoting a weight as `w^x[yz]`, its position can be determined as follows:
* `x` identifies the layer containing the node producing the weighted signal
* `y` identifies the index of the node producing the signal to be weighted
* `z` identifies the index of the node receiving the signal
For example, `w²[01]` identifies a weight in the third layer (Layer 2). The network multiplies the weight by the signal leaving the first node (0) and entering the second node (1).

## Deep Learning
As more hidden layers are added, the network becomes more capable of sophisticated detection and classification. When an application uses a neural network with multiple hidden layers, we say that it's making use of *deep learning*.
Deep learning has proven effective in many applications. Two famous examples include Google's AlphaGo program, which uses deep learning to beat professional Go players, and self-driving cars, which use neural networks to stay on the road and avoid traffic collisions.
But there are two major drawbacks to adding more layers to a network. First, each hidden layer increases the amount of time needed to train the network. Second, each new layer increases the chances of *overfitting*, which means the network is good at classification/prediction in particular cases but it doesn't work well with general data.

## Training
At this point, you should have a basic understanding of nodes, weights, and activation functions. But one critical aspect of neural networks has yet to be discussed: *training*. The goal of training is to update the weights so that the output nodes produce suitable results. These results could be prediction (What will tomorrow's average temperature be?) or classification (Does this image display a cat or a dog?)
To understand training, it helps to think of a neural network as a multi-stage mathematical function involving weighted inputs. Consider the network depicted in [Figure 9.11](#chapter9.xhtml#fig9_11).
![Figure 9.11 Example neural network.](images/fig9_11.jpg)
[Figure 9.11](#chapter9.xhtml#b9fig9_11) Example neural network.
Denoting the activation functions as `f[0]`, `f[1]`, and `f[2]`, the neural network in the illustration embodies the following mathematical relationship:
`y(x[i]) = f[2](w[00]¹f[0](w[00]⁰x[0]+w[10]⁰x[1]+w[20]⁰x[2]+w[30]⁰x[3])+w[10]¹f[1](w[41]⁰x[4]+w[51]⁰x[5]+w[61]⁰x[6]))`
The goal of training is to compute the set of weights `w[i]` that bring `y(x[i])` as close as possible to the observed data. The most popular method of training a neural network is called *backpropagation*, which consists of five steps:
1. Generate initial values of the weights, `w[i]`.
2. For each batch of input vectors `x[i]`, compute the output vectors `y(x[i])`. This is called *forward propagation*.
3. Compute the disparity between the output values `y(x[i])` and observed results, `obs[i]`. This is called the *loss*.
4. Use an optimization method to update the weights `w[i]` based on the computed loss.
5. Repeat Steps 2 through 4 until the loss falls to an acceptable value.
If these steps are performed correctly, the neural network will (theoretically) produce acceptable results for real-world prediction or classification. To clarify how these steps can be performed, the following discussion presents weight initialization, loss computation, and methods of optimization.

### Initializing Weights
When I started working with neural networks, weights were always initialized to 0.0. But researchers have found it better to use random values. The goal is to make sure none of the inputs are excessively magnified or reduced. This prevents weights from growing to infinity (exploding gradients problem) or shrinking to zero (vanishing gradient problem).
In the 2015 paper, *Delving Deep into Rectifiers*, Kaiming He and other researchers present a weight initialization method that takes into account the number of inputs entering a node. Each weight is assigned a value from a normal distribution whose average is zero and whose standard deviation, `σ`, is obtained in the following way:
$$\\sigma = \\sqrt{\\frac{2}{fan\\,\\, in}}$$
In this equation, *fan in* refers to the number of inputs entering the node. As the number of inputs increases, the standard deviation decreases and the initialization values come closer to zero.
An example will clarify how this works. If a node has four inputs, `σ` will equal sqrt(2/4) = 0.707. The mean is zero, so when normally distributed weights are generated, 68% of them should lie between –0.707 and 0.707. Ninety-five percent of the generated weights should have values between –1.414 and 1.414.
JavaScript doesn't provide functions that generate normally distributed values, so the example code in this chapter initializes weights using the Box-Muller Transform. This accepts two uniformly distributed random numbers, `x[1]` and `x[2]`, and generates normally distributed weights `w[1]` and `w[2]` using the following relationships:
$$\\begin{matrix} {w\_{1} = \\sqrt{- 2\\ln\\left( x\_{1} \\right)}\\cos\\left( {2\\pi x\_{2}} \\right)\\sigma} \\\\ {w\_{2} = \\sqrt{- 2\\ln\\left( x\_{1} \\right)}\\sin\\left( {2\\pi x\_{2}} \\right)\\sigma} \\\\ \\end{matrix}$$
In these equations, `σ` is the standard deviation computed from the He weight initialization method. The following code shows how the `Ch09_IrisNetwork` initializes its weights and stores them inside a buffer named `weightBuffer`.
```
const weightData = new Array(numWeights);
for (let i = 0; i < numWeights; i+= 2) {
    let x1 = Math.random();
    let x2 = Math.random();
    weightData[i] = Math.sqrt(-2.0 * Math.log(x1)) * Math.cos(2 * Math.PI * x2) * sigma;
    weightData[i + 1] = Math.sqrt(-2.0 * Math.log(x1)) * Math.sin(2 * Math.PI * x2) * sigma;
}
const weightRange = weightBuffer.getMappedRange();
new Float32Array(weightRange).set(weightData);
weightBuffer.unmap();
```
Note that bias weights are always initialized to zero. This ensures that regular input signals are given priority in determining the output.

### Computing Loss
During training, an application needs to measure how well the neural network is operating. To make this determination, it computes the disparity between the values of the network's output nodes and the observed values. This disparity is called the *loss*, and the method of computing the loss depends on many factors, including the nature of the neural network's output.
When training starts, all the weights have random values, so the output will likely be far away from the desired values (high loss). As training progresses, the weights will be updated to bring the network's output in line with observed values. When the network's output is acceptable, training stops (low loss). Loss is always greater than or equal to 0, and the lower the loss value, the better the training.
