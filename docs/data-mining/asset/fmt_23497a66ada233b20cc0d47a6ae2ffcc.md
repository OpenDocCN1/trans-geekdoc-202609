
CNNs are a special kind of feedforward network that has proven extremely successful for image analysis. When classifying images, filtering them—by applying a filter for edge detection—can provide a useful set of spatially organized features. Imagine now if one could learn many such filters jointly, along with the other parameters of the neural network. Each filter can be implemented by multiplying a relatively small spatial zone of the image by a set of weights and feeding the result to an activation function like those discussed earlier for vanilla feedforward networks. Because this filtering operation is simply repeated around the image using the same weights it can be implemented using so-called convolution operations. The result is a CNN, for which it is possible to learn both the filters and the classifier using gradient descent and the backpropagation algorithm.

In a CNN once an image has been filtered by several learnable filters each filter bank’s output is often aggregated across a small spatial region, using the average or maximum value. Aggregation can be performed within nonoverlapping regions, or using subsampling, yielding a lower-resolution layer of spatially organized features—a process that is sometimes referred to as “decimation.” This gives the model a degree of invariance to small differences as to exactly where a feature has been detected. For example, if aggregation uses the max operation, a feature is activated if it is detected anywhere in the pooling zone.

We have seen how synthetic transformations allowed deep feedforward networks to yield state-of-the-art performance in the MNIST evaluation, and that cropping small regions of an image can be a useful, easy-to-implement transformation. Although this can be applied to any classification technique, it is particularly effective for training CNNs. Random cropping positions can be used, or deterministic strategies such as cropping from the corners and center of the image can be. The same strategy can be used at test time, where the model’s predictions are averaged over crops from the test image. These networks are designed to have a certain degree of translational invariance but augmenting data through such global transformations can increase performance significantly.

[Fig. 10.5](#Ch011_391-432_B978044315888900011X.xhtml#f0030) shows a typical network structure. A smaller part of the original image is subjected to repeated phases of convolutional filtering, pooling, and decimation before being passed to a fully connected, nonconvolutional multilayer perceptron, which may have a number of hidden layers prior to making a final prediction.

![Fig. 10.5 Typical convolutional neural network architecture. Credit: Christopher J. Pal](images/F00011Xf10-05-9780443158889.jpg)

[Fig. 10.5](#Ch011_391-432_B978044315888900011X.xhtml#Bf0030) Typical convolutional neural network architecture. Credit: Christopher J. Pal

CNNs are usually optimized using mini-batch–based stochastic gradient descent, and the practical discussion earlier about learning deep networks applies here as well. Resource issues related to the amount of central processing unit (CPU) vs. graphics processing unit (GPU) memory available are often important to consider, particularly when processing videos.

## The ImageNet Evaluation and Very Deep Convolutional Networks

The ImageNet challenge has been crucial in demonstrating the effectiveness of deep CNNs. The problem is to recognize object categories in typical imagery that one might find on the Internet. The 2012 ImageNet Large Scale Visual Recognition Challenge (ILSVRC) classification task was to classify imagery obtained from Flickr and other search engines into the correct one of 1000 possible object category classes. This task served as a standard benchmark for deep learning. The imagery was hand-labeled based on the presence or absence of an object belonging to these categories. There were 1.2 *million* images in the training set, with 732-1300 training images available per class. A random subset of 50,000 images was used as the validation set and 100,000 images were used for the test set, with 50 and 100 images per class, respectively.

Visual recognition methods not based on deep CNNs hit a plateau in performance on this benchmark. The “top-5 error” is the percentage of times that the target label does not appear among the five highest-probability predictions, and many methods cannot get below 25%. [Table 10.4](#Ch011_391-432_B978044315888900011X.xhtml#t0025) summarizes the performance of different CNN architectures as a function of network depth for the ImageNet challenge. Note that CNNs dramatically outperform the 25% plateau, and that increasing network depth can further improve performance. Smaller filters have been found to lead to superior results in deep networks; the ones with 19 and 152 layers use filters of size 3 × 3<mml:math><mml:mn>3</mml:mn><mml:mo>&#215;</mml:mo><mml:mn>3</mml:mn></mml:math>![Equation](images/F00011Xsi70.png). The performance for human agreement has been measured at 5.1% top-5 error for ImageNet so deep CNNs are able to outperform people on this task.

Table 10.4

Convolutional Neural Network Performance on the ImageNet Challenge

| Name | Layers | Top-5 Error (%) | References |
| --- | --- | --- | --- |
| AlexNet | 8 | 15.3 | Krizhevsky et al. (2012) |
| --- | --- | --- | --- |
| VGG Net | 19 | 7.3 | [Simonyan and Zisserman (2014)](#References_705-736_B978044315888900025X.xhtml#fur496) |
| ResNet | 152 | 3.6 | He et al. (2016) |

Credit: Christopher J. Pal

## From Image Filtering to Learnable Convolutional Layers

When an image is filtered the output is another image that contains the filter’s response at each spatial location, one with its edges emphasized. We can also think of such an image as a *feature map* that indicates where certain features are detected in the image—edges. However, in a deep network the initial filtered images or feature maps are subjected to many further levels of filtering. Over many successive filter applications this produces spatially organized neurons that respond to much more complex inputs, and the term “feature map” becomes more descriptive.

When viewed as layers in a neural network that takes an image as input, these filtering operations can be viewed as constraining spatially organized neurons to respond only to features that are within a limited region of the input known as the neuron’s *receptive field*. When groups of such neurons respond in the same way to the same types of input we say they have shared parameters—but each neuron forming the feature map responds only when certain inputs are detected at corresponding spatially restricted receptive fields in the image.

Consider a simple example with a 1D vector `x`. A filtering operation can be implemented by multiplying it by a matrix `W` that has a special structure, such as
