— and the model's first layer treats each input feature as a separate channel and performs a one-dimensional convolution over them. A 1D convolution is just like the 2D convolutions you've already used, except it uses kernels that are vectors instead of matrices.

Each kernel is the length of the prediction window and gets applied to all the input features to produce a new output channel. The current version of the code applies 64 such kernels.

The convolutional layer in this diagram may seem confusing because it looks like the waves are two-dimensional, but these are actually just vectors with numbers in them that we are displaying as a 2D image. To display a vector in two dimensions, we treat each item's index in the vector as its value along the X axis. That is, each item in the vector represents a value at a specific point in time.

Remember from the discussions on transfer learning earlier in the book, how the pre-trained CNN extracts features from images and then the layers you use those extracted features as inputs? This might be what Turi's model does, except the CNN isn't pre-trained. The CNN learns to output a vector encapsulating any interesting temporal found within the prediction window. For example, maybe it notices patterns of peaks and valleys that are helpful when identifying a shaking phone. These extracted features flow into the LSTM layer as if they were a single item in a sequence.

> To understand why CNNs might be well suited to this task, it can help to think of this as a vision: imagine you plotted the sensor data for a prediction window, similar to what we show in the previous diagram, and then passed to a CNN. If CNNs can learn to recognize dogs in images, they should be capable of learning to recognize patterns in sequences just like the ones you saw in the previous chapter exploring the dataset.

The LSTM layer receives the extracted features from the CNN layer, it produces an output based on those features combined with its internal memory and its output from the previous prediction window. The LSTM's output passes through fully connected layers with batch normalization and dropout, and finally a softmax layer that outputs probabilities for each of the classes the model knows about. You learned about all those layer types earlier in the book they aren't discussed here.

This talk about internal memory and previous predictions brings up an important question: What about when a sequence doesn't relate to what came before it? Data doesn't always arrive as one long, unbroken stream, so do you really your

![](bbox=[0.161, 0.923, 0.836, 0.953])