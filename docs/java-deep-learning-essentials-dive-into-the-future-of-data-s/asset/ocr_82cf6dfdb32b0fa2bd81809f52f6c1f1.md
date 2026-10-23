```
```java
.layer(1, new
SubsamplingLayer.Builder(SubsamplingLayer.PoolingType.MAX,
new int[]{2, 2})
        .build())
.layer(2, new ConvolutionLayer.Builder(5, 5)
        .nIn(20)
        .nOut(50)
        .stride(2,2)
        .weightInit(WeightInit.XAVIER)
        .activation("relu")
        .build())
.layer(3, new
SubsamplingLayer.Builder(SubsamplingLayer.PoolingType.MAX,
new int[]{2, 2})
        .build())
.layer(4, new DenseLayer.Builder().activation("tanh")
        .nOut(500).build())
.layer(5, new
OutputLayer.Builder(LossFunctions.LossFunction
.NEGATIVELOGLIKELIHOOD)
        .nOut(outputNum)
        .weightInit(WeightInit.XAVIER)
        .activation("softmax")
        .build())
.backprop(true).pretrain(false);
new ConvolutionLayerSetup(builder,28,28,1);
```
```

As you can see in the first convolutional layer, dropout can easily be applied to CNN with DL4J.

With this model, we get the following result:

```
```text
=========================Scores=========================
Accuracy:  0.8656
Precision: 0.8827
Recall:    0.8645
F1 Score:  0.873490476878917
=========================================================
```
```

You can see from the MNIST dataset page (http://yann.lecun.com/exdb/mnist/) that the state-of-the-art result is much better than the one above. Here, again, you would realize how important the combination of parameters, activation functions, and optimization algorithms are.