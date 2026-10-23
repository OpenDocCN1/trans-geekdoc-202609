
Here, the value of 10 in ConvolutionLayer.Builder() is the size of the kernels, and the value of 6 in .nOut() is the number of kernels. Also, .stride() defines the size of the strides of the kernels. The code we implemented from scratch in Chapter 4, Dropout and Convolutional Neural Networks has a functionality equivalent only to .stride(1, 1). The larger the number is, the less time it takes because it decreases the number of calculations necessary for convolutions, but we have to be careful at the same time that it might also decrease the model's precision. Anyway, we can implement convolutions with more flexibility now.

The subsampling layer is described as:

```
.layer(1, new
SubsamplingLayer.Builder(SubsamplingLayer.PoolingType.MAX, new int[]
{2,2})
    .build()
```

Here, {2, 2} is the size of the pooling windows. You may have noticed that we don't have to set the size of the inputs for each layer, including the output layer. These values are automatically set once you set up the model.

The output layer can be written just the same as in the other models:

```
.layer(2, new OutputLayer.Builder(LossFunctions.LossFunction.
NEGATIVELOGLIKELIHOOD)
    .nOut(outputNum)
    .weightInit(WeightInit.XAVIER)
    .activation("softmax")
    .build()
```

The graphical model of this example is as follows:

![](img/9315e45972ec0fbaf15f9144035bca79_185_0.png)

After the building comes the training. Since we have multiple mini-batches, we need to iterate training through all the batches. This can be achieved easily using .hasNext() on DataSetIterator and mnistIter in this case. The whole training process can be written as follows:

```
model.setListeners(Arrays.asList((IterationListener) new ScoreIterationListener(listenerFreq)));
while(mnistIter.hasNext()) {
    mnist = mnistIter.next();
    trainTest = mnist.splitTestAndTrain(splitTrainNum, new Random(seed));
    trainInput = trainTest.getTrain();
    testInput.add(trainTest.getTest().getFeatureMatrix());
    testLabels.add(trainTest.getTest().getLabels());
    model.fit(trainInput);
}
```

Here, the test data and test labels are stocked for further use.

During the test, again, we need to iterate the evaluation process of the test data because we have more than one mini-batch:

```
for(int i = 0; i < testInput.size(); i++) {
    INDArray output = model.output(testInput.get(i));
    eval.eval(testLabels.get(i), output);
}
```

Then, we use the same as in the other examples:

```
log.info(eval.stats());
```

This will return the result as follows:

```
=====================Scores=====================
Accuracy:  0.832
Precision: 0.8783
Recall:    0.8334
F1 Score:  0.8552464933704985
=====================
```

The example just given is the model with one convolutional layer and one subsampling layer, but you have deep convolutional neural networks with LenetMnistExample.java. In this example, there are two convolutional layers and subsampling layers, followed by fully connected multi-layer perceptrons:

```
MultiLayerConfiguration.Builder builder = new NeuralNetConfiguration.Builder()
    .seed(seed)
    .batchSize(batchSize)
    .iterations(iterations)
    .regularization(true).l2(0.0005)
    .learningRate(0.01)
    .optimizationAlgo(OptimizationAlgorithm.STOCHASTIC_GRADIENT_DESCENT)
    .updater(Updater.NESTEROVS).momentum(0.9)
    .list(6)
    .layer(0, new ConvolutionLayer.Builder(5, 5)
        .nIn(nChannels)
        .stride(1, 1)
        .nOut(20).dropOut(0.5)
        .weightInit(WeightInit.XAVIER)
        .activation("relu")
        .build())
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

As you can see in the first convolutional layer, dropout can easily be applied to CNN with DL4J.

With this model, we get the following result:

```
=========================Scores=========================
Accuracy:  0.8656
Precision: 0.8827
Recall:    0.8645
F1 Score:  0.873490476878917
=========================================================
```

You can see from the MNIST dataset page (http://yann.lecun.com/exdb/mnist/) that the state-of-the-art result is much better than the one above. Here, again, you would realize how important the combination of parameters, activation functions, and optimization algorithms are.

## Learning rate optimization

We have learned various deep learning algorithms so far; you may have noticed that they have one parameter in common: the learning rate. The learning rate is defined in the equations to update the model parameters. So, why not think of algorithms to optimize the learning rate? Originally, these equations were described as follows:

$\theta^{(\tau+1)} = \theta^{(\tau)} + \Delta\theta^{(\tau)}$

Here:

$\Delta\theta^{(\tau)} = -\eta \frac{\partial E}{\partial \theta^{(\tau)}}$

Here, $\tau$ is the number of steps and $\eta$ is the learning rate. It is well known that decreasing the value of the learning rate with each iteration lets the model have better precision rates, but we should determine the decline carefully because a sudden drop in the value would collapse the model. The learning rate is one of the model parameters, so why not optimize it? To do so, we need to know what the best rate could be.

The simplest way of setting the rate is using the momentum, represented as follows:

$\Delta\theta^{(\tau)} = -\eta \frac{\partial E}{\partial \theta^{(\tau)}} + \alpha\Delta\theta^{(\tau-1)}$

Here, $\alpha \in [0,1]$, called the **momentum coefficient**. This hyper parameter is often set to be 0.5 or 0.9 first and then fine-tuned.

Momentum is actually a simple but effective way of adjusting the learning rate but **ADAGRAD**, proposed by Duchi et al. (http://www.magicbroom.info/Papers/DuchiHaSi10.pdf), is known to be a better way. The equation is described as follows:

$\Delta\theta^{(\tau)} = -\frac{\eta}{\sqrt{\sum_{t=0}^{\tau} g_t^2}} g_{\tau}$

Here:

$g_{\tau} = \frac{\partial E}{\partial \theta^{(\tau)}}$

Theoretically, this works well, but practically, we often use the following equations to prevent divergence:

$\Delta \theta^{(\tau)} = -\frac{\eta}{\sqrt{\sum_{t=0}^{\tau} g_{t}^{2} + 1}} g_{\tau}$

Or we use:

$\Delta \theta^{(\tau)} = -\frac{\eta}{\sqrt{\sum_{t=0}^{\tau} g_{t}^{2} + 1}} g_{\tau}$

ADAGRAD is easier to use than momentum because the value is set automatically and we don't have to set additional hyper parameters.

ADADELTA, suggested by Zeiler (http://arxiv.org/pdf/1212.5701.pdf), is known to be an even better optimizer. This is an algorithm-based optimizer and cannot be written in a single equation. Here is a description of ADADELTA:

- Initialization:
  - Initialize accumulation variables:

$E\left[g^{2}\right]_{0} = 0$

And:

$E\left[\Delta \theta^{2}\right]_{0} = 0$

- Iteration τ = 0,1,2,...,T :
  - Compute:
    $$g_{\tau} = \frac{\partial E}{\partial \theta^{(\tau)}}$$
  - Accumulate gradient:
    $$E\left[g^2\right]_{\tau} = \rho E\left[g^2\right]_{\tau-1} + (1-\rho) g_{\tau}^2$$
  - Compute update:
    $$\Delta \theta^{(\tau)} = -\frac{\sqrt{E\left[\Delta \theta^2\right]_{\tau-1} + \varepsilon}}{\sqrt{E\left[g^2\right]_{\tau} + \varepsilon}} g_{\tau}$$
  - Accumulate updates:
    $$E\left[\Delta \theta^2\right]_{\tau} = \rho E\left[\Delta \theta^2\right]_{\tau-1} + (1-\rho)\left(\Delta \theta^{(\tau)}\right)^2$$
  - Apply update:
    $$\theta^{(\tau+1)} = \theta^{(\tau)} + \Delta \theta^{(\tau)}$$

Here, ρ and ε are the hyper parameters. You may think ADADELTA is rather complicated but you don't need to worry about this complexity when implementing with DL4J.

There are still other optimizers supported in DL4J such as RMSProp, RMSProp + momentum, and Nesterov's Accelerated Gradient Descent. However, we won't dig into them because, practically, momentum, ADAGRAD, and ADADELTA are enough to optimize the learning rate.
