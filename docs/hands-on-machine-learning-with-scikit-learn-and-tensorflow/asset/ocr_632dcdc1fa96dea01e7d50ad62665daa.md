Using loss=sparse_categorical_crossentropy is equivalent to loss=keras.losses.sparse_categorical_crossentropy. Similarly, optimizer="sgd" is equivalent to optimizer.keras.SGD() and metrics=['accuracy'] is equivalent to metrics=[keras.metrics.sparse_categorical_accuracy] (when using this loss). We will use many other losses, optimizers and metrics in this book, but for the full lists see https://keras.io/losses/, https://keras.io/optimizers/ and https://keras.io/metrics.

![](bbox=[0.169, 0.087, 0.239, 0.163])

This requires some example. First, we use the "sparse_categorical_crossentropy" because we have sparse labels (i.e., for each instance there is just a class index, from 0 to 9 in this case), and the classes are exclusive. If we have one target probability for each instance (such as one-hot vectors, e.g. [0., 0., 0., 1., 0., 0., 0., 0., 0.]) to represent class 3), then we would need to use the "categorical_crossentropy" loss. If we were doing binary classification (with one or more binary labels), then we would use the "sigmoid" (i.e., logistic) activation function in the output layer instead of the "softmax" activation function, and we would use the "binary_crossentropy" loss.

If you want to convert sparse labels (i.e., class indices) to one-hot vector labels, you can use the keras.utils.to_categorical() function. Or the other way round, you can just use the np.max(axis=1).

![](bbox=[0.169, 0.446, 0.239, 0.522])

Secondly, the optimizer, "sgd" simply means that we will train the model using simple Stochastic Gradient Descent. In other words, Keras will perform the backpropagation algorithm described earlier (i.e., reverse-mode autodiff + Gradient Descent). We will discuss more efficient optimizers in Chapter 11 (they improve the Gradient Descent part, not the autodiff).

Finally, this is a classifier, it will be useful to measure its "accuracy" during training and evaluation.

# Training and Evaluating the Model

Now the model is ready to be trained. For this we simply need to call its fit() method. We pass the input features (X_train) and the classes (y_train), as well as the number of epochs to train (or else it would default to 1, which would definitely not be enough to converge to a good solution). We also pass a validation set loss and the extra metrics on this set at the end of each epoch, which is very useful to see how well the model performs: if the performance on the training set is much better than on the validation set, your