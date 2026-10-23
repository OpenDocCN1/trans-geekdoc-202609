Once a model is built, what we do next is train the model with dropout. The method for training is simply called train. Since we need some layer inputs when calculating the backpropagation errors, we define the variable called layerInputs first to cache their respective input values:

```
List<double[][]> layerInputs = new ArrayList<>(nLayers+1);
layerInputs.add(X);
```

Here, X is the original training data. We also need to cache the dropout masks for each layer for backpropagation, so let's define it as dropoutMasks:

```
List<int[][]> dropoutMasks = new ArrayList<>(nLayers);
```

Training begins in a forward activation fashion. Look how we apply the dropout masks to the value; we merely multiply the activated values and binary masks:

```
// forward hidden layers
for (int layer = 0; layer < nLayers; layer++) {

    double[] x_; // layer input
    double[][] Z_ = new
    double[minibatchSize][hiddenLayerSizes[layer]];
    int[][] mask_ = new
    int[minibatchSize][hiddenLayerSizes[layer]];

    for (int n = 0; n < minibatchSize; n++) {

        if (layer == 0) {
            x_ = X[n];
        } else {
            x_ = Z[n];
        }

        Z_[n] = hiddenLayers[layer].forward(x_);
        mask_[n] = dropout(Z_[n], pDroput);  // apply dropout mask
        to units
    }

    Z = Z_;
    layerInputs.add(Z.clone());

    dropoutMasks.add(mask_);
}
```