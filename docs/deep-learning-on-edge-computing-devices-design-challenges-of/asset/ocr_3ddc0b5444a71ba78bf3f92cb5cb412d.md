![](bbox=[0.22, 0.1, 0.8, 0.24])

Figure 6.2 Schematic diagram of bagged BNN. K independent BNN classifiers are trained based on different training samples to obtain K weak classifiers, which are then combined to form the final classifier.

![](bbox=[0.3, 0.33, 0.72, 0.48])

Figure 6.3 The accuracy of 64-128-128 BMLP model on MNIST when we change the number of extra-aggregated BNNs based on one BNN.

to combine the opinions of $K$ BNN classifiers for obtaining the final classification label. One is the hard voting, which selects the majority agreed label as the final label, and the other is selecting the best label after averaging the softmax probability of all classifiers, which be called soft voting.

We evaluated the bagging method on 64-128-128 bagged MLP (BMLP), which is a three-layer fully connected neural network for MNIST handwriting dataset, and each layer has 128 neurons except the first layer, which has 64. We compared two voting methods with different number of aggregated BNNs in terms of model accuracy. As shown in Fig. 6.3, the model with soft voting is always more accurate than that with hard voting, and the accuracy increases from 95.5% to 97.7% when we aggregate extra BNNs from 0 to 7. Interestingly, the situation was quite opposite when we applied the bagging method to some other model, so our hardware architecture supports both hard and soft voting to meet various task requirements with different networks.