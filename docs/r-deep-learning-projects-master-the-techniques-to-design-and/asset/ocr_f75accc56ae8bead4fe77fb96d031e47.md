Let's look at the reconstructed image of a typical element of the test set:

![](bbox=[0.36, 0.15, 0.63, 0.3])

Reconstructed image by our autoencoder.

How does it compare to the original image, before reconstruction? Let’s take a look:

```
y_test[1]
image(255*X_test[1,,], col=gray.colors(3) )
```

![](bbox=[0.38, 0.44, 0.61, 0.54])

Original image.

Overall, not bad for a 24.5 compression! Clearly there is a lot to be improved, but we can already see the potential of autoencoders to learn intrinsic features of the data.

# Outlier detection in MNIST

All right, so admittedly our previous application has nothing to do with fraud or outlier detection so far. We can do a small modification on the previous setup to show how a similar framework works. For this, let’s assume that the number 7 is an outlier class and we will try to identify it from the result of our normal numbers: 0, 1, 2, 3, 4, 5, 6, 8, 9.

We will train the autoencoder on the normal dataset and then apply it to the test set. The aim will be to abstract as many features of the normal situation as possible. This requires knowledge of the normal situation, which translates into availability of labelled data and hence, it is an ideal scenario, for many practical applications, for instance credit card fraud or intrusion detection, we sometimes (or rather often) lack such labeled data.