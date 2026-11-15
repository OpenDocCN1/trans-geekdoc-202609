![](bbox=[0.195, 0.075, 0.58, 0.225])

Note that since we have 24 × 24 neurons output from the convolutional layer, after pooling we have 12 × 12 neurons.

As mentioned above, the convolutional layer usually involves more than a single feature map. We apply max-pooling to each feature map separately. So if there were three feature maps, the combined convolutional and max-pooling layers would look like:

![](bbox=[0.16, 0.39, 0.605, 0.515])

We can think of max-pooling as a way for the network to ask whether a given feature is found anywhere in a region of the image. It then throws away the exact positional information. The intuition is that once a feature has been found, its exact location isn't as important as its rough location relative to other features. A big benefit is that there are many fewer pooled features, and so this helps reduce the number of parameters needed in later layers.

Max-pooling isn't the only technique used for pooling. Another common approach is known as L2 pooling. Here, instead of taking the maximum activation of a 2 × 2 region of neurons, we take the square root of the sum of the squares of the activations in the 2 × 2 region. While the details are different, the intuition is similar to max-pooling: L2 pooling is a way of condensing information from the convolutional layer. In practice, both techniques have been widely used. And sometimes people use other types of pooling operation. If you're really trying to optimize performance, you may use validation data to compare several different approaches to