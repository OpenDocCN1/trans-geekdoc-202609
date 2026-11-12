
## Average pooling

Average pooling is a type of pooling process that selects and provides the average value of the pixel from the feature map’s region scanned by the filter, but max-pooling provides the output as the most prominent feature of the feature map. The average pooling provides the average of the feature present in the filter scanned area. Suppose we have a feature map of size 4x4 obtained after the convolution operation, as shown in figure 4.90:

| 1 | 3 | 2 | 1 |
|---|---|---|---|
| 2 | 9 | 1 | 1 |
| 1 | 3 | 2 | 3 |
| 5 | 6 | 1 | 2 |

**Figure 4.90:** Feature or activation map

Let us assume that we have a stride length of 2 and a filter size of 2*2 and we want to calculate the padded feature map. So, we place a 2*2 filter on the feature map, as shown in figure 4.91, and calculate the average of all the values of the pixel within that region:

![](img/7e519fee1b702b91799cdf1664598392_291_0.png)

**Figure 4.91:** Average pooling of 2*2

Similarly, we calculate all pooled values by using the stride of 2, as shown in figure 4.92:

![](img/7e519fee1b702b91799cdf1664598392_292_0.png)

Figure 4.92: Pooled feature map after average pooling of 2*2 with a stride of two

## Fully connected layer

Fully connected layer, also known as FC layer, is an important component of CNN. FC layer drives the final output of the classification. It takes input in the form of pooled feature maps. It flattens the output from the previous layers and converts it into a single vector of different values, where each value represents the feature of the particular label.

For example, if the input image shows cat, then the features representing the fur or whiskers have high values of the probabilities.

Consider three pooled feature maps as shown in figure 4.93:

| 0.77 | 0.11 | 0.9 |
|---|---|---|
| 0.62 | 0.2 | 0.91 |
| 0.21 | 0.12 | 0.98 |

| 0.9 | 0.21 | 0.1 |
|---|---|---|
| 0.89 | 0.1 | 0.9 |
| 0.23 | 0.1 | 0.12 |

| 0.65 | 0.45 | 0.21 |
|---|---|---|
| 0.68 | 0.3 | 0.21 |
| 0.21 | 0.4 | 0.12 |

Figure 4.93: Pooled feature or activation maps.

Figure 4.94 shows the fully connected layer after the flattening:

![](img/7e519fee1b702b91799cdf1664598392_293_0.png)

Figure 4.94: Flattened feature or activation maps

Now, as we have discussed almost all the layers of the convolutional neural network, let us take an example of the detection of an image of dimensions (32 * 32 * 3) with the number “7” as shown in figure 4.95:

![](img/7e519fee1b702b91799cdf1664598392_294_0.png)

Figure 4.95: Image representing “7” of size (32 * 32 * 3)

Now, in the first convolution layer, we use six filters of size (5 * 5) and stride of 1 with no padding. So, applying the first convolution layer, we get the following output, as shown in figure 4.96:

![](img/7e519fee1b702b91799cdf1664598392_294_1.png)

Figure 4.96: Output of first convolutional layer

As we observe in figure 4.96, when we use six filters of size (5 * 5), we get the output as a feature map of dimension (28 * 28 * 6). Now, let us apply the pooling layer and use Max pooling of filter size (2 * 2) with a stride of 2 and no padding.

As we observe in figure 4.97, the output after applying the first pooling layer is of dimensions (14 * 14 * 6):

![](img/7e519fee1b702b91799cdf1664598392_294_2.png)

Figure 4.97: Output after applying Max Pooling Layer of filter size (2*2)

Now, in the second convolutional layer, when we use 16 filters of size (5 * 5), we get the output as a feature map of dimension (10 * 10 * 16) as shown in figure 4.98:

![](img/7e519fee1b702b91799cdf1664598392_295_0.png)

Now, let us apply the second layer of pooling, and again, we are using Max pooling of filter size (2 * 2) with a stride of 2 and no padding.

As we observe in figure 4.99, the output after applying the second pooling layer is the pooled feature map of dimensions (5 * 5 * 16):

![](img/7e519fee1b702b91799cdf1664598392_295_1.png)

So, after applying the second layer of pooling, we get the output of size (5 * 5 * 16) = 400. So, now, let us flatten the output by dividing it into 400 nodes, as shown in figure 4.100:

![](img/7e519fee1b702b91799cdf1664598392_295_2.png)

Now, let us build the first fully connected layer of size 120 nodes. We connect the 400 nodes of the flattening to the 120 nodes of the fully connected Layer 1, as shown in figure 4.101:

![](img/7e519fee1b702b91799cdf1664598392_296_0.png)

Figure 4.101: First fully connected layer

Let us assume that we use another fully connected layer of size 84 nodes. We connect the 120 nodes of the first fully connected layer to the 84 nodes of the fully connected Layer 2, as shown in figure 4.102:

![](img/7e519fee1b702b91799cdf1664598392_297_0.png)

Figure 4.102: Second fully connected layer

So, finally, we have 84 nodes that we can feed to a SoftMax unit output. When we have to do a number recognition, we must have 10 numbers as output. So, we have to use a Softmax of 10 outputs as follows:

```
Softmax = {0,1,2,3,4,5,6,7,8,9}
```

So, according to the highest probability, the neural network provides accurate output, as mentioned in figure 4.103:

![](img/7e519fee1b702b91799cdf1664598392_298_0.png)

Figure 4.103: Final output of convolutional neural network

So, let us brief up the preceding example using table 4.1 as follows:

| Layer | Activation Shape | Activation Size |
|---|---|---|
| Input | (32 * 32 * 3) | 3072 |
| Conv. Layer 1 | (28 * 28 * 6) | 4704 |
| Pooling Layer 1 | (14 * 14 * 6) | 1176 |
| Conv. Layer 1 | (10 * 10 * 16) | 1600 |
| Pooling Layer 2 | (5 * 5 * 16) | 400 |
| Fully Connected Layer 1 | (120 * 1) | 120 |
| Fully Connected Layer 2 | (84 * 1) | 84 |
| Output | (10 * 1) | 10 |

Table 4.1: Convolutional neural network parameters in figure 4.103

## Convolutional neural network with example (Implementation: How CNN works?)

We start with a simple classification problem where we have to predict whether this image has X or O. We have to train our CNN so that it does the right classification when a new object is shown to this. Figure 4.104 shows the problem. Figure 4.105 shows the spatial representation of X or O in the spatial domain. Figure 4.106 defines various possible spatial positions of X or O that are obtained using translation, scaling, and rotation. Figure 4.107 represents the problem of deciding the similarity between the two images. One way to find similarities between two images is by matching. So, finding the similarity between two images is basically a metric learning problem. If we want to find whether it is X or O, then it becomes a classification problem. At last, if we want that what is inside the image, then this is basically an object detection problem. Figure 4.108 represents the values of a particular pixel where a white intensity pixel is represented by 1, whereas a black intensity pixel is represented by -1. The X (cross) at the pixel values in figure 4.109 represents the region of the two images in figure 4.108 that are not matching. Figure 4.110 represents that the two images are not matching with each other. Convolutional networks (ConvNets) match the pixels of the image, as shown in figure 4.111. They match the regions of an image. Figure 4.112 represents the possible three matching patterns of X. Basically, these are called as convolutional filters, which are applied on the given image to generate activation maps to train the model:

Two Dimensional array of pixel

![](img/7e519fee1b702b91799cdf1664598392_299_0.png)

Figure 4.104: Simple classification problem

![](img/7e519fee1b702b91799cdf1664598392_300_0.png)

Figure 4.105: The spatial representation of “X” or “O” in spatial domain

![](img/7e519fee1b702b91799cdf1664598392_300_1.png)

Figure 4.106: Various possible spatial positions of “X” or “O”

![](img/7e519fee1b702b91799cdf1664598392_300_2.png)

Figure 4.107: Problem of deciding the similarity between the two images

![](img/7e519fee1b702b91799cdf1664598392_301_0.png)

Figure 4.108: Intensity representations [white (with value 1) and black (with value -1)]

![](img/7e519fee1b702b91799cdf1664598392_301_1.png)

Figure 4.109: Region of mismatch in figure 4.108.

![](img/7e519fee1b702b91799cdf1664598392_301_2.png)

Figure 4.110: Representation of mismatch between two images
