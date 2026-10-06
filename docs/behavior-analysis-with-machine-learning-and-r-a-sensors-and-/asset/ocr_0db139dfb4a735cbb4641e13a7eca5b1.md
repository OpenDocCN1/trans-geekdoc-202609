# CHAPTER 8. PREDICTING BEHAVIOR WITH DEEP LEARNING

# 8.7.1 Example 1

Let's create our CNN in Keras. For now, this CNN will not be trained but only its architecture will be defined. The objective is to understand the building blocks of the network. In the next section, we will build and train a CNN that detects smiles from image faces.

Our network will consist of 1 convolution layer, 1 max pooling layer, 1 fully connected hidden layer, and 1 output layer as if this a classification problem. The code to build such a network is shown below and the output of the summary() function in Figure 8.30.

```
library(keras)
model <- keras_model_sequential()
%
modellayer_conv_2d(filters = 4,
    kernel_size = c(3,3),
    padding = 'valid',
    activation = 'relu',
    input_shape = c(10,10,1)) %%
layer_max_pooling_2d(pool_size = c(2, 2)) %%
layer_flatten() %%
layer_dense(units = 32, activation = 'relu') %%
layer_dense(units = 2, activation = 'softmax')

summary(model)
```

The first convolution layer has 4 kernels of size 3x3 and a ReLU as the activation function. The padding is set to "valid" so no padding will be done. The input image has a size of 10x10x1 (height, width, depth). Then, we are applying max pooling with a window size of 2x2. Later, the output is flattened and fed into a fully connected layer with 32 units. Finally, the output layer is 2 units with a softmax activation for classification.

From the summary, if you look at the output of the first Conv2d layer it shows (None, 8, 4). The 'None' means that the number of input images is not fixed and will depend on the batch size. The next two numbers correspond to the height and width which are both 8. This is because the image was not padded and after applying the convolution operation on the original 10x10 height and width image, its dimensions are reduced to 8. The last number