
- There is now a huge quantity of data available to train neural networks, and ANNs frequently outperform other ML techniques on very large and complex problems.

- The tremendous increase in computing power since the 1990s now makes it possible to train large neural networks in a reasonable amount of time. This is in part due to Moore's Law, but also thanks to the gaming industry, which has produced GPU cards by the millions.

- The training algorithms have been improved. To be fair they are only slightly different from the ones used in the 1990s, but these relatively small tweaks have a huge positive impact.

- Some theoretical limitations of ANNs have turned out to be in practice. For example, many people thought that ANN training algorithms were doomed because they were likely to get stuck in local optima, but it turns out that this is rarer in practice (or when it is the case, they are usually close to the global optimum).

- ANNs seem to have entered a virtuous cycle of funding and progress. Amazing products based on ANNs regularly make the headline news, which pulls more and more attention and funding toward them, resulting in more and more, even more amazing products.

## Biological Neurons

Before we discuss artificial neurons, let's take a quick look at a biological neuron (represented in Figure 10-1). It is an unusual-looking cell most found in animal cerebral cortex (e.g., your brain), composed of a *body* containing the nucleus and most of the cell's complex components, and many branching extensions called *dendrites*, plus one long extension called the *axon*. The axon's length may be a few times longer than the cell body, or up to thousands of times longer. Near its axon splits into many branches called *telodendria*, and at the tip of these branches are minuscule structures called *synaptic terminals* (or simply *synapses*), which are connected to the dendrites (or directly to the cell) of other neurons. Biological neurons receive short electrical impulses called *signals* from other neurons via these synapses. When a neuron receives a sufficient number of signals from other neurons within a few milliseconds, it fires its own signals.

![](img/0684d2da98e09085c0a622d4fd69aaad_305_0.png)

Figure 10-1. Biological neuron³

Thus, individual biological neurons seem to behave in a rather simple way, but they are organized in a vast network of neurons, each neuron typically connected to other neurons. Highly complex computations can be performed by a vast network of simple neurons, much like a complex anthill emerge from the combined efforts of simple agents. The architecture of biological neural networks (BNN³) is still the subject of active research, but some parts of the brain have been mapped, and it seems that neurons are often organized in consecutive layers, as shown in Figure 10-2.

![](img/0684d2da98e09085c0a622d4fd69aaad_305_1.png)

Figure 10-2. Multiple layers in a biological neural network (human cortex)⁵

³ Image by Bruce Blau [Creative Commons 3.0]. Reproduced from https://en.wikipedia.org/wiki/Neuron.
⁴ In the context of Machine Learning, the phrase "neural networks" generally refers to ANNs, not BNNs. 
⁵ Drawing of a complex lamination by S. Ramon y Cajal (public domain). Reproduced from https://en.wikipedia.org/wiki/Cerebral_cortex.

280 | Chapter 10: Introduction to Artificial Neural Networks with Keras

## Logical Computations with Neurons

Warren McCulloch and Walter Pitts proposed a very simple model of the biological neuron, which later became known as an artificial neuron: it has one or more binary (on/off) inputs and one binary output. The artificial neuron simply activates its output when more than a certain number of inputs is active. McCulloch and Pitts showed that even with a simplified model it is possible to build a network of artificial neurons that computes any logical proposition you want. For example, let's build a few ANNs that perform various logical computations (see Figure 10-3), assuming that the neuron is activated when at least two of its inputs are active.

![](img/0684d2da98e09085c0a622d4fd69aaad_306_0.png)

Figure 10-3. ANNs performing simple logical computations

- The first network on left is the identity function: if neuron A is activated, neuron C activates as well (it receives two input signals from neuron A), but if neuron A is off, then neuron C is off as well.
- The second network performs a logical AND: neuron C is activated only when both neurons A and B are activated (a single input signal is not enough to activate C).
- The third network performs a logical OR: neuron C is activated if either neuron A or neuron B is activated (or both).
- If, we suppose that an input connection can inhibit the neuron's activity (which is the case with biological neurons), the fourth network computes a slightly more complex logical proposition: neuron C is activated only if neuron A is active and neuron B is off. If neuron A is all the time, then you get a logical NOT: neuron C is active when neuron B is off, and vice versa.

You can easily imagine how these networks can be combined to compute complex logical expressions (see the exercises at the end of the chapter).

## The Perceptron

The Perceptron is one of the simplest ANN architectures, invented in 1957 by Frank Rosenblatt. It is based on a slightly different artificial neuron (see Figure 10-4) called a threshold logic unit (TLU), sometimes a linear threshold unit (LTU): the inputs and output are now numbers (instead of binary on/off values) and each input connection is associated with a weight. The TLU computes a weighted sum of its inputs ($z = w_1x_1 + w_2x_2 + \dots + w_nx_n = \mathbf{w}^T\mathbf{x}$), then applies a *step function* to that sum and outputs the result: $h_w(x) = \text{step}(z)$, where $z = \mathbf{x}^T\mathbf{w}$.

![](img/0684d2da98e09085c0a622d4fd69aaad_307_0.png)

Figure 10-4. Threshold logic unit

The most common step function used in Perceptrons is the Heaviside step function (see Equation 10-1). Sometimes the sign function is used instead.

### Equation 10-1. Common step functions used in Perceptrons

```
$\text{heaviside}(z) = \begin{cases} 0 & \text{if } z < 0 \\ 1 & \text{if } z \geq 0 \end{cases}$
$\text{sgn}(z) = \begin{cases} -1 & \text{if } z < 0 \\ 0 & \text{if } z = 0 \\ +1 & \text{if } z \geq 0 \end{cases}$
```

A single TLU can be used for simple binary classification. It computes a linear combination of the inputs and if the result exceeds the threshold, it outputs the positive class or else outputs the negative class (just like a Logistic Regression classifier or a linear SVM). For example, you could use a single TLU to classify iris flowers based on the petal length and width (adding an extra bias feature $x_0=1$, just like we did in previous chapters). Training a TLU in this case means finding the right values for $w_1$ and $w_2$ (the training algorithm is discussed shortly).

A Perceptron is simply composed of a single layer of TLUs, with each TLU connected to all the inputs. When all the neurons in a layer are connected to neuron in the previous layer (i.e., its input neurons), it is a *fully connected layer* or *dense layer*. To represent the fact that each input is set to every TLU, it is common to draw special passthrough neurons called *input neurons*; they output whatever input they are fed. All the input neurons form the *input layer*. Moreover, an extra feature is generally added (x₀ = 1): it is typically represented using a special type of neuron called bias neuron, which just outputs 1 all the time. > 6 The name Perceptron is sometimes used to mean a tiny network with a single TLU. A Perceptron with two inputs and three outputs is represented in Figure 10-5. This Perceptron can classify instances simultaneously into three different classes, which makes it a multi-output classifier.

![](img/0684d2da98e09085c0a622d4fd69aaad_308_0.png)

Figure 10-5. Perceptron diagram

Thanks to the magic of linear algebra, it is possible to efficiently compute the outputs of a layer of artificial neurons for several instances at once, by using Equation 10-2:

Equation 10-2. Computing the outputs of a fully connected layer

hw,b(X) = ϕ(XW + b)

- As weights, X represents the matrix of input features. It has one row per instance, one column per feature.
- The weight matrix W contains all the connection weights except for the ones from the bias neuron. It has one row per input neuron and one column per artificial neuron in the layer.
- The bias vector b contains all the connection weights between the bias neuron and the artificial neurons. It has one term per artificial neuron.
- The function ϕ is called the activation function: when the artificial neurons TLUs, it is a step function (but we will discuss other activation functions shortly).

So how is a Perceptron trained? The Perceptron training algorithm proposed by Frank Rosenblatt was largely inspired by Hebb rule. In his book The Organization of Behavior, published in 1949, Donald Hebb suggested that when a biological neuron often triggers another neuron, the connection between these two grows stronger. This idea was later summarized by Sigmund Löbler in this catchy phrase: "Cells that fire together, wire together." This rule later became known as Hebb’s rule.
