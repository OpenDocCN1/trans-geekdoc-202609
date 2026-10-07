Stride: Steps at which we're moving this filter is called by the stride. So if we have a stride of one pixel, Stride is a component of CNN, or neural networks tuned for the Compression of images and Video data. Stride is a parameter of the neural network's filter that modifies the amount of movement over the image or video. For example, if a network's stride is set to 1, the filter will move one pixel, or unit; the size of the filters affects the encoded output volume, stride is often set to a whole integer, rather than a fraction or decimal.

# 7 x 7 Input Volume

# 5 x 5 Output Volume

![](bbox=[0.233, 0.133, 0.673, 0.269])

Imagine a convolutional neural network is taking an image and analyzing the content. If the filter size is 3 pixels, the contained nine pixels will be converted down to 1 pixel in the output layer. Naturally, the stride, or movement, is increased, the resulting output will be smaller.

Feature map: The image on the right is called a feature map also called convolved feature can also be called the activation map. When you apply convolution operator to something, it doesn't become convoluted it becomes convolved.

| 0 | 0 | 0 | 0 | 0 | | | 0 | 1 | 0 | 0 |
|---|---|---|---|---|---|---|---|---|---|---||
| 1 | 0 | 0 | 0 | 1 | 0 | | 0 | 3 | 1 | 1 |
| 0 | 0 | 0 | 0 | 0 | | | 1 | 4 | 2 | 1 |
| | | | | | | = | 1 | 0 | 2 | 1 |
| 0 | 0 | 0 | 1 | 0 | 0 | | | 0 | 2 | 1 |
| 1 | 0 | 0 | 0 | 1 | 0 | | | | | |
| 0 | 0 | 1 | 1 | 0 | 0 | | | | | |
| 0 | 0 | 0 | 0 | 0 | 0 | | 0 | 1 | 1 |

# Input Image

# Feature
Detector

# Feature Map

Here we've actually reduced the size of the image. If you have a stride of one you can see the image a bit, but if you have stride of two it is going to reduce more, the feature-map is going to be even smaller.

The purpose of this whole step is to make the image smaller, so that, it'll be easier & faster to process it. Therefore feature detectors will reduce the size of the image and feature stride of two is actually beneficial.

Information loss: Some we are losing because we have less values in resulting matrix. But at the same time the purpose of the feature detector is to detect certain features in that parts of the image that are integral.

For instance if you think about this way: the feature detector has a certain pattern on it, the highest number in your feature map is when pattern matches. As in case it is 4 the highest value, feature detector fully matches.

It helps us to focus on the features, for as detector 'Cheetah' will like its 'eye mark'. We don't consider all of the pixels.

Multiple FEATURE MAPs with DIFFERENT FILTERS/FEATURE-DETECTOR: For our input image, and we create multiple feature maps because we use different filters/feature-detector. That another way that we preserve some of the information. (Kind of extracting features).

Here we don't just have one feature map. Basically we want to detect features. Each layer has its own feature map for certain features.