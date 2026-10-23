The result only outputs the percentages of the accuracy, precision, and recall of the model, but for example, if you dump the prediction data with the predict method of LogisticRegression, you can see how much it actually predicts the probability, as follows:

```
```java
double[] y = output(x);   // activate input data through learned networks
Integer[] t = new Integer[nOut];  // output is the probability, so cast it to label

System.out.println( Arrays.toString(y) );
```
```

We've just shown that MLPs can approximate the function of XOR. Moreover, it is proven that MLPs can approximate any functions. We don't follow the math details here, but you can easily imagine that the more units MLPs have, the more complicated functions they could express and approximate.

# # Summary

In this chapter, as preparation for deep learning, we dug into neural networks, which are one of the algorithms of machine learning. You learned about three representative algorithms of single-layer neural networks: perceptrons, logistic regression, and multi-class logistic regression. We see that single-layer neural networks can't solve nonlinear problems, but this problem can be solved with multi-layer neural networks—the networks with a hidden layer(s) between the input layer and output layer. An intuitive understanding of why MLPs can solve nonlinear problems says that the networks can learn more complicated logical operations by adding layers and increasing the number of units, and thus having the ability to express more complicated functions. The key to letting the model have this ability is the backpropagation algorithm. By backpropagating the error of the output to the whole network, the model is updated and adjusted to fit in the training data with each iteration, and finally optimized to approximate the function for the data.

In the next chapter, you'll learn the concepts and algorithms of deep learning. Since you've now acquired a foundational understanding of machine learning algorithms, you'll have no difficulty learning about deep learning.