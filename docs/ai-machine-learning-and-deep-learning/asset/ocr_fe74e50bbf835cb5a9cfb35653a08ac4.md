is a normal sample, its reconstruction error is small because the sample has the same generation process as the training data of autoencoder, and that, conversely, if the sample with detection is an adversarial sample, then the reconstruction error of that sample will be large.

2. *Probabilistic divergence-based detection*: The authors were able to find the adversarial input samples by comparing the results of two different sets of input data that went through the softmax layer output. They used the Jensen–Shannon scatter to measure the degree of disagreement between the results of the two sets of data.

The ideal reformer needs to satisfy the following two conditions: (1) It should not change the classification structure of the normal samples; (2) it should reconstruct the adversarial samples sufficiently so that the reconstructed samples are close to the normal samples. The authors trained the autoencoder to minimize the reconstruction errors on the training set and to ensure that it is well adapted to the validation set. Afterward, when given a normal input set, the autoencoder output a very similar example. However, when given an adversarial example, the autoencoder should output an example that approximates the adversarial one. In this way, MagNet can improve the classification accuracy while maintaining classification accuracy.

# 9.4 DISCUSSIONS AND OPEN ISSUES

The biggest challenges faced by current researchers can be summarized in two points.

+   1. *Effective defense against white-box attacks*: We still have not seen a defense that balances effectiveness and efficiency well. In terms of effectiveness, adversarial training shows the best performance but is computationally expensive. In terms of efficiency, many random and denoising-based defense algorithms can be configured in a few seconds, but simple defenses do not protect the DL model algorithm against attackers who already have the access to the DL model details.