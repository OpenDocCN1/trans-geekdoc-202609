
samples. Moreover, these models are very deep and complex and require
a lot of computational power to train.

This chapter aims to develop a better understanding of semantic
segmentation and its application in satellite imagery. In this chapter,
state-of-the-art semantic segmentation architectures are presented and
reviewed.

The rest of this chapter is laid out in the following manner: Section
13.2 discusses satellite imagery, its unique properties, and the challenges
faced in processing it. Section 13.3 provides an overview of CNNs, which
are the backbone of computer vision tasks using deep learning. Various
state-of-the-art semantic segmentation architectures are discussed in
Section 13.4. Section 13.5 discusses developments in the field of semantic
segmentation of satellite images. The chapter concludes with pointers to
future research in Section 13.6.

## 13.2 SATELLITE IMAGERY

Satellite data serve as a reliable source of information that is globally
available. Landsat-1 was the first civil earth surveillance satellite launched
in 1972. Researchers have been researching satellite imagery applications
since then. At present, more than 4500 satellites are orbiting the earth, with
more than 700 being imagery satellites for earth observation.

### 13.2.1 PROPERTIES OF SATELLITE IMAGERY

- *Spatial resolution*: It refers to the visible details in pixel space. A
spatial resolution of 15 m, for example, means that each pixel on
the image corresponds to a 15 × 15 m2 area on the ground.
- *Temporal resolution*: It is dependent on the satellite's revisit period.
- *Spectral resolution*: It refers to the number of electromagnetic
(EM) bands present in an image. Instead of only red, blue,
and green, satellite photography includes microwaves (radar),
infrared (IR), near-IR (NIR), mid-IR (MIR), ultraviolet, and other
EM bands, as shown in Figure 13.1. Depending on the spectral
resolution, satellite imagery can be classified as multispectral and
hyperspectral. Hyperspectral images are made up of a large number
of very small EM bands with wavelengths ranging from 10 to 20 nm. One such example is NASA's Hyperion imaging spectrometer, which produces 30 m resolution images in 220 spectral bands. The multispectral images obtained from the Landsat-8 sensors are similar, although they have fewer and larger bands.

![](img/08e33f9814ed09d3c1bb11cd99f09e86_256_0.png)

FIGURE 13.1 The EM spectrum.

Source: Reprinted from Philip Ronan, http://creativecommons.org/licenses/by-sa/3.0/

- Radiometric resolution: It is defined as the ability of the sensor to discriminate between differences in energy.

Current state-of-the-art satellites have a resolution of 25 cm per pixel, which means that a person takes 3 pixels on an image. The images are captured every 14 days by the American Landsat satellite, which has a resolution of 30 m per pixel. The Sentinel satellites Sentinel-1, Sentinel-2, Sentinel-3, Sentinel-4, Sentinel-5, and Sentinel-5P are part of the European Space Agency's Copernicus Program. Sentinel-1 and Sentinel-2 are used for monitoring land and water, while the others are meant for purposes such as air quality monitoring, ozone monitoring, UV radiation monitoring, etc. The Sentinel-2 satellite mission involves two satellites with a phase of 180° and a resolution of 10 m per pixel, which take images every 5 days. MODIS captures images 46 times per year with a resolution of 500 m per pixel. Table 13.1 lists the satellite missions providing free imagery.

| Satellite | Instruments | Spatial resolution | Temporal resolution | Radiometric resolution |
|---|---|---|---|---|
| Sentinel-1 | Radar | 5–40 m (depends on acquisition mode) | 6 days (12 days per week with two satellites) | 1 dB |
| Sentinel-2 | Visible, NIR, SWIR, and coastal | 10 m (visible, NIR), 20 m (SWIR), 60 m (coastal) | 5 days (10 days, per week with two satellites) | 12-bit |
| Landsat-8 | Panchromatic, visible, NIR, SWIR, coastal, and thermal | 15 m (panchromatic), 20 m (visible, NIR, SWIR, and coastal), and 100 m (thermal) | 16 days | 12-bit |

### 13.2.2 CHALLENGES INVOLVED IN PROCESSING SATELLITE IMAGERY

The RGB images, which have only three channels used in general computer vision tasks, are relatively smaller as compared to satellite images with multiple bands ranging from tens to thousands. Furthermore, gathering ground truth data is time-consuming and costly. Similar spectral and feature values frequently correlate to different objects at various locations, making classification a difficult task.

## 13.3 CNNS

CNNs are dedicated networks that handle image-related tasks. A simple linear classifier is of the form:

```
yi = Wi xi + bi
```

where xi is the input (in the case of images, xi can be thought of as a flattened image vector), Wi is the weight matrix, bi is the bias, and yi is the output. In the case of semantic segmentation, yi represents the class label predicted for a particular pixel xi in the image. A nonlinear activation function, such as sigmoid, tanh, or ReLU (Rectified Linear Unit), can be fed the output of eq 13.1. Each layer in the neural network consists of multiple such nodes (or neurons). Multiple similar layers are placed on top of each other to form a multilayered neural network. To learn patterns in images, CNNs (Figure 13.2) use convolutional filters that traverse the image from left to right and top to bottom. Learning is performed layerwise through weight sharing in an end-to-end manner. The first layers learn fine features from the image, such as lines, curves, and edges, whereas the latter layers learn more abstract elements. Pooling layers are used in conjunction with convolution filters to broaden the receptive field at each deeper layer.

![](img/08e33f9814ed09d3c1bb11cd99f09e86_258_0.png)

FIGURE 13.2 A typical CNN architecture.

Source: Reprinted from Aphex34, https://creativecommons.org/licenses/by-sa/4.0

Following are the various steps performed in a typical CNN:

- Convolutions: Each convolutional layer is made up of h*w*d kernels (or filters), where h and w are the kernel's height and width, respectively, and d is the depth, which denotes the number of channels. While sliding across the width and height of the image, a kernel is convolved with a corresponding volume of the image. The sum of the elementwise dot product of the neurons in a kernel with the corresponding values in the input is the output of the convolution process.
- Nonlinearity functions: Nonlinearity activation functions, such as sigmoid, tanh, or ReLU, determine whether a neuron fires or not. For the most part, ReLU has been determined to be the most effective.1 As shown in eq 13.2 below, ReLU squashes negative input values to zero while allowing positive values to pass unchanged.

```
f(z) = max(0, z) (13.2)
```

where z is the ReLU unit's input.
- Pooling layers: The goal of pooling layers is to spatially downsample the input information. Maxpooling, average pooling, the L2 norm of a rectangle neighborhood, or a weighted average based on the distance to the central pixel are all examples of pooling.26
- Fully connected layers: These are the final set of layers in a CNN.
- Classifier: At the final output layer, the softmax function is used to estimate the input data’s class from many mutually exclusive classes. It assigns probabilities to different classes whose sum equals one. The cross-entropy loss function, which is the softmax function’s negative log-likelihood, is used here (eq 13.3):

```
$p(y = k|x_i) = e^{(s_k)} / \sum_j e^{(s_j)}$ \quad (13.3)
```

where “s” is the total score for a certain class.
- Regularization: Regularization is used in neural networks to prevent the model from overfitting the training data. Overfitting reduces the model’s capability to generalize well to new and unseen problem instances. Dropout27 is a commonly used regularization strategy wherein certain neurons are dropped randomly based on a probability. L² regularization is another widely used regularization approach.
- Training: A forward computation produces an output at the last layer during neural network training, and then an error or loss is backpropagated through the network to alter the network parameters to lessen the difference between the output produced and the actual output. This forward-pass and backpropagation operation is repeated until convergence or a set number of epochs are reached.
- Hyperparameters: The learning method, learning rate, minibatch size, weight initialization, regularization, and number of epochs are just a few of the hyperparameters that can be tweaked in a neural network.

The most prominent CNN models for image classification are AlexNet,1 VGGNet,28 and GoogleNet.29 They’ve served as the foundation for many semantic segmentation architectures.

## 13.4 SEMANTIC SEGMENTATION

Computer vision has been used to solve a variety of image classification, object recognition, and semantic segmentation challenges. The work of
