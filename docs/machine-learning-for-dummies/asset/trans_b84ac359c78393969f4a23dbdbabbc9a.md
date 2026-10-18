

# 神经网络基础

This threshold outputs a value of 1; otherwise, its prediction is 0. Unfortunately, a perceptron can't learn when the classes it tries to process aren’t linearly separable. However, scholars discovered that even though a single perceptron couldn’t learn the logical operation XOR shown in [Figure 14-1](#c14.xhtml#c14-fig-0001) (the exclusive or, which is true only when the inputs are dissimilar), two perceptrons working together could.

![FIGURE 14-1: Learning logical XOR using a single separating line isn’t possible.](images/9781119724018-fg1401.png)

[FIGURE 14-1:](#c14.xhtml#rc14-fig-0001) Learning logical XOR using a single separating line isn’t possible.

Neurons in a neural network are a further evolution of the perceptron: They take many weighted values as inputs, sum them, and provide the summation as the result, just as a perceptron does. However, they also provide a more sophisticated transformation of the summation, something that the perceptron can’t do. In observing nature, scientists noticed that neurons receive signals but don’t always release a signal of their own. It depends on the amount of signal received. When a neuron acquires enough stimuli, it fires an answer; otherwise it remains silent. In a similar fashion, algorithmic neurons, after receiving weighted values, sum them and use an `activation function` to evaluate the result, which transforms it in a nonlinear way. For instance, the activation function can release a zero value unless the input achieves a certain threshold, or it can dampen or enhance a value by nonlinearly rescaling it, thus transmitting a rescaled signal.

A neural network has different activation functions, as shown in [Figure 14-2](#c14.xhtml#c14-fig-0002). The linear function (labeled Binary step) doesn’t apply any transformation, and it’s seldom used because it reduces a neural network to a regression with polynomial transformations. Neural networks commonly use the sigmoid (also known as logistic) or the hyperbolic tangent (labeled TanH), or the ReLU (which is by far the more common today) activation functions.

![FIGURE 14-2: Plots of different activation functions.](images/9781119724018-fg1402.png)

[FIGURE 14-2:](#c14.xhtml#rc14-fig-0002) Plots of different activation functions.

The figure shows how an input (expressed on the horizontal axis) can transform an output into something else (expressed on the vertical axis). The examples show a binary step, a logistic, a tangent hyperbolic, and a ReLU activation function.

![Tip](images/tip.png)You learn more about activation functions later in the chapter, but note for now that activation functions clearly work well in certain ranges of input values. As you can see from [Figure 14-2](#c14.xhtml#c14-fig-0002), they output end-of-scale values outside certain input boundaries. For this reason, you should always rescale inputs to a neural network using statistical standardization (zero mean and unit variance) or normalize the input in the range from 0 to 1 or from –1 to +1.

## Pushing forth with feed-forward

In a neural network, you have first to consider the architecture, which is how the neural network components are arranged. Contrary to other algorithms, which have a fixed pipeline that determines how algorithms receive and process data, neural networks require you to decide how information flows by fixing the number of units (the neurons) and their distribution in layers, as shown in [Figure 14-3](#c14.xhtml#c14-fig-0003).

![FIGURE 14-3: An example of the architecture of a neural network.](images/9781119724018-fg1403.png)

[FIGURE 14-3:](#c14.xhtml#rc14-fig-0003) An example of the architecture of a neural network.

The figure shows a simple neural architecture. Note how the layers filter information in a progressive way. This is a feed-forward input because data feeds forward into the network in a single direction. Connections exclusively link the units in one layer with the units in the following layers (information flow from left to right). No connections exist between units in the same layer or with units outside the next layers. The information usually pushes forward to the next layer, but it can skip to additional layers forward. The example of [Figure 14-3](#c14.xhtml#c14-fig-0003) shows the connections from the left to the right, but in other representations, you may find connections from top to bottom or bottom to top. Processed data never returns to previous neuron layers.

![Remember](images/remember.png)Neural networks are also seen as graphs. A `graph` is simply a set of vertexes, nodes, or points connected by edges, arcs, or lines. In the case of neural networks, the graph is called a Directed Acyclic Graph (DAG) because: 

*   You can’t get from one vertex to another and back to the beginning vertex using any route.

*   There is a predictable set of routes moving from one vertex to the next one.

![Remember](images/remember.png)There are kinds of neural networks that actually allow loops, though the loops occur inside certain neurons (not between layers) and they’re limited to the size of the input they receive. Such networks are called `Recurrent Neural Networks` (RNNs), and they are briefly illustrated at the end of this chapter.

Using a neural network is like using a stratified filtering system for water: You pour the water from above and the water is filtered at the bottom. The water has no way to go back; it just goes forward and straight down, and never laterally. In the same way, neural networks force data features to flow through the network and mix with each other only according to the network’s architecture. By using the best architecture to mix features, the neural network creates new composed features at every layer and helps achieve better predictions. Unfortunately, there is no way to determine the best architecture without empirically (or systematically) trying different solutions and testing whether output data helps predict your target values after flowing through the network.

The first and last layers play an important role. The first layer, called the `input layer`, picks up the features from each data example processed by the network. The last layer, called the `output layer`, releases the results.

A neural network can process only numeric, continuous information; it can’t be constrained to work with qualitative features (for example, labels indicating a quality such as red, blue, or green in an image). You can process qualitative features by transforming them into a continuous numeric value, such as a series of binary values, as discussed in [Chapter 7](#c07.xhtml) in the material about working with data. When a neural network processes a binary feature, the neuron treats the feature as a generic number and turns the binary values into other values, even negative ones, by processing across units.

Note the limitation of dealing only with numeric values, because you can’t expect the last layer to output a nonnumeric label prediction. When dealing with a regression problem, the last layer is a single unit. Likewise, when you’re working with a classification and you have output that must choose from a number of classes, you should have an equivalent number of terminal units, each one representing a score linked to the probability of the represented class. Therefore, when classifying a multiclass problem (as discussed in the “[Handling multiple classes](#c13.xhtml#c13-sec-0009)” section in [Chapter 13](#c13.xhtml)), such as a penguin species, the final layer has as many units as species. To see how this works, review the Palmer Penguins dataset demonstration in the “[Experimenting with K-means reliability](#c12.xhtml#c12-sec-0009)” section of [Chapter 12](#c12.xhtml). You have three units representing one of the three Penguin species: Adele, Chinstrap, or Gentoo). For each example, the predicted class is the one that gets the higher score at the end.

