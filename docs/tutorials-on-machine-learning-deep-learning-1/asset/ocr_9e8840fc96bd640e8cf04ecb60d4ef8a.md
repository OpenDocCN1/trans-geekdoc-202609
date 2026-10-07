The key-point is: the primary purpose of Convolution is to find features in your image using the feature detector put them into a Feature map by preserving the spatial relationships between pixels (if they are completely jumbled then we've lost the pattern).

It's important to understand that most of the time the features a neural network will detect/recognize certain images and classes, it will mean nothing to humans.

#  9.2.2 Rectified Linear Unit (ReLU)

ReLU (Rectified Linear Unit) is an additional step on top of our Convolution step. Here we have our Input image and we have all Convolution Layer on top of that we're going to apply rectifier function. The reason why we're applying the rectifier we want to Increase Non-Linearity in our image or in our CNN. ReLU acts as filter or that function that breaks linearity.

![](bbox=[0.095, 0.295, 0.855, 0.465])

+   - Why increase Non-linearity: We want to increase nonlinearity in our network is because images themselves are highly non-linear especially if you're recognizing different objects next to each other.
- Images are going to have lots of nonlinear elements and the transition between pixels-adjacent pixels is often becomes nonlinear, because of its borders, different colors, elements in your images.
- When we're applying a mathematical operation such as convolution, and running this feature detection to create our feature maps there is a possibility that we might create something linear therefore we need to break up the linearity.

Example: Here is a image an original image. When we apply a feature detector to this image we get:

You can see that black is negative and white is positive. When you apply a feature detector to a real-life image, (not just 1 or 0 but lots of different values, including negative values) we get this kind of result.

![](bbox=[0.525, 0.64, 0.875, 0.955])