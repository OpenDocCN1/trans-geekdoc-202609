As per usual, we'll connect the input pixels to a layer of hidden neurons. But we won't connect every input pixel to every hidden neuron. Instead, we only make connections in small, localized regions of the input image.

To be more precise, each neuron in the first hidden layer will be connected to a small region of the input neurons, say, for example, a 5 x 5 region, corresponding to 25 input pixels. So, for a particular hidden neuron, we might have connections that look like this:

![](bbox=[0.233, 0.265, 0.55, 0.435])

That region in the input image is called the local receptive field for the hidden neuron. It's a little window on the input pixels. Each connection learns a weight. And the hidden neuron learns an overall bias as well. You can think of that particular hidden neuron as learning to analyze its particular local receptive field.

We then slide the local receptive field across the entire input image. For each local receptive field, there is a different hidden neuron in the first hidden layer. To illustrate this concretely, let's start with a local receptive field in the top-left corner:

![](bbox=[0.172, 0.66, 0.62, 0.82])

Then we slide the local receptive field over by one pixel to the right (i.e., by one neuron), to connect to a second hidden neuron: