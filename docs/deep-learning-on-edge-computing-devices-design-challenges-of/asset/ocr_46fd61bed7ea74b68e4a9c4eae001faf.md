![](bbox=[0.14, 0.1, 0.89, 0.3])

# (a)Activation distribution

![](bbox=[0.14, 0.34, 0.89, 0.55])

# (b)Bitwise rate of code one and coefficients of \(\alpha^{(l)}\)

**Figure 4.2** Featurewise vs. bitwise activation sparsity. (a) The distributions of real-valued (upper) and quantized (lower) activations of the first four layers of ResNet50 over CIFAR10. (b) The average rate of code one of each bit of the quantized activation (upper) and the estimated coefficients \(\alpha^{(l)}\) (lower). It seems that the optimal code rates of different layers depend on the level of activation sparsity, and the Bitwise Bottleneck approach can adaptively remove the near-zero high-end bits and the less-informative low-end bits of the activation representation.

bitwise bottlenecks can exploit the sparsity in the activation representation so that the precision of activation representation without hurting classification accuracy can be reduced. Fig. 4.2 illustrates the activation distributions of the first four layers of ResNet50 [25] over the CIFAR10 dataset. It seems that activations of different layers are sparse, but the sparsity varies from layer to layer. Fig. 4.2(b) illustrates the average rate of code one in each bit of the activation representation (upper graph). Despite the change of featurewise sparsity as shown in Fig. 4.2(a), the bitwise sparsity over the high-end bits