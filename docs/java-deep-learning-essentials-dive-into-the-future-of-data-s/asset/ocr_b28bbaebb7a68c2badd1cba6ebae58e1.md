Multi-class logistic regression is used in the output layer and the delta is then backpropagated to the hidden layer:

```
// forward & backward output layer
dY = logisticLayer.train(Z, T, minibatchSize, learningRate);

// backward hidden layer
dZ = hiddenLayer.backward(flattened_X, Z, dY, logisticLayer.W,
minibatchSize, learningRate);

// backpropagate delta to input layer
for (int n = 0; n < minibatchSize; n++) {
    for (int i = 0; i < flattenedSize; i++) {
        for (int j = 0; j < nHidden; j++) {
            dX_flatten[n][i] += hiddenLayer.W[j][i] * dZ[n][j];
        }
    }
    dX[n] = unflatten(dX_flatten[n]); // unflatten delta
}

// backward convolution + pooling layers
dC = dX.clone();
for (int i = nKernels.length-1; i >= 0; i--) {
    dC = convpoolLayers[i].backward(downsmapled_X.get(i),
        preActivated_X.get(i), activated_X.get(i),
        downsampled_X.get(i+1), dC, minibatchSize, learningRate);
}
```

The backward method of ConvolutionPoolingLayer is the same as forward, also simple. Backpropagation of max-pooling is written in upsample and that of convolution is in deconvolve:

```
public double[][][][] backward(double[][][][] X, double[][][][] preActivated_X, double[][][][] activated_X, double[][][][] downsampled_X, double[][][][] dY, int minibatchSize, double learningRate) {
    double[][][][] dZ = this.upsample(activated_X, downsampled_X, dY, minibatchSize);
    return this.deconvolve(X, preActivated_X, dZ, minibatchSize, learningRate);
}
```