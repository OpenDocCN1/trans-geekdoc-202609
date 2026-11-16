7 tps://medium.com/@cxu24/why-dimensionality-reduction-is-important-dd60b5611543.
8 tps://towardsdatascience.com/preventing-deep-neural-network-from-verfitting-953458db800a.
9 tps://towardsdatascience.com/deep-learning-3-more-on-cnns-andling-overfitting-2bd5d99abe5d.
0 tps://www.kdnuggets.com/2015/04/preventing-overfitting-neural-etworks.html.

igher dimensionality also increases (and sometimes explodes) computation time. If you're performing the deep learning on CPUs rather than GPUs or TPUs, the training could become intolerably slow.

# Adding a Pooling Layer

To reduce overfitting and computation time, a convolution layer is often followed by one or more layers that reduce the dimensionality of the convolution layer's output. A pooling layer compresses (or down-samples) the results by discarding features, which helps make the model more general. The most common pooling technique is called max pooling, which examines a 2-by-2 square of features and keeps only the maximum feature. To understand pooling, let's once again assume a 6-by-6 set of features. In the following diagram, the numeric values in the 6-by-6 square represent the features that we wish to compress and the 2-by-2 blue square in position 1 represents the initial pool of features to examine:

![](bbox=[0.17, 0.52, 0.88, 0.79])

The max pooling layer first looks at the pool in position 1 above, then outputs the maximum feature from that pool—9 in our diagram. Unlike convolution, there's no overlap between pools. The pool moves by its width—for a 2-by-2 pool, the stride is 2. For the second pool, represented by the orange 2-by-2 square, the layer outputs 7. For the third pool, the layer outputs 9. Once the pool reaches the right edge, the pooling layer moves the pool down by its height—2 rows—then continues from left-to-right. Because every group of four features is reduced to one, 2-by-2 pooling compresses the number of features by 75%.