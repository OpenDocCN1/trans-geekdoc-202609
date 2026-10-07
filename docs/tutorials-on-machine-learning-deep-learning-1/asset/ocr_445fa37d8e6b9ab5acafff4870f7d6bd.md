And we obtain our next layer composed of all these pooled-feature-maps and that is called the Polling Layer.

This will reduce the complexity and the time execution without the losing too much information because we are using maxpooling

Using max-pooling we are keeping track of the most-important features of the image, that contained the high features detected from some specific features in the input image.

| 0 | 0 | 0 | 0 | 0 |
|---|---|---|---|--|
| 0 | 1 | 0 | 0 | 1 |
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 | 0 |
| 1 | 0 | 0 | 1 | 0 |
| 0 | 1 | 1 | 1 | 0 |
| 0 | 0 | 0 | 0 | 0 |

![](bbox=[0.368, 0.172, 0.853, 0.363])

Remember, we apply this max pooling to reduce the number of nodes for the Flatten step, it is some kind of reduction of independent variables.

+   Here we are actually reducing the size of these feature maps, we'll get to too large flattened one-dimensional vector (which will be huge) for the Full Connection step.

+   If we don't reduce the size of these feature maps, we'll get to too large flattened one-dimensional vector and then we will get too many nodes in the fully connected layers in the NN part and therefore our model will be highly compute-intensive.

+   So we don't lose the spatial structure information, however we don't lose the complexity and make it less compute-intensive.

But at the same time, we managed to reduce the time complexity and make it less compute-intensive.

![](bbox=[0.128, 0.555, 0.853, 0.696])

Creating Pooling-Layer: We'll apply same add() method to our cnn_classifier to add a pooling-layer. Inside add() we use MaxPooling2D:

+   pool_size: We are gonna use pool_size = (2, 2). Most of the time we use a 2-by-2 pool_size when we apply max pooling on our feature maps. Because we don't lose the information. We're still precise on where we have the High numbers (max-pooling) in the feature maps.

Basically adding linear will reduce the size of your feature maps, and pooled-feature-map's size will be half of original-feature-map's size.

```
# step 2 : Pooling - Layer
cnn_classifier.add(MaxPooling2D(pool_size=(2, 2)))
```

So we reduced the complexity of our model without reducing its performance.