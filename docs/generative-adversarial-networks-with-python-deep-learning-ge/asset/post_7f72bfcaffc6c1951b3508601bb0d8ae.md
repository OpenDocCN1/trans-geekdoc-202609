
```
1, 2
Output = 3, 4
```

Listing 3.18: Example of an output matrix with a 1 × 1 stride.

With an output stride of (2,2), the 1 × 1 convolution requires the insertion of additional rows and columns into the input image so that the reads of the operation can be performed. Therefore, the input looks as follows:

```
1, 0, 2, 0
Input = 0, 0, 0, 0
       3, 0, 4, 0
       0, 0, 0, 0
```

Listing 3.19: Example of an input matrix with a 2 × 2 stride.

The model can then read across this input using an output stride of (2,2) and will output a 4 × 4 image, in this case with no change as our model weights have no effect by design:

```
1, 0, 2, 0
Output = 0, 0, 0, 0
        3, 0, 4, 0
        0, 0, 0, 0
```

Listing 3.20: Example of an output matrix with a 2 × 2 stride.

## 3.4.1 Worked Example Using the Conv2DTranspose Layer

Keras provides the transpose convolution capability via the Conv2DTranspose layer. It can be added to your model directly; for example:

```
...
# define model
model = Sequential()
model.add(Conv2DTranspose(...))
```

Listing 3.21: Example of defining a model with a Conv2DTranspose layer.

We can demonstrate the behavior of this layer with a simple contrived example. First, we can define a contrived input image that is 2 × 2 pixels, as we did in the previous section. We can use specific values for each pixel so that after the transpose convolutional operation, we can see exactly what effect the operation had on the input.

```
...
# define input data
X = asarray([[1, 2],
             [3, 4]])
# show input data for context
print(X)
```

Listing 3.22: Example of defining an input matrix for the model.

Once the image is defined, we must add a channel dimension (e.g. grayscale) and also a sample dimension (e.g. we have 1 sample) so that we can pass it as input to the model.

```
...
# reshape input data into one sample a sample with a channel
X = X.reshape((1, 2, 2, 1))
```

Listing 3.23: Example of reshaping the input matrix as an image input.

We can now define our model. The model has only the Conv2DTranspose layer, which takes 2 × 2 grayscale images as input directly and outputs the result of the operation. The Conv2DTranspose both upsamples and performs a convolution. As such, we must specify both the number of filters and the size of the filters as we do for Conv2D layers. Additionally, we must specify a stride of (2,2) because the upsampling is achieved by the stride behavior of the convolution on the input. Specifying a stride of (2,2) has the effect of spacing out the input. Specifically, rows and columns of 0.0 values are inserted to achieve the desired stride. In this example, we will use one filter, with a 1 × 1 kernel and a stride of 2 × 2 so that the 2 × 2 input image is upsampled to 4 × 4.

```
...
# define model
model = Sequential()
model.add(Conv2DTranspose(1, (1,1), strides=(2,2), input_shape=(2, 2, 1)))
# summarize the model
model.summary()
```

Listing 3.24: Example of defining a model with a Conv2DTranspose layer.

To make it clear what the Conv2DTranspose layer is doing, we will fix the single weight in the single filter to the value of 1.0 and use a bias value of 0.0. These weights, along with a kernel size of (1,1) will mean that values in the input will be multiplied by 1 and output as-is, and the 0 values in the new rows and columns added via the stride of 2 × 2 will be output as 0 (e.g. 1 × 0 in each case).

```
...
# define weights that do nothing
weights = [asarray([[[[1]]]]), asarray([0])]
# store the weights in the model
model.set_weights(weights)
```

Listing 3.25: Example of fixing the model weights.

We can then use the model to make a prediction, that is upsample a provided input image.

```
...
# make a prediction with the model
yhat = model.predict(X)
```

Listing 3.26: Example of making a prediction with the model.

The output will have four dimensions, like the input, therefore, we can convert it back to a 2 × 2 array to make it easier to review the result.

```
...
# reshape output to remove channel to make printing easier
yhat = yhat.reshape((4, 4))
# summarize output
print(yhat)
```

Listing 3.27: Example of interpreting the prediction from the model.

Tying all of this together, the complete example of using the Conv2DTranspose layer in Keras is provided below.

```
# example of using the transpose convolutional layer
from numpy import asarray
from keras.models import Sequential
from keras.layers import Conv2DTranspose
# define input data
X = asarray([[[1, 2],
              [3, 4]]])
# show input data for context
print(X)
# reshape input data into one sample a sample with a channel
X = X.reshape((1, 2, 2, 1))
# define model
model = Sequential()
model.add(Conv2DTranspose(1, (1,1), strides=(2,2), input_shape=(2, 2, 1)))
# summarize the model
model.summary()
# define weights that do nothing
weights = [asarray([[[[1]]]]), asarray([0])]
# store the weights in the model
model.set_weights(weights)
# make a prediction with the model
yhat = model.predict(X)
# reshape output to remove channel to make printing easier
yhat = yhat.reshape((4, 4))
# summarize output
print(yhat)
```

Listing 3.28: Example of defining a simple model using the Conv2DTranspose layer.

Running the example first creates and summarizes our 2 × 2 input data. Next, the model is summarized. We can see that it will output a 4 × 4 result as we expect, and importantly, the layer two parameters or model weights. One for the single 1 × 1 filter and one for the bias. Unlike the UpSampling2D layer, the Conv2DTranspose will learn during training and will attempt to fill in detail as part of the upsampling process. Finally, the model is used to upsample our input. We can see that the calculations of the cells that involve real values as input result in the real value as output (e.g. 1 × 1, 1 × 2, etc.). We can see that where new rows and columns have been inserted by the stride of 2 × 2, that their 0.0 values multiplied by the 1.0 values in the single 1 × 1 filter have resulted in 0 values in the output.

| Layer (type) | Output Shape | Param # |
|---|---|---|
| conv2d_transpose_1 (Conv2DTr | (None, 4, 4, 1) | 2 |

Total params: 2
Trainable params: 2
Non-trainable params: 0

```
[[1. 0. 2. 0.]
[0. 0. 0. 0.]
[3. 0. 4. 0.]
[0. 0. 0. 0.]]
```

Listing 3.29: Example output from defining a simple model using the Conv2DTranspose layer.

Recall that this is a contrived case where we artificially specified the model weights so that we could see the effect of the transpose convolutional operation. In practice, we will use a large number of filters (e.g. 64 or 128), a larger kernel (e.g. 3 × 3, 5 × 5, etc.), and the layer will be initialized with random weights that will learn how to effectively upsample with detail during training. In fact, you might imagine how different sized kernels will result in different sized outputs, more than doubling the width and height of the input. In this case, the padding argument of the layer can be set to 'same' to force the output to have the desired (doubled) output shape; for example:

```
...
# example of using padding to ensure that the output are only doubled
model.add(Conv2DTranspose(1, (3,3), strides=(2,2), padding='same', input_shape=(2, 2, 1)))
```

Listing 3.30: Example of defining the Conv2DTranspose layer with same padding.

## 3.4.2 Simple Generator Model With the Conv2DTranspose Layer

The Conv2DTranspose is more complex than the UpSampling2D layer, but it is also effective when used in GAN models, specifically the generator model. Either approach can be used, although the Conv2DTranspose layer is preferred, perhaps because of the simpler generator models and possibly better results, although GAN performance and skill is notoriously difficult to quantify. We can demonstrate using the Conv2DTranspose layer in a generator model with another simple example.

In this case, our little GAN generator model must produce a 10 × 10 image and take a 100-element vector from the latent space as input, as in the previous UpSampling2D example. First, a Dense fully connected layer can be used to interpret the input vector and create a sufficient number of activations (outputs) that can be reshaped into a low-resolution version of our output image, in this case, 128 versions of a 5 × 5 image.

```
...
# define model
model = Sequential()
# define input shape, output enough activations for 128 5x5 images
model.add(Dense(128 * 5 * 5, input_dim=100))
# reshape vector of activations into 128 feature maps with 5x5
model.add(Reshape((5, 5, 128)))
```

Listing 3.31: Example of defining the base activations for a generator model.

Next, the 5 × 5 feature maps can be upsampled to a 10 × 10 feature map. We will use a 3 × 3 kernel size for the single filter, which will result in a slightly larger than doubled width and height in the output feature map (11 × 11). Therefore, we will set the padding argument to 'same' to ensure the output dimensions are 10 × 10 as required.
