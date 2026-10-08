at level (the patterns most liked by hidden units) clearly confirms the notion of multiple levels of composition which motivated deep architectures in the first place, moving up from edges to object parts to objects in a natural way.

# 4.6 Auto-Encoders

Some of the deep architectures discussed below (Deep Belief Nets and Stacked Auto-Encoders) exploit as component or monitoring a particular type of neural network: the auto-encoder, called autoassociator, or Diabolo network [25, 79, 90, 156, 172]. There are also connections between the auto-encoder and RBMs discussed in Section 5.4.3, showing that auto-encoder approximates RBM training by Contrastive Divergence. Because training an auto-encoder seems easier than training an RBM, they have been used as blocks to train deep networks, where each layer is associated with an auto-encoder that can be trained [17, 99, 153, 195].

An auto-encoder is trained to encode the input x into some representation c(x) so the input can be reconstructed from that representation. Hence the target output of the auto-encoder is the autoencoder input itself. If there is one linear hidden layer and the mean squared error criterion is used to train the network, then the k hidden units learn to project the input in the span of the first k principal components of the data [25]. If the hidden layer is non-linear, the auto-encoder behaves differently from PCA, with the ability to capture multi-modal aspects of the input distribution [90]. The formulation that we generalize the mean squared error criterion to the minimization of the negative log-likelihood of the reconstruction, given the encoding c(x):

```
$RE = -\log P(x|c(x)).$$
```

If x|c(x) is Gaussian, we recover the familiar squared error. If the inputs xi are either binary or considered to be binomial probabilities, then the loss function be

```
$-\log P(x|c(x)) = -\sum_{i} x_i \log f_i(c(x)) + (1 - x_i) \log(1 - f_i(c(x)))$
```