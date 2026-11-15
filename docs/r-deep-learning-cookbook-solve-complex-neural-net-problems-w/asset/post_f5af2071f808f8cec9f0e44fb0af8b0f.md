
## Data Representation Using Autoencoders

This chapter will introduce unsupervised applications of deep learning using autoencoders. In this chapter, we will cover the following topics:

- Setting up autoencoders
- Data normalization
- Setting up a regularized autoencoder
- Fine-tuning the parameters of the autoencoder
- Setting up stacked autoencoders
- Setting up denoising autoencoders
- Building and comparing stochastic encoders and decoders
- Learning manifolds from autoencoders
- Evaluating the sparse decomposition

### Introduction

Neural networks aim to find a non-linear relationship between input X with output _y_, as _y=f(x)_. An autoencoder is a form of unsupervised neural network which tries to find a relationship between features in space such that _h=f(x)_, which helps us learn the relationship between input space and can be used for data compression, dimensionality reduction, and feature learning.

An autoencoder consists of an encoder and decoder. The encoder helps encode the input x in a latent representation y, whereas a decoder helps converts back the y to x. Both the encoder and decoder possess a similar representation of form.

Here is a representation of a one layer autoencoder:

```
h = f(x) = \sigma(W_e^T X + b_e)

\tilde{X} = f(h) = \sigma(W_d^T h + b_d)
```

The encoder encodes input X to h in a hidden layer, whereas the decoder helps to attain the original data from encoded output h. The matrices We and Wd represent the weights of the encoder and decoder layers, respectively. The function f is the activation function.

An illustration of an autoencoder is shown in the following diagram:

![](img/88a9c35e3059565190fbb6413f1ca217_121_0.png)

The constraints in the form of nodes allows the autoencoder to discover interesting structures within the data. For example, in the encoder in the preceding diagram, the five-input dataset must pass through three-node compression to get an encoded value h. The Encoded Output layer of an encoder can have a dimensionality that is the same, lower, or higher than the input/output Decoded Output layer. The Encoded Output layer with a fewer number of nodes than the input layer is referred to as an under-complete representation, and can be thought of as data compression transforming data into low-dimensional representation.

An Encoded Output layer with a larger number of nodes than the input layer is referred to as an over-complete representation and is used in a sparse autoencoder as a regularization strategy. The objective of an autoencoder is to find y, capturing the main factors along the variation of data, which is similar to Principal Component Analysis (PCA), and thus can be used for compression as well.

### Setting up autoencoders

There exist a lot of different architectures of autoencoders distinguished by cost functions used to capture data representation. The most basic autoencoder is known as a vanilla autoencoder. It's a two-layer neural network with one hidden layer the same number of nodes at the input and output layers, with an objective to minimize the cost function. The typical choices, but not limited to, for a loss function are mean square error (MSE) for regression and cross entropy for classification. The current approach can be easily extended to multiple layers, also known as multilayer autoencoder.

The number of nodes plays a very critical role in autoencoders. If the number of nodes in the hidden layer is less than the input layer then an autoencoder is known as an under-complete autoencoder. A higher number of nodes in the hidden layer represents an over-complete autoencoder or sparse autoencoder.

The sparse autoencoder aims to impose sparsity in the hidden layer. This sparsity can be achieved by introducing a higher number of nodes than the input in the hidden layer or by introducing a penalty in the loss function that will move the weights for the hidden layer toward zero. Some autoencoders attain the sparsity by manually zeroing out the weight for nodes; these are referred to as K-sparse autoencoders. We will set up an autoencoder on the occupancy dataset discussed in Chapter 1, Getting Started. The hidden layer for the current example can be tweaked around.

### Getting ready

Let's use the Occupancy dataset to set up an autoencoder:

- Download the Occupancy dataset as described in Chapter 1, Getting Started
- TensorFlow installation in R and Python

### How to do it...

The current occupancy dataset as described in Chapter 1, Getting Started, is used to demonstrate the autoencoder setup in R using TensorFlow:

1. Set up the R TensorFlow environment.
2. The load_occupancy_data function can be used to load the data by setting the correct working directory path using setwd:

```
# Function to load Occupancy data
load_occupancy_data<-function(train) {
xFeatures = c("Temperature", "Humidity", "Light", "CO2",
"HumidityRatio")
yFeatures = "Occupancy"
if(train) {
occupancy_ds <-
as.matrix(read.csv("datatraining.txt",stringsAsFactors = T))
} else {
occupancy_ds <-
as.matrix(read.csv("datatest.txt",stringsAsFactors = T))
}
occupancy_ds<-apply(occupancy_ds[, c(xFeatures, yFeatures)], 2,
FUN=as.numeric)
return(occupancy_ds)
}
```

3. The train and test occupancy dataset can be loaded to the R environment with the following script:

```
occupancy_train <-load_occupancy_data(train=T)
occupancy_test <- load_occupancy_data(train = F)
```

### Data normalization

**Data normalization** is a critical step in machine learning to bring data to a similar scale. It is also known as feature scaling and is performed as data preprocessing.

The correct normalization is very critical in neural networks, else it will lead to saturation within the hidden layers, which in turn leads to zero gradient and no learning will be possible.

### Getting ready

There are multiple ways to perform normalization:

- **Min-max standardization**: The min-max retains the original distribution and scales the feature values between [0, 1], with 0 as the minimum value of the feature and 1 as the maximum value. The standardization is performed as follows:

  $$x' = \frac{x - \min(x)}{\max(x) - \min(x)}$$

  Here, $x'$ is the normalized value of the feature. The method is sensitive to outliers in the dataset.

- **Decimal scaling**: This form of scaling is used where values of different decimal ranges are present. For example, two features with different bounds can be brought to a similar scale using decimal scaling as follows:

  $x'=x/10^j$

- **Z-score**: This transformation scales the value toward a normal distribution with a zero mean and unit variance. The Z-score is computed as:

  $Z=(x-\mu)/\sigma$

Here, \(\mu\) is the mean and \(\sigma\) is the standard deviation of the feature. These distributions are very efficient for a dataset with a Gaussian distribution.

All the preceding methods are sensitive to outliers; there are other more robust approaches for normalization that you can explore, such as **Median Absolute Deviation** (**MAD**), tanh-estimator, and double sigmoid.

### Visualizing dataset distribution

Let's look at the distribution of features for the occupancy data:

```
> ggpairs (occupancy_train$data[, occupancy_train$xFeatures])
```

![](img/88a9c35e3059565190fbb6413f1ca217_125_0.png)

The figure shows that the features have linear correlations and the distributions are non-normal. The non-normality can be further validated using the Shapiro-Wilk test, using the `shapiro.test` function from R. Let's use min-max standardization for the occupancy data.

### How to do it...

1. Perform the following operation for data normalization:

```
minmax.normalize<-function(ds, scaler=NULL) {
if(is.null(scaler)) {
for(f in ds$xFeatures) {
scaler[[f]]$minval<-min(ds$data[, f])
scaler[[f]]$maxval<-max(ds$data[, f])
ds$data[, f] <- (ds$data[, f] -
scaler[[f]]$minval) / (scaler[[f]]$maxval-scaler[[f]]$minval)
}
ds$scaler <- scaler
} else {
for (f in ds$xFeatures) {
ds$data[, f] <- (ds$data[, f] -
scaler[[f]]$minval) / (scaler[[f]]$maxval-scaler[[f]]$minval)
}
}
return(ds)
}
```
