```
#> [1,]   3.465378
#> [2,]   24.752701
#> [3,] -108.911880
```

From the results, it can be seen that we got more or less the expected results. Setting a
hig learning rate, for example, 0.05. With this learning rate, the algorithm will converge
much faster. In my computer, at epoch 11 the loss was already 0.

![](bbox=[0.081, 0.301, 0.137, 0.347])

One practical thing to note is that if you make any changes in the compile() or fit()
functions you will have to run the code again that instantiates and defines the network.
This is because the object saves the current state including the learned weights.
If you run the fit() function again on a previously trained model, it will start with
t previously learned weights.

# 8.3 Classification with Neural Networks

Neural networks are trained iteratively by modifying their weights aiming to minimize the
loss function. When the network predicts real numbers, the MSE loss function is normally
used. For classification problem, the network should predict what is the most likely class
of k possible categories. To make a neural network work for classification problems, we
eed to introduce new elements to its architecture:

+   1. Add more units to the output layer.
2. Use a softmax activation function in the output layer.
3. Use average cross-entropy as the loss function.

Let's start with point 1 (add more units to the output layer). This means that the
number of classes is k, then the last layer needs to have k units, one for each class. That's
it! Figure 8.18 shows an example of a neural network with an output layer having 3 units.
Each unit predicts a score for each of the 3 classes. Let's call the vector of predicted scores
y'.

Point number 2 says that a softmax activation function should be used in the output layer.
When training the network