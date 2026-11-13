# A4.3.9 Convolutional neural networks

Convolution: a mathematical operation that combines two functions to produce a third function. In the context of a convolutional neural network being used for image processing, convolution applies filtering functions to the pixels in an input image to compute distinctive features from the data.

A convolutional neural network (CNN) extends on the architecture of ANNs by using additional layers of calculations prior to processing the data through a fully connected artificial neural network.

CNNs are ideally suited to processing image data but are also valuable for applications such as video analysis, natural language processing (NLP), audio and speech processing, and recommendation systems.

To explore what makes a CNN different from an ANN, consider the following diagram of a typical convolutional neural network:

![](bbox=[0.285, 0.255, 0.9, 0.405])

# Input layer

The input layer comprises the raw pixel data of the image being processed. The number of input nodes would be based upon image width x image height x colour depth.

It is important to consider that, when dealing with input data such as images, the input data can get very large with relative ease. A small image of only 100 x 100 pixels at full colour resolution (that is, 1 byte each for red, green and blue) would comprise 300,000 values. This is too much to feed directly into an ANN, and so preprocessing through convolution and pooling is used to reduce this to something more manageable.

# Convolutional layer

The convolutional layers serve as feature extractors that are looking for patterns in the input image.

As the network trains, it develops filters (also known as “kernels”) that learn to detect patterns that are important for the individual network at hand. Generally, these patterns are as simple as edge detection or various textures, but they can be used to detect more complex shapes within the image. Other common patterns that may emerge are sharpening filters and blur filters.

Edge detection will typically look for vertical or horizontal edges. For instance, the matrix to find vertical edges may look like this:

```
[-1  0  1]
[-1  0  1]
[-1  0  1]
```

Applying an edge detection filter to an image is shown in the following diagram. The first image is the original; the second is the output using vertical edge detection with the matrix above; the third is horizontal edge detection after rotating the matrix clockwise.