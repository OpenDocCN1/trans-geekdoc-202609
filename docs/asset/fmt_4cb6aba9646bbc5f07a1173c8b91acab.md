
## 4.4.1 Bridge Connections Analysis

Tables 4.1 and 4.2 compare the performance of various ResNet architectures with and without bridge connections, respectively. The performance without bridge connections drastically drops, particularly in ResNet-56 and ResNet-110. This comparison stresses the importance of bridge connections. However, in the original ResNet [3], all feature maps in the bridge connections are weighted equally. It is to be noted that SE-ResNet [5] weights the feature maps along the non-skip connections, based on their importance. The importance is learnt using a simple feed forward network that adds negligible computations. This idea motivated us to quantify the importance of feature maps that arise in bridge connections.

**Table 4.1** Performance of baseline ResNets.

| **Architecture** | **CIFAR-10 Top-1 (Acc %)** | **CIFAR-10 Top-5 (Acc %)** | **CIFAR-100 Top-1 (Acc %)** | **CIFAR-100 Top-5 (Acc %)** |
| --- | --- | --- | --- | --- |
| Res-20 | 91.4 | 99.74 | 67.37 | 91.06 |
| Res-32 | 92.32 | 99.73 | 69.8 | 91.25 |
| Res-44 | 93.57 | 99.81 | 73.15 | 92.9 |
| Res-56 | 93.16 | 99.82 | 73.8 | 92.99 |
| Res-110 | 93.66 | 99.77 | 73.33 | 92.7 |

**Table 4.2** Performance of baseline ResNets without bridge connections.

| **Architecture** | **CIFAR-10 Top-1 (Acc %)** | **CIFAR-10 Top-5 (Acc %)** | **CIFAR-100 Top-1 (Acc %)** | **CIFAR-100 Top-5 (Acc %)** |
| --- | --- | --- | --- | --- |
| Res-20 | 90.48 | 99.71 | 67.37 | 91.06 |
| Res-32 | 90.38 | 99.62 | 69.8 | 91.25 |
| Res-44 | 87.62 | 99.51 | 73.15 | 92.9 |
| Res-56 | 77.46 | 98.55 | 48.65 | 76.67 |
| Res-110 | 92.42 | 99.83 | 1.00 | 5.00 |

## 4.4.2 Res-SE-Net: Proposed Architecture

The novel architecture incorporates an `SE` block in each of the bridge connection of a ResNet. Figure 4.4 shows an illustration of a modified bridge connection. The proposed model `Res-SE-Net` has a similar architecture as mentioned in [3]. Specifically, our architecture is as follows.

The input image is of the size 32 × 32. The first layer is a 3 × 3 convolutional layer, which is followed by batch normalization [8] and ReLU [10]. This is followed by a stack of ResNet modules. A group of ResNet modules within the stack which have the same number of feature maps constitute a block. Average-pooling follows the stack of ResNet modules. The final layer is a fully connected layer followed by softmax activation, which predicts the probability of an input belonging to a class. The sub-sampling of feature-maps is done in the first convolutional layer of every block, by performing the convolution with a stride of 2. There is a reduction in the size of feature maps and an increase in their number from one block to another. Hence, to take activations from one block to another, the bridge connection downsamples the feature map size and increases their number by using 1 × 1 convolution with stride 2.

An `SE` block [5] is added on to the bridge connection just after downsampling. This ensures that when the feature maps are taken from one block to another, they are weighted according to the content that they carry. Hence, those features that are more relevant are given higher importance. The downsampled feature maps are sent from the previous block to the next one, so the weighting process must be done after downsampling in order to give more importance to the downsampled feature maps. Doing this before downsampling would reduce the significance of the weighted features. This is the primary reason for adding `SE` layer after downsampling and not before. It is also found empirically that adding `SE` layer before the downsampling process gives less accuracy compared to adding it after downsampling.

![Figure 4.4 Modified bridge connection.2](img/fig4-4.jpg)

**Figure 4.4** Modified bridge connection.^(2)

## 4.5 Experiments

### 4.5.1 Datasets

All experiments are conducted on CIFAR-10 [9] and CIFAR-100 [9] datasets. The CIFAR-10 dataset consists of 50,000 training images and 10,000 test images in 10 classes, with 5,000 training images and 1,000 test images per class. The CIFAR-100 dataset consists of 50,000 training images and 10,000 test images in 100 classes, with 500 training images and 100 test images per class. There are 20 main classes which contain these classes. The size of images in both the datasets is 32 × 32 and all of them are RGB images.

### 4.5.2 Experimental Setup

The experiments on ResNets considered ResNets of varying depths such as 20, 32, 44, 56, and 110 layers. The implementations are coded in `Pytorch` [11]. The code for baseline ResNet^(3) and SE-ResNet^(4) have been adapted from existing implementations and modified. The following data augmentation techniques are used:

## 4.6 结果

Tables 4.1, 4.4, and 4.5 报告了基线 ResNets、基线 SE-ResNets 和 Res-SE-Nets 所取得的准确率。

As 可以 从 Table 4.1 看出，表现最佳的 ResNet 是 ResNet-110，在 CIFAR-10 和 CIFAR-100 上的 Top-1 准确率分别为 93.66% 和 73.33%。

Similarly, 从 Table 4.4 可以看出，表现最佳的 SE-ResNet 是 SE-ResNet-110，在 CIFAR-10 和 CIFAR-100 上的 Top-1 准确率分别为 93.79% 和 72.99%。

It is clear from Table 4.5 that, our model, Res-SE-Net-110 reporting Top-1 accuracies of 94.53% and 74.93% on CIFAR-10 and CIFAR-100 datasets respectively, significantly overwhelms the baseline ResNets and SE-ResNets.

It can further be observed from Table 4.5, that Res-SE-Net-44 performs exceedingly well compared to baseline ResNets and SE-ResNets.

In fact, Res-SE-Net-44 can outperform ResNet-110 and SE-ResNet-110 by a significant margin of 0.42% and 0.29% on CIFAR-10 dataset, respectively. On CIFAR-100 dataset, Res-SE-Net-44 dominates over ResNet-110 and SE-ResNet-110 by a margin of 0.5% and 0.84%.

It is to be noted that Res-SE-Net-44 has 61.75% and 62.06% lesser number of parameters compared to ResNet-110 and SE-ResNet-110, respectively.

Res-SE-Net-56 too exhibits outstanding performance on CIFAR-100 dataset compared to baseline ResNets and SE-ResNets, and near on-par performance on CIFAR-10 dataset with baseline ResNets and SE-ResNets.

This strongly emphasizes the gravity of the proposed idea to activate the feature maps in bridge connections by their importance. The proposed idea enables a reasonably deep network with lesser number of parameters to outperform very deep networks.

**Table 4.4** Performance of baseline SE-ResNets.

| **Architecture** | **CIFAR-10 Top-1 (Acc %)** | **CIFAR-10 Top-5 (Acc %)** | **CIFAR-100 Top-1 (Acc %)** | **CIFAR-100 Top-5 (Acc %)** |
| --- | --- | --- | --- | --- |
| SE-ResNet-20 | 92.1 | 99.7 | 68.31 | 90.69 |
| SE-ResNet-32 | 93.08 | 99.83 | 70.09 | 92.12 |
| SE-ResNet-44 | 93.71 | 99.77 | 71.2 | 91.78 |
| SE-ResNet-56 | 93.64 | 99.76 | 71.42 | 91.28 |
| SE-ResNet-110 | 93.79 | 99.74 | 72.99 | 92.71 |

**Table 4.5** Performance of proposed model.

| **Architecture** | **CIFAR-10 Top-1 (Acc%)** | **CIFAR-10 Top-5 (Acc%)** | **CIFAR-100 Top-1 (Acc%)** | **CIFAR-100 Top-5 (Acc%)** |
| --- | --- | --- | --- | --- |
| Res-SE-Net-20 | 91.9 | 99.75 | 67.99 | 91.03 |
| Res-SE-Net-32 | 92.79 | 99.82 | 69.93 | 91.95 |
| Res-SE-Net-44 | 94.08 | 99.83 | 73.83 | 93.54 |
| Res-SE-Net-56 | 93.64 | 99.87 | 74.29 | 93.45 |
| Res-SE-Net-110 | 94.53 | 99.87 | 74.93 | 93.48 |

The improvement in accuracies of Res-SE-Nets, for both the datasets in comparison to baseline ResNets [3] and SE-ResNets [5] are tabulated in Tables 4.6 and 4.7, respectively. Res-SE-Net outperforms baseline ResNet by 0.566%, i.e., about 56 images on CIFAR-10 and by 0.704%, i.e., about 70 images on CIFAR-100 datasets on an average. Res-SE-Net-110 has achieved the maximum improvement in accuracy of 0.87% on CIFAR-10 and 1.6% on CIFAR-100 over Res-110. Similarly, Res-SE-Net outperforms SE-ResNet by 0.124% on CIFAR-10 and by 1.392% on CIFAR-100 datasets, respectively. Res-SE-Net-110 has achieved maximum overall improvement over SE-ResNet-110 with an increase in accuracy of 0.74% on CIFAR-10 and of 1.94% on CIFAR-100 datasets, respectively.

**Table 4.6** Performance improvement from baseline ResNet.
