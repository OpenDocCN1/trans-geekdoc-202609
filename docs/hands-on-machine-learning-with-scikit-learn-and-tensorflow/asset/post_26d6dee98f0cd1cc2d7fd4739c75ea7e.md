
![](img/0684d2da98e09085c0a622d4fd69aaad_458_0.png)

Figure 14-1. Local receptive fields in the visual cortex

These studies of the visual cortex inspired the neocognitron, introduced in 1980,⁴ which gradually evolved into what we now call convolutional neural networks. An important milestone was a 1998 paper⁵ by Yann LeCun, Léon Bottou, Yoshua Bengio, and Patrick Haffner, introduced the famous LeNet-5 architecture, widely used to recognize handwritten check numbers. This architecture has building blocks that you already know, such as fully connected layers and sigmoid activation functions, but it also introduces two new building blocks: convolutional layers and pooling layers. Let's look at them now.

Why not use a regular deep neural network with fully connected layers for image recognition tasks? Unfortunately, although this works for small images (e.g., MNIST), it breaks down for larger images because of the huge number of parameters it requires. For example, a 100 × 100 image has 10,000 pixels, and the first layer has 1,000 neurons (which already severely restricts the amount of information transmitted to the next layer), this means a total of 10 million connections. And that's the first layer. CNNs solve this problem using partially connected layers and weight sharing.

⁴Neocognitron: A Self-organizing Neural Network Model for a Mechanism of Pattern Recognition Unaffected by Shift in Position,” K. Fukushima (1980).

⁵“Gradient-Based Learning Applied to Document Recognition,” Y. LeCun et al. (1998).

The Architecture of the Visual Cortex | 433

WOW! eBook
www.wowebook.org

# Convolutional Layer

The most important building block of a CNN is the convolutional layer; neurons in the first convolutional layer are not connected to every pixel in the input image (like they were in previous chapters), but only to pixels in their receptive fields (see Figure 14-2). In turn, each neuron in the second convolutional layer is connected only to neurons located within a small rectangle in the first layer. This architecture allows the network to concentrate on small low-level features in the first hidden layer, then assemble them into larger high-level features in the next hidden layer, and so on. This hierarchical structure is common in real-world images, which is one of the reasons why CNNs work so well for image recognition.

![](img/0684d2da98e09085c0a622d4fd69aaad_459_0.png)

Figure 14-2. CNN layers with rectangular local receptive fields

Until now, all multilayer neural networks we looked at had layers composed of a long line of neurons, and but now each layer is represented in 2D, which makes it easier to match neurons with their corresponding inputs.

A neuron located in row i, column j of a given layer is connected to the outputs of the neurons in the previous layer located in rows i to i + f_h - 1, columns j to j + f_w - 1, where $f_h$ and $f_w$ are the height and width of the receptive field (see Figure 14-3). For order for a layer to have the same height and width as the previous layer, it is-

> 6 Convolution is a mathematical operation that slides one function over another and measures the integral of their pointwise multiplication. It has deep connections with the Fourier transform and the Laplace transform, and is heavily used in signal processing. Convolutional layers actually use cross-correlation, which are very similar to convolutions (see https://home.info/76 for more details).

434 | Chapter 14: Deep Computer Vision Using Convolutional Neural Networks

mon to add zeros around the inputs, as shown in the diagram. This is called zero padding.

![](img/0684d2da98e09085c0a622d4fd69aaad_460_0.png)

Figure 14-3. Connections between layers and zero padding

It is also possible to connect a large input layer to a much smaller layer by spacing out the receptive fields, as shown in Figure 14-4. The shift from one receptive field to the next is called the stride. In the diagram, a $5 \times 7$ input layer (plus zero padding) is connected to a $3 \times 4$ layer, using $3 \times 3$ receptive fields and a stride of 2 (in this example the stride is the same in both directions, but it does not have to be). A neuron located in row $i$, column $j$ in the upper layer is connected to the outputs of the neurons in the previous layer in rows $i \times s_h$ to $i \times s_h + f_h - 1$, columns $j \times s_w$ to $j \times s_w + f_w - 1$, where $s_h$ and $s_w$ are the vertical and horizontal strides.

![](img/0684d2da98e09085c0a622d4fd69aaad_461_0.png)

Figure 14-4. Reducing dimensionality using a stride of 2

# Filters

A neuron's weights can be represented as a small image the size of the receptive field. For example, Figure 14-5 shows two possible sets of weights, called filters (or convolution kernels). The first one is represented as a black square with a white line in the middle (it is a 7 × 7 matrix full of 0s except for the central column, which is full of 1s); neurons using these weights will ignore everything in their receptive field except for the central vertical line (since all inputs get multiplied by 0, except for the ones located in the central vertical line). The second filter is a black square with a horizontal white line in the middle. Once again, neurons using these weights will ignore everything in their receptive field except for the central horizontal line.

Now if all neurons in a layer use the same vertical filter (and the same bias term), and you feed the network input image using Figure 14-5 (bottom image), the layer will output the top-left image. Notice that the white lines get enhanced while the rest get blurred. Similarly, the upper-right image will get if you get all neurons use the same horizontal line filter; notice that the horizontal lines get enhanced while the rest is blurred out. Thus, a full layer of neurons using the same filter outputs a feature map, which highlights the areas in an image that activate the filter. Of course you do not have to define the filters manually; instead, training the convolutional layer will automatically learn the most useful filters for its task, and the layers above will learn to combine them into more complex patterns.

![](img/0684d2da98e09085c0a622d4fd69aaad_462_0.png)

Figure 14-5. Applying two different filters to get two feature maps

# Stacking Multiple Feature Maps

Up now, for simplicity, I have represented the output of each convolutional layer as a 2D depth, but in reality a convolutional layer has multiple filters (you decide how many), it outputs one feature map per filter, so it is more accurately represented in 3D (see Figure 14-6). To do so, it has one neuron per pixel in each feature map, and all neurons within a given feature map share the same parameters (i.e., the same weights and bias term). However, neurons in different feature maps differ parameters. A neuron's receptive field is the same as described earlier, but extends across all the previous layers' feature maps. In short, a convolutional layer simultaneously applies trainable filters to its inputs, making capable of detecting multiple features in its inputs.

> The fact that all neurons in a feature map share the same parameters dramatically reduces the number of parameters in the model. Moreover, the CNN has learned to recognize a pattern in one location, it can recognize it in any other location. In contrast, a regular DNN has learned to recognize a pattern in one location, it can recognize it only in that particular location.

Moreover, input images are also composed of multiple sublayers: one per color channel. There are typically three: red, green, and blue (RGB). Grayscale images have just one channel, but some images may have much more—for example, satellite images that capture extra light frequencies (such as infrared).

![](img/0684d2da98e09085c0a622d4fd69aaad_463_0.png)

Figure 14-6. Convolutional layers with multiple feature maps, and images with three color channels

Specifically, a neuron located in row $i$, column $j$ of the feature map $k$ in a given convolutional layer $l$ is connected to the outputs of the neurons in the previous layer $l-1$, located in $i \times s_h$ to $i \times s_h + f_h - 1$ and columns $j \times s_w$ to $j \times s_w + f_w - 1$, across all feature maps (layer $l-1$). Note that all neurons located in the same row and column $j$ but in different feature maps are connected to the outputs of the exact same neurons in the previous layer.

Equation 14-1 summarizes the preceding explanations in one big mathematical equation: it shows how to compute the output of a given neuron in a convolutional layer.
