
The parameters of the MLP are the weights w and bias b of the hidden layer, HiddenLayer, and the output layer, LogisticRegression. Since the output layer is the same as the one previously introduced, we won't look at the code here. The constructor of HiddenLayer is as follows:

```java
public HiddenLayer(int nIn, int nOut, double[][] W, double[] b, Random rng, String activation) {

    if (rng == null) rng = new Random(1234);  // seed random

    if (W == null) {

        W = new double[nOut][nIn];
        double w_ = 1. / nIn;

        for(int j = 0; j < nOut; j++) {
            for(int i = 0; i < nIn; i++) {
                W[j][i] = uniform(-w_, w_, rng);  // initialize W with uniform distribution
            }
        }

    }

    if (b == null) b = new double[nOut];

    this.nIn = nIn;
    this.nOut = nOut;
    this.W = W;
    this.b = b;
    this.rng = rng;

    if (activation == "sigmoid" || activation == null) {

        this.activation = (double x) -> sigmoid(x);
        this.dactivation = (double x) -> dsigmoid(x);

    } else if (activation == "tanh") {

        this.activation = (double x) -> tanh(x);
        this.dactivation = (double x) -> dtanh(x);

    } else {
        throw new IllegalArgumentException("activation function not supported");
    }
}
```

W is initialized, randomly matching the number of the units. This initialization is actually tricky as it makes you face the local minima problem more often if the initial values are not well distributed. Therefore, in a practical scene, it often happens that the model is tested with some random seeds. The activation function can be applied to either the sigmoid function or the hyperbolic tangent function.

The training of the MLP can be given by forward propagation and backward propagation through the neural networks in order:

```java
public void train(double[][] X, int T[][], int minibatchSize, double learningRate) {
    double[][] Z = new double[minibatchSize][nIn];  // outputs of hidden layer (= inputs of output layer)
    double[][] dY;
    // forward hidden layer
    for (int n = 0; n < minibatchSize; n++) {
        Z[n] = hiddenLayer.forward(X[n]);  // activate input units
    }
    // forward & backward output layer
    dY = logisticLayer.train(Z, T, minibatchSize, learningRate);
    // backward hidden layer (backpropagate)
    hiddenLayer.backward(X, Z, dY, logisticLayer.W, minibatchSize, learningRate);
}
```

The part of hiddenLayer.backward gives the hidden layer backpropagation of the prediction error, dY, from a logistic regression. Be careful, as the input data of a logistic regression is also necessary for the backpropagation:

```java
public double[][] backward(double[][] X, double[][] Z, double[][] dY, double[][] Wprev, int minibatchSize, double learningRate) {
    double[][] dZ = new double[minibatchSize][nOut];  // backpropagation error
    double[][] grad_W = new double[nOut][nIn];
    double[] grad_b = new double[nOut];

    // train with SGD
    // calculate backpropagation error to get gradient of W, b
    for (int n = 0; n < minibatchSize; n++) {

        for (int j = 0; j < nOut; j++) {

            for (int k = 0; k < dY[0].length; k++) { // k < ( nOut of previous layer )
                dZ[n][j] += Wprev[k][j] * dY[n][k];
            }
            dZ[n][j] *= dactivation.apply(Z[n][j]);

            for (int i = 0; i < nIn; i++) {
                grad_W[j][i] += dZ[n][j] * X[n][i];
            }

            grad_b[j] += dZ[n][j];
        }
    }

    // update params
    for (int j = 0; j < nOut; j++) {
        for(int i = 0; i < nIn; i++) {
            W[j][i] -= learningRate * grad_W[j][i] / minibatchSize;
        }
        b[j] -= learningRate * grad_b[j] / minibatchSize;
    }

    return dZ;
}
```

You might think the algorithm is complex and difficult because the arguments seem complicated, but what we do here is almost the same as what we do with the train method of logistic regression: we calculate the gradients of W and b with the unit of the mini-batch and update the model parameters. That's it. So, can an MLP learn the XOR problem? Check the result by running MultiLayerPerceptrons.java.

The result only outputs the percentages of the accuracy, precision, and recall of the model, but for example, if you dump the prediction data with the predict method of LogisticRegression, you can see how much it actually predicts the probability, as follows:

```java
double[] y = output(x);   // activate input data through learned networks
Integer[] t = new Integer[nOut];  // output is the probability, so cast it to label

System.out.println( Arrays.toString(y) );
```

We've just shown that MLPs can approximate the function of XOR. Moreover, it is proven that MLPs can approximate any functions. We don't follow the math details here, but you can easily imagine that the more units MLPs have, the more complicated functions they could express and approximate.

## Summary

In this chapter, as preparation for deep learning, we dug into neural networks, which are one of the algorithms of machine learning. You learned about three representative algorithms of single-layer neural networks: perceptrons, logistic regression, and multi-class logistic regression. We see that single-layer neural networks can't solve nonlinear problems, but this problem can be solved with multi-layer neural networks—the networks with a hidden layer(s) between the input layer and output layer. An intuitive understanding of why MLPs can solve nonlinear problems says that the networks can learn more complicated logical operations by adding layers and increasing the number of units, and thus having the ability to express more complicated functions. The key to letting the model have this ability is the backpropagation algorithm. By backpropagating the error of the output to the whole network, the model is updated and adjusted to fit in the training data with each iteration, and finally optimized to approximate the function for the data.

In the next chapter, you'll learn the concepts and algorithms of deep learning. Since you've now acquired a foundational understanding of machine learning algorithms, you'll have no difficulty learning about deep learning.

## 3 Deep Belief Nets and Stacked Denoising Autoencoders

From this chapter through to the next chapter, you are going to learn the algorithms of deep learning. We'll follow the fundamental math theories step by step to fully understand each algorithm. Once you acquire the fundamental concepts and theories of deep learning, you can easily apply them to practical applications.

In this chapter, the topics you will learn about are:

- Reasons why deep learning could be a breakthrough
- The differences between deep learning and past machine learning (neural networks)
- Theories and implementations of the typical algorithms of deep learning, **deep belief nets (DBN)**, and **Stacked Denoising Autoencoders (SDA)**

## Neural networks fall

In the previous chapter, you learned about the typical algorithm of neural networks and saw that nonlinear classification problems cannot be solved with perceptrons but can be solved by making multi-layer modeled neural networks. In other words, nonlinear problems can be learned and solved by inserting a hidden layer between the input and output layer. There is nothing else to it; but by increasing the number of neurons in a layer, the neural networks can express more patterns as a whole. If we ignore the time cost or an over-fitting problem, theoretically, neural networks can approximate any function.

So, can we think this way? If we increase the number of hidden layers—accumulate hidden layers over and over—can neural networks solve any complicated problem? It's quite natural to come up with this idea. And, as a matter of course, this idea has already been examined. However, as it turns out, this trial didn't work well. Just accumulating layers didn't make neural networks solve the world's problems. On the contrary, some cases have less accuracy when predicting than others with fewer layers.

Why do these cases happen? It's not wrong for neural networks with more layers to have more expression. So, where is the problem? Well, it is caused because of the feature that learning algorithms have in feed-forward networks. As we saw in the previous chapter, the backpropagation algorithm is used to propagate the learning error into the whole network efficiently with the multi-layer neural networks. In this algorithm, an error is reversed in each layer of the neural network and is conveyed to the input layer one by one in order. By backpropagating the error at the output layer to the input layer, the weight of the network is adjusted at each layer in order and the whole weight of a network is optimized.

This is where the problem occurs. If the number of layers of a network is small, an error backpropagating from an output layer can contribute to adjusting the weights of each layer well. However, once the number of layers increases, an error gradually disappears every time it backpropagates layers, and doesn't adjust the weight of the network. At a layer near the input layer, an error is not fed back at all.

The neural networks where the link among layers is dense have an inability to adjust weights. Hence, the weight of the whole of the networks cannot be optimized and, as a matter of course, the learning cannot go well. This serious problem is known as the **vanishing gradient problem** and has troubled researchers as a huge problem that the neural network had for a long time until deep learning showed up. The neural network algorithm reached a limit at an early stage.

## Neural networks' revenge

Because of the vanishing gradient problem, neural networks lost their popularity in the field of machine learning. We can say that the number of cases used for data mining in the real world by neural networks was remarkably small compared to other typical algorithms such as logistic regression and SVM.
