```
# Target user test set.
# This data is used to test the performance.
target.test <- target.data[-idxs],
```

```
# Save target.test labels in a separate variable.
target.test.y <- target$intlabel
```

```
# Save target.test pixels in a separate variable.
target.test.x <- as.matrix(target.test[,-c(301,302,303)])
```

We also need to normalize the data and reshape it into the actual image format since in its current form, the pixels are stored into 1-dimensional arrays. We learn the normalization parameters only from the train script and then use the normalize.reshape() function (in the same script file) to perform the actual normalization and formatting.

```
# Learn min and max values from train set for normalization.
maxv <- max(train.x)
minv <- min(train.x)
```

```
# Normalize and reshape. May take some minutes.
train.x <- normalize.reshape(train.x, minv, maxv)
target.adaptive.x <- normalize.reshape(target.adaptive.x, minv, maxv)
target.test.x <- normalize.reshape(target.test.x, minv, maxv)
```

Let's inspect how the structure of the final datasets like.

```
dim(train.x)
# [1] 6399 10 10 3
dim(target.adaptive.x)
# [1] 124 10 10 3
dim(target.test.x)
# [1] 124 10 10 3
```

Here, we see that the train set has 6399 instances (images). The adaptive and test sets both have 124 instances.