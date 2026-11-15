
![](img/9499fc06bad8b4a2610710f5e9d6ea39_19_0.png)

This shape is a smoothed out version of a step function:

![](img/9499fc06bad8b4a2610710f5e9d6ea39_19_1.png)

If \(\sigma\) had in fact been a step function, then the sigmoid neuron would be a perceptron, since the output would be 1 or 0 depending on whether \(w \cdot x + b\) was positive or negative*. By using the actual \(\sigma\) function we get, as already implied above, a smoothed out perceptron. Indeed, it's the smoothness of the \(\sigma\) function that is the crucial fact, not its detailed form. The smoothness of \(\sigma\) means that small changes \(\Delta w_j\) in the weights and \(\Delta b\) in the bias will produce a small change \(\Delta \text{output}\) in the output from the neuron. In fact, calculus tells us that \(\Delta \text{output}\) is well approximated by

> *Actually, when \(w \cdot x + b = 0\) the perceptron outputs 0, while the step function outputs 1. So, strictly speaking, we'd need to modify the step function at that one point. But you get the idea.

```
\(\Delta \text{output} \approx \sum_j \frac{\partial \text{output}}{\partial w_j} \Delta w_j + \frac{\partial \text{output}}{\partial b} \Delta b, \quad (5)\)
```

where the sum is over all the weights, \(w_j\), and \(\partial \text{output}/\partial w_j\) and \(\partial \text{output}/\partial b\) denote partial derivatives of the output with respect to \(w_j\) and \(b\), respectively. Don't panic if you're not comfortable with partial derivatives! While the expression above looks complicated, with all the partial derivatives, it's actually saying something very simple (and which is very good news): \(\Delta \text{output}\) is a *linear function* of the changes \(\Delta w_j\) and \(\Delta b\) in the weights and bias. This linearity makes it easy to choose small changes in the weights and biases to achieve any desired small change in the output. So while sigmoid neurons have much of the same qualitative behaviour as perceptrons, they make it much easier to figure out how changing the weights and biases will change the output.

If it's the shape of \(\sigma\) which really matters, and not its exact form, then why use the particular form used for \(\sigma\) in Equation (3)? In fact, later in the book we will occasionally consider neurons where the output is \(f(w \cdot x + b)\) for some other activation function \(f(\cdot)\). The main thing that changes when we use a different activation function is that the particular values for the partial derivatives in Equation (5) change. It turns out that when we compute those partial derivatives later, using \(\sigma\) will simplify the algebra, simply because exponentials have lovely properties when differentiated. In any case, \(\sigma\) is commonly-used in work on neural nets, and is the activation function we'll use most often in this book.

How should we interpret the output from a sigmoid neuron? Obviously, one big difference between perceptrons and sigmoid neurons is that sigmoid neurons don't just output 0 or 1. They can have as output any real number between 0 and 1, so values such as 0.173 ... and 0.689 ... are legitimate outputs. This can be useful, for example, if we want to use the output value to represent the average intensity of the pixels in an image input to a neural network. But sometimes it can be a nuisance. Suppose we want the output from the network to indicate either "the input image is a 9" or "the input image is not a 9". Obviously, it'd be easiest to do this if the output was a 0 or a 1, as in a perceptron. But in practice we can set up a convention to deal with this, for example, by deciding to interpret any output of at least 0.5 as indicating a "9", and any output less than 0.5 as indicating "not a 9". I'll always explicitly state when we're using such a convention, so it shouldn't cause any confusion.

## Exercises

- Sigmoid neurons simulating perceptrons, part I
- Suppose we take all the weights and biases in a network of perceptrons, and multiply them by a positive constant, \(c > 0\).
- Show that the behaviour of the network doesn't change.

### Sigmoid neurons simulating perceptrons, part II

Suppose we have the same setup as the last problem - a network of perceptrons. Suppose also that the overall input to the network of perceptrons has been chosen. We won't need the actual input value, we just need the input to have been fixed. Suppose the weights and biases are such that \( w \cdot x + b \neq 0 \) for the input \( x \) to any particular perceptron in the network. Now replace all the perceptrons in the network by sigmoid neurons, and multiply the weights and biases by a positive constant \( c > 0 \). Show that in the limit as \( c \to \infty \) the behaviour of this network of sigmoid neurons is exactly the same as the network of perceptrons. How can this fail when \( w \cdot x + b = 0 \) for one of the perceptrons?

## The architecture of neural networks

In the next section I'll introduce a neural network that can do a pretty good job classifying handwritten digits. In preparation for that, it helps to explain some terminology that lets us name different parts of a network. Suppose we have the network:

![](img/9499fc06bad8b4a2610710f5e9d6ea39_21_0.png)

As mentioned earlier, the leftmost layer in this network is called the input layer, and the neurons within the layer are called input neurons. The rightmost or output layer contains the output neurons, or, as in this case, a single output neuron. The middle layer is called a hidden layer, since the neurons in this layer are neither inputs nor outputs. The term "hidden" perhaps sounds a little mysterious - the first time I heard the term I thought it must have some deep philosophical or mathematical significance - but it really means nothing more than "not an input or an output". The network above has just a single hidden layer, but some networks have multiple hidden layers. For example, the following four-layer network has two hidden layers:

![](img/9499fc06bad8b4a2610710f5e9d6ea39_22_0.png)

Somewhat confusingly, and for historical reasons, such multiple layer networks are sometimes called *multilayer perceptrons* or *MLPs*, despite being made up of sigmoid neurons, not perceptrons. I'm not going to use the MLP terminology in this book, since I think it's confusing, but wanted to warn you of its existence.

The design of the input and output layers in a network is often straightforward. For example, suppose we're trying to determine whether a handwritten image depicts a "9" or not. A natural way to design the network is to encode the intensities of the image pixels into the input neurons. If the image is a 64 by 64 greyscale image, then we'd have 4,096 = 64 × 64 input neurons, with the intensities scaled appropriately between 0 and 1. The output layer will contain just a single neuron, with output values of less than 0.5 indicating "input image is not a 9", and values greater than 0.5 indicating "input image is a 9".

While the design of the input and output layers of a neural network is often straightforward, there can be quite an art to the design of the hidden layers. In particular, it's not possible to sum up the design process for the hidden layers with a few simple rules of thumb. Instead, neural networks researchers have developed many design heuristics for the hidden layers, which help people get the behaviour they want out of their nets. For example, such heuristics can be used to help determine how to trade off the number of hidden layers against the time required to train the network. We'll meet several such design heuristics later in this book.

Up to now, we've been discussing neural networks where the output from one layer is used as input to the next layer. Such networks are called *feedforward* neural networks. This means there are no loops in the network - information is always fed forward, never fed back.

If we did have loops, we'd end up with situations where the input to the \(\sigma\) function depended on the output. That'd be hard to make sense of, and so we don't allow such loops.

However, there are other models of artificial neural networks in which feedback loops are possible. These models are called recurrent neural networks. The idea in these models is to have neurons which fire for some limited duration of time, before becoming quiescent. That firing can stimulate other neurons, which may fire a little while later, also for a limited duration. That causes still more neurons to fire, and so over time we get a cascade of neurons firing. Loops don't cause problems in such a model, since a neuron's output only affects its input at some later time, not instantaneously.

Recurrent neural nets have been less influential than feedforward networks, in part because the learning algorithms for recurrent nets are (at least to date) less powerful. But recurrent networks are still extremely interesting. They're much closer in spirit to how our brains work than feedforward networks. And it's possible that recurrent networks can solve important problems which can only be solved with great difficulty by feedforward networks. However, to limit our scope, in this book we're going to concentrate on the more widely-used feedforward networks.

## A simple network to classify handwritten digits

Having defined neural networks, let's return to handwriting recognition. We can split the problem of recognizing handwritten digits into two sub-problems. First, we'd like a way of breaking an image containing many digits into a sequence of separate images, each containing a single digit. For example, we'd like to break the image

![](img/9499fc06bad8b4a2610710f5e9d6ea39_23_0.png)

into six separate images,
