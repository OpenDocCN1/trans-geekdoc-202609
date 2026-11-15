![](bbox=[0.105, 0.095, 0.845, 0.285])

Figure 5.3 The architecture of the Cellular Binary Neural Network. The left subfigure compares the binary neural networks with different architectures. The lateral connection of the CBN-Net contained in the dashed square is magnified on the right. The right subfigure illustrates the channelwise point multiplication operation defined by the group sparse lateral connection. The dashed connections are near-zero sparse connections.

input channel of the \(j\)th subnet at the \((k+1)\)th layer \(\mathbf{X}_t^{(j,k+1)}\) may depend on the \(t\)th output channel of the \(k\)th layers of different subnets as shown in Fig. 5.3:

```
\(\mathbf{X}_t^{(j,k+1)} = \mathbf{Y}_t^{(j,k)} + \sum_i^{i \neq j} \overline{W}_t^{(i,j,k)} \mathbf{Y}_t^{(i,k)}, \quad (5.9)\)
```

where the matrix \(\mathbf{Y}_t^{(i,k)}\) is the \(t\)th channel of the output tensor \(\mathbf{Y}^{(i,k)}\). With the weighted lateral connections, the output features from other binary subnets can enrich the input features of the next layer.

# 5.3.2 Group sparse regularization

It is worth noting that in Fig. 5.3 the brain-inspired lateral connections are assumed to be *sparse*. Furthermore, since different layers in deep neural networks may play different roles for the task of image classification, the lateral connections of the CBN-Net are assumed to be *grouped* with respect to different source layers. The characteristic of group sparsity can significantly reduce computational complexity caused by the extra lateral connections.

To improve the classification accuracy of the binary neural network, the CBN-Net adopts learnable lateral connection weights \(\overline{\mathbf{W}}\) and attempts to explore the optimal routing paths described by the lateral connection weights. Technically, the L21 norm-based group sparse regularization term