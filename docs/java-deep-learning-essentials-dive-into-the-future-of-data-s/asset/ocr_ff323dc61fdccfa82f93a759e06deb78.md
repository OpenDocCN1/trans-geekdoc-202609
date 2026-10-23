```
classifier.train(train_X_minibatch[batch], train_T_minibatch[batch], minibatchSize, learningRate);
}
learningRate *= 0.95;
}
```

Here, the learning rate gradually decreases so that the model can converge. Now, for the actual training train method, you can briefly divide it into two parts, as follows:

+   1. Calculate the gradient of w and b using the data from the mini-batch.
+   2. Update w and b with the gradients:

```
// 1. calculate gradient of W, b
for (int n = 0; n < minibatchSize; n++) {

double[] predicted_Y_ = output(X[n]);

for (int j = 0; j < nOut; j++) {
	dY[n][j] = predicted_Y_[j] - T[n][j];

for (int i = 0; i < nIn; i++) {
	grad_W[j][i] += dY[n][j] * X[n][i];
}

grad_b[j] += dY[n][j];
}
}

// 2. update params
for (int j = 0; j < nOut; j++) {
for (int i = 0; i < nIn; i++) {
W[j][i] -= learningRate * grad_W[j][i] / minibatchSize;
}
b[j] -= learningRate * grad_b[j] / minibatchSize;
}

return dY;
```

At the end of the train method, return dY, the error value of the predicted data and the correct data is returned. This is not mandatory for logistic regression itself but it is necessary in the machine learning and the deep learning algorithms introduced later.

Next up for the training is the test. The process of performing the test doesn't really change from the one for perceptrons.