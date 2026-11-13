
## Listing 8.3 Training the convnet on MNIST images

```python
from tensorflow.keras.datasets import mnist

(train_images, train_labels), (test_images, test_labels) = mnist.load_data()
train_images = train_images.reshape((60000, 28, 28, 1))
train_images = train_images.astype("float32") / 255
test_images = test_images.reshape((10000, 28, 28, 1))
test_images = test_images.astype("float32") / 255
model.compile(optimizer="rmsprop",
              loss="sparse_categorical_crossentropy",
              metrics=["accuracy"])
model.fit(train_images, train_labels, epochs=5, batch_size=64)
```

Let's evaluate the model on the test data.

## Listing 8.4 Evaluating the convnet

```python
>>> test_loss, test_acc = model.evaluate(test_images, test_labels)
>>> print(f"Test accuracy: {test_acc:.3f}")
Test accuracy: 0.991
```

Whereas the densely connected model from chapter 2 had a test accuracy of 97.8%, the basic convnet has a test accuracy of 99.1%: we decreased the error rate by about 60% (relative). Not bad!

But why does this simple convnet work so well, compared to a densely connected model? To answer this, let's dive into what the Conv2D and MaxPooling2D layers do.

### 8.1.1 The convolution operation

The fundamental difference between a densely connected layer and a convolution layer is this: Dense layers learn global patterns in their input feature space (for example, for a MNIST digit, patterns involving all pixels), whereas convolution layers learn local patterns—in the case of images, patterns found in small 2D windows of the inputs (see figure 8.1). In the previous example, these windows were all 3 × 3.

![](img/ab452ecf572a1f1372915be13bd8088f_228_0.png)

Figure 8.1 Images can be broken into local patterns such as edges, textures, and so on.

This key characteristic gives convnets two interesting properties:

- The patterns they learn are translation-invariant. After learning a certain pattern in the lower-right corner of a picture, a convnet can recognize it anywhere: for example, in the upper-left corner. A densely connected model would have to learn the pattern anew if it appeared at a new location. This makes convnets data-efficient when processing images (because the *visual world is fundamentally translation-invariant*); they need fewer training samples to learn representations that have generalization power.

- They can learn spatial hierarchies of patterns. A first convolution layer will learn small local patterns such as edges, a second convolution layer will learn larger patterns made of the features of the first layers, and so on (see figure 8.2). This allows convnets to efficiently learn increasingly complex and abstract visual concepts, because *the visual world is fundamentally spatially hierarchical*.

![](img/ab452ecf572a1f1372915be13bd8088f_229_0.png)

Figure 8.2 The visual world forms a spatial hierarchy of visual modules: elementary lines or textures combine into simple objects such as eyes or ears, which combine into high-level concepts such as “cat.”

Convolutions operate over rank-3 tensors called *feature maps*, with two spatial axes (*height* and *width*) as well as a *depth* axis (also called the *channels* axis). For an RGB image, the dimension of the depth axis is 3, because the image has three color channels: red, green, and blue. For a black-and-white picture, like the MNIST digits, the depth is 1 (levels of gray). The convolution operation extracts patches from its input feature map and applies the same transformation to all of these patches, producing an *output feature map*. This output feature map is still a rank-3 tensor: it has a width and a height. Its depth can be arbitrary, because the output depth is a parameter of the layer, and the different channels in that depth axis no longer stand for specific colors as in RGB input; rather, they stand for _filters_. Filters encode specific aspects of the input data: at a high level, a single filter could encode the concept “presence of a face in the input,” for instance.

In the MNIST example, the first convolution layer takes a feature map of size (28, 28, 1) and outputs a feature map of size (26, 26, 32): it computes 32 filters over its input. Each of these 32 output channels contains a 26 × 26 grid of values, which is a _response map_ of the filter over the input, indicating the response of that filter pattern at different locations in the input (see figure 8.3).

![](img/ab452ecf572a1f1372915be13bd8088f_230_0.png)

That is what the term _feature map_ means: every dimension in the depth axis is a _feature_ (or filter), and the rank-2 tensor `output[:, :, n]` is the 2D spatial _map_ of the response of this filter over the input.

Convolutions are defined by two key parameters:

- Size of the patches extracted from the inputs—These are typically 3 × 3 or 5 × 5. In the example, they were 3 × 3, which is a common choice.

- Depth of the output feature map—This is the number of filters computed by the convolution. The example started with a depth of 32 and ended with a depth of 64.

In Keras `Conv2D` layers, these parameters are the first arguments passed to the layer: `Conv2D(output_depth, window_height, window_width)`.

A convolution works by _sliding_ these windows of size 3 × 3 or 5 × 5 over the 3D input feature map, stopping at every possible location, and extracting the 3D patch of surrounding features (shape (`window_height`, `window_width`, `input_depth`)). Each such 3D patch is then transformed into a 1D vector of shape (`output_depth`,), which is done via a tensor product with a learned weight matrix, called the _convolution kernel_— the same kernel is reused across every patch. All of these vectors (one per patch) are then spatially reassembled into a 3D output map of shape (`height`, `width`, `output_depth`). Every spatial location in the output feature map corresponds to the same location in the input feature map (for example, the lower-right corner of the output contains information about the lower-right corner of the input). For instance, with 3 x 3 windows, the vector output[i, j, :] comes from the 3D patch input[i-1:i+1, j-1:j+1, :]. The full process is detailed in figure 8.4.

![](img/ab452ecf572a1f1372915be13bd8088f_231_0.png)

**Figure 8.4** How convolution works

Note that the output width and height may differ from the input width and height for two reasons:

- Border effects, which can be countered by padding the input feature map

- The use of strides, which I'll define in a second

Let's take a deeper look at these notions.

### UNDERSTANDING BORDER EFFECTS AND PADDING

Consider a 5 x 5 feature map (25 tiles total). There are only 9 tiles around which you can center a 3 x 3 window, forming a 3 x 3 grid (see figure 8.5). Hence, the output feature map will be 3 x 3. It shrinks a little: by exactly two tiles alongside each dimension, in this case. You can see this border effect in action in the earlier example: you start with 28 x 28 inputs, which become 26 x 26 after the first convolution layer.

If you want to get an output feature map with the same spatial dimensions as the input, you can use padding. Padding consists of adding an appropriate number of rows

![](img/ab452ecf572a1f1372915be13bd8088f_232_0.png)

and columns on each side of the input feature map so as to make it possible to fit center convolution windows around every input tile. For a 3 x 3 window, you add one column on the right, one column on the left, one row at the top, and one row at the bottom. For a 5 x 5 window, you add two rows (see figure 8.6).

![](img/ab452ecf572a1f1372915be13bd8088f_232_1.png)

In Conv2D layers, padding is configurable via the padding argument, which takes two values: "valid", which means no padding (only valid window locations will be used), and "same", which means "pad in such a way as to have an output with the same width and height as the input." The padding argument defaults to "valid".

### UNDERSTANDING CONVOLUTION STRIDES

The other factor that can influence output size is the notion of strides. Our description of convolution so far has assumed that the center tiles of the convolution windows are all contiguous. But the distance between two successive windows is a parameter of the
