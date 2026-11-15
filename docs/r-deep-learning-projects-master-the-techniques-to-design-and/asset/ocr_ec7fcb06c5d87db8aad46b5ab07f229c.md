Now we see where its name TensorFlow is derived from: Tensors flowing in networks.

By now, the installation of the core Keras library as well as the TensorFlow backend is done. We continue our Keras-based solution for traffic signs classification.

First, prepare the input data for Keras modeling by reshaping the training and testing feature matrix:

```
```
> x_train <- data_train.x
> dim(x_train) <- c(nrow(data_train.x), 32, 32, 1)
> x_test <- data_test.x
> dim(x_test) <- c(nrow(data_test.x), 32, 32, 1)
```
```

Again, the input pixels are already of values ranging from 0 to 1, so we do not need to perform any rescaling.

We also convert training and testing target vectors (integers from 0 to 42) into a binary class matrix (one-hot encoded) as required by the Keras classification models:

```
```
> y_train <- to_categorical(data_train.y, num_classes = 43)
> y_test <- to_categorical(data_test.y, num_classes = 43)
```
```

Before we start modeling, there is a trick for obtaining reproducible results in Keras in R. It is specifying a random seed before development of a model using the following function:

```
```
> use_session_with_seed(42)
```
```

It takes all measures known to ensure reproducible results from Keras sessions.

Time to define the model after data preparation!

We begin by initializing the Keras sequential model as follows:

```
```
> model <- keras_model_sequential()
```
```