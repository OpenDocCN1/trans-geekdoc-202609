
So we have to make sure that our NN has a property "spatial invariance" meaning that it doesn't care where the features are i.e. the NN doesn't have to care if the features are a bit tilted, different in texture, if the features are a bit clearer or a bit apart relative to each other.

If the feature itself is a bit distorted neural network has to have some level of flexibility to be able to find that feature and is what it POOLING is all about.

## 9.3.2 Max Pooling

Consider following as our feature map (already deconvolution). Now we're going to apply pooling (also called Down-Sampling). There are different types of pooling:

- Max pooling: The maximum pixel value of the batch is selected.
- Min pooling: The minimum pixel value of the batch is selected.
- Average pooling: The average value of all pixels in the batch is selected.
- Sum Pooling: This is a variation of the Max pooling. Here, instead of average or max value, the sum of all the pixels in the chosen region is calculated.

Here we'll apply Max-Pooling:

| 0 | 1 | 0 | 0 | 0 |
|---|---|---|---|---|
| 0 | 1 | 1 | 1 | 0 |
| 1 | 0 | 1 | 2 | 1 |
| 1 | 4 | 2 | 1 | 0 |
| 0 | 0 | 1 | 2 | 1 |

Max Pooling

| | |
|--|--|
| | |
| | |
| | |
| | |

Pooled Feature Map

Feature Map

Max-pooling: We take a box of 2 x 2 pixels. And Select stride of 2 (if you want overlapping pooling then select stride size of 1). However, you can choose any size of box and place it in the top left hand corner and you find the maximum value in that box and you record only that max value.

| 0 | 1 | 0 | 0 | 0 |
|---|---|---|---|---|
| 0 | 1 | 1 | 1 | 0 |
| 1 | 0 | 1 | 2 | 1 |
| 1 | 4 | 2 | 1 | 0 |
| 0 | 0 | 1 | 2 | 1 |

| | |
|--|--|
| | |
| | |
| | |
| | |

Max Pooling

 Pooled Feature Map

Feature Map

| 0 | 1 | 0 | 0 | 0 |
|---|---|---|---|---|
| 0 | 1 | 1 | 1 | 0 |
| 1 | 0 | 1 | 2 | 1 |
| 1 | 4 | 2 | 1 | 0 |
| 0 | 0 | 1 | 2 | 1 |

| 1 | 1 |
|--|--|
| | |
| | |

| 0 | 1 | 0 | 0 | 0 |
|---|---|---|---|---|
| 0 | 1 | 1 | 1 | 0 |
| 1 | 0 | 1 | 2 | 1 |
| 1 | 4 | 2 | 1 | 0 |
| 0 | 0 | 1 | 2 | 1 |

| 1 | 0 | 0 |
|--|--|--|
| | | |
| | |

Feature Map

Pooled Feature Map

Feature Map

Pooled Feature Map

Max Pooling

*

## Max Pooling

| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 2 | 1 |
| 1 | 4 | 2 | 0 |
| 0 | 0 | 2 | 1 |

| 1 | 1 | 0 |
| 4 | |

| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 2 | 1 |
| 1 | 4 | 2 | 0 |
| 0 | 0 | 2 | 1 |

## Max Pooling

| 1 | 1 | 0 |
| 4 | 2 |

Pooled Feature Map

Feature Map

Pooled Feature Map

| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 1 |
| 1 | 4 | 1 | 0 |
| 0 | 0 | 2 | 1 |

## Max Pooling

| 1 | 1 | 0 |
| 4 | 2 | 1 |

| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 1 |
| 1 | 4 | 1 | 0 |
| 0 | 0 | 2 | 1 |

## Max Pooling

| 1 | 1 | 0 |
| 4 | 2 | 1 |

```
0
```

Pooled Feature Map

Feature Map

Pooled Feature Map

| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 2 | 1 |
| 1 | 4 | 2 | 0 |
| 0 | 0 | 1 | 1 |

## Max Pooling

| 1 | 1 | 0 |
| 4 | 2 | 1 |

| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 1 |
| 1 | 4 | 1 | 0 |
| 0 | 0 | 1 | 1 |

## Max Pooling

| 1 | 1 | 0 |
| 4 | 2 | 1 |

| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 1 |
| 1 | 4 | 1 | 0 |
| 0 | 0 | 1 | 1 |

## Max Pooling

| 1 | 1 | 0 |
| 4 | 2 | 1 |

Feature Map

Pooled Feature Map

Feature Map

Pooled Feature Map

Here we're selecting a stride of two and this size is commonly used. After repeating the process we record that values shown above. Following things:

- i. Preserving the features: First of all were still able to preserve the features, the maximum numbers represents the features. These large numbers in feature map represent where you found the similarity to a feature.
- ii. We're introducing spatial invariants: Because we are taking the maximum of pixels we are gaining spatial invariance. For example: different version of image (rotated and squashed) or other position with Pooled-Map
- iii. Reducing the size of data: We're reducing the size by 75% which is really going to help us in terms of Processing By pooling these features we are getting rid of 75% of the information that is not the feature by using max pooling of 2x2
- iv. Preventing overfitting: Another benefit of pooling is that we are reducing the number of parameters. We're reducing 75% as we go into the Final Layers of the neural network and we are preventing overfitting (i.e. model doesn't get dependent on train images). It is a very important benefit of pooling that we are removing information because our model might be able to overfit that. It's important to see the exact features that are still keeping in our eyes. This sense for neural networks by eliminating the unnecessary information.
- Max pooling (Additional Readings): There's lots of types of pooling and size of 2 pixels box size. On that note I'd like to introduce this lovely research paper 'Evaluation Of Pooling Operations in Convolutional Architectures For Recognition' by Scherer from University of Bonn. They talk about subsampling which is basically average. In average pooling, instead of taking the max value we make the average.

## Additional Reading: Evaluation of Pooling Operations in Convolutional Architectures for Object Recognition By Dominik Scherer et al. (2010) Link: http://ais.uni-bonn.de/papers/icann2010_maxpool.pdf

## Let's recap what we have done so far.

- [1]. Convolution and [2]. Pooling

| 0 | 0 | 0 | 0 | 0 |
| 1 | 0 | 0 | 0 | 1 |
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 |
| 0 | 0 | 0 | 0 | 0 |

Convolution

img/0aa092657a6eb1b9f2dd65bbb79055a3_282_0.png

Input Image

Convolutional Layer

Pooling Layer

Example: There is a fun example of CNN. Follow the link (the may be deleted now).

img/0aa092657a6eb1b9f2dd65bbb79055a3_282_1.png

And basically this is exactly what we're doing but we can visualize it here (kind of). So here we draw a number, say we draw number 4, and in this tool will put the number four at the bottom (that's what we drew).

After that, the 1st row is the convolution step, the 2nd row is the Pooling step (also called Down-Sampling). When it's applied pooling it's reducing the size and you can see here that pooled image has same features that having just less information.

img/0aa092657a6eb1b9f2dd65bbb79055a3_283_0.png

It also gives the 2nd guess.

img/0aa092657a6eb1b9f2dd65bbb79055a3_283_1.png

We can also see the pixels of the image how it is reduced. And we see the Stride size (pointy thing). The 3rd row is convolution layer of the previous Pooling layer. 4th row is another Pooling. Last two rows are flattened-layer.

img/0aa092657a6eb1b9f2dd65bbb79055a3_284_0.png

## 9.3.3 Flattening

After we get Pooled Feature Map (in pooling) we're going to flatten it into a column. Basically row by row we put 2-D matrix into 1-D vector. This will be input for ANN.

img/0aa092657a6eb1b9f2dd65bbb79055a3_284_1.png

## 9.3.4 Full Connection

In this step we are adding a Artificial Neural Network (ANN) to our Convolutional Network (CNN).

- So we've got the input-layer, fully-connected-layer, and output-layer. In ANN we used to call them "Hidden-Layers" but in CNN we call them "fully-connected-layer"
- Because, inside we have hidden layers but at the same time they're more specific type of hidden layers that are fully connected.
- In ANN, hidden letters don't need to be fully connected. But in CNN layers are fully connected, hence called fully-layer.

img/0aa092657a6eb1b9f2dd65bbb79055a3_285_0.png

img/0aa092657a6eb1b9f2dd65bbb79055a3_285_1.png

- Above is a very simplified example of ANN. The main purpose of this ANN is to combine our features into more attributes that predicts the Classes even better. Here the column or vector of flattened-layer is passed into the Input Layer.
- In our vector of flattened-layer we have some features encoded in the values in that vector. Those features can already predict what we're looking at, for instance, whether it's a Dog or a Cat.
- But at the same time the ANN dealing with features and coming up with new attributes and combining attributes together to get better prediction.
