This is SqueezeNet, zoomed out:

![](bbox=[0.159, 0.149, 0.84, 0.245])

SqueezeNet uses the now-familiar Conv2D and MaxPoolLing2D layers, as well as the ReLU activation. However, it also has a branching structure that looks like this:

![](bbox=[0.309, 0.319, 0.69, 0.483])

# The fire module

This combination of several different layers is called a fire module, because no one reads your research papers until you come with a cool name for your inventions. SqueezeNet is simply a whole bunch of these fire modules stacked together.

In SqueezeNet, most of the convolution layers do not use 3×3 windows but consisting of a single pixel, also called 1×1 convolution. Such convolution filters only at a single pixel at a time and not at any of that pixel's neighbors. The math is just a regular dot product across the channels for that pixel.

Convolutions with a 1×1 kernel size are very common in modern convnets. They are often used to increase or decrease the number of channels in a tensor. That's why SqueezeNet uses them, too.

The squeeze part of the fire module has main job it is to reduce the number of channels. For example, the first layer in SqueezeNet is a regular 3×3 convolution with 64 filters. The squeeze layer that follows it, reduces this back to 16 filters. What such a layer learns isn't necessarily to detect patterns in the data, but to keep only the most important patterns. This forces the model to focus on learning only things that truly matter.