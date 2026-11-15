After preparing the training and testing set, we structure our CNN model as follows:

![](bbox=[0.105, 0.155, 0.895, 0.41])

The network starts with the first set of convolutional layers, the ReLu nonlinear layer and the pooling layer. Here we use 32 5*5 convolutional filters and a 2*2 max pooling filter:

```
> require(mxnet)
> data <- mx.symbol.Variable("data")
> # first convolution
> conv1 <- mx.symbol.Convolution(data=data, kernel=c(5, 5),
                                  num_filter=32)
> act1 <- mx.symbol.Activation(data=conv1, act_type="relu")
> pool1 <- mx.symbol.Pooling(data=act1, pool_type="max",
                             +         kernel=c(2, 2), stride=c(2, 2))
```

It follows with the second set of convolutional, Relu nonlinear and pooling layer, where 64 5*5 convolutional filters and 2*2 max pooling filter are used:

```
> # second convolution
> conv2 <- mx.symbol.Convolution(data=pool1, kernel=c(5, 5),
                                  num_filter=64)
> act2 <- mx.symbol.Activation(data=conv2, act_type="relu")
> pool2 <- mx.symbol.Pooling(data=act2, pool_type="max",
                             +         kernel=c(2, 2), stride=c(2, 2))
```

Now that we've extracted rich representations of the input images by detecting edges, curves, and shapes, we move on to the fully connected layers. But before doing so, we need to flatten the resulting feature maps from the previous convolution layers:

```
> flatten <- mx.symbol.Flatten(data=pool2)
```