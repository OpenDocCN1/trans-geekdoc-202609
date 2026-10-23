Since we can see the multi-class classification problem, we generate a sample dataset with three classes. In addition to mean values and variances used in perceptrons, we also use the dataset according to normal distribution with the mean of 0.0 and the variance of 1.0 for the training data and the test data for class 3. In other words, each class's data follows normal distributions with the mean of [-2.0, 2.0], [2.0, -1.0] and [0.0, 0.0] and the variance of 1.0. We defined the training data as the int type and the test data as the Integer type for the labeled data. This is to process the test data easier when evaluating the model. Also, each piece of labeled data is defined as an array because it follows multi-class classification:

```
train_T[i] = new int[]{1, 0, 0};
test_T[i] = new Integer[]{1, 0, 0};
```

Then we classify the training data into a mini-batch using minibatchIndex, which was defined earlier:

```
for (int i = 0; i < minibatch_N; i++) {
    for (int j = 0; j < minibatchSize; j++) {
        train_X_minibatch[i][j] = train_X[minibatchIndex.get(i *
minibatchSize + j)];
        train_T_minibatch[i][j] = train_T[minibatchIndex.get(i *
minibatchSize + j)];
    }
}
```

Now we have prepared the data, let's practically build a model:

```
LogisticRegression classifier = new LogisticRegression(nIn, nOut);
```

The model parameters of logistic regression are w, weight of the network, and bias b:

```
public LogisticRegression(int nIn, int nOut) {
    this.nIn = nIn;
    this.nOut = nOut;
    W = new double[nOut][nIn];
    b = new double[nOut];
}
```

The training is done with each mini-batch. If you set minibatchSize = 1, you can make the training so-called online training:

```
for (int epoch = 0; epoch < epochs; epoch++) {
    for (int batch = 0; batch < minibatch_N; batch++) {
```