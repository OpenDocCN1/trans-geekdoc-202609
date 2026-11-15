estimate the optimal weight $\overline{W}_t^{(i,j,k)}$ associated with the lateral connections, technically, its gradient can be calculated as follows:

```
\frac{\partial \mathcal{L}}{\partial \overline{W}_t^{(i,j,k)}} = \sum_{x_t^{(j,k+1)}} \frac{\partial \mathcal{L}}{\partial x_t^{(j,k+1)}} \frac{\partial x_t^{(j,k+1)}}{\partial \overline{W}_t^{(i,j,k)}}, \quad (5.18)
```

where summation $\sum_{x_t^{(j,k+1)}}$ is applied to all entries in the $t$th channel, and the second term can be computed by Eq. (5.9). The key steps of the training process of our method are shown in Algorithm 5.1. With this novel binary network structure, we can train a highly accurate binary neural network in an end-to-end manner.

# 5.4 Application to efficient image classification

In this section. we conduct experiments with the proposed CBN-Net on two benchmark datasets, CIFAR-10 [23] and ILSVRC12 ImageNet [24]. Meanwhile, its classification performance was compared with other state-of-the-art binary neural networks.

# 5.4.1 Datasets and experiment settings

**CIFAR-10.** CIFAR-10 dataset [23] included 60,000 32×32 RGB color images, where there were totally 10 classes with 6000 images per class. There were 50,000 images used for training and 10,000 images used for testing the model performance. Similarly to previous works, we adopted the data augmentation strategies including random crop and flipping while tensor normalization was applied on both the training set and testing set.

**ImageNet.** ILSVRC 2012 ImageNet [24] was a large-scale dataset with 1000 classes, including 1.2 million high-resolution natural images for training and 50k images for testing. The most used data augmentation strategies such as random crop, flipping, and PCA noise were applied during training. In test time, we reported the evaluation results over 224 × 224 center-cropped testing images.

**Implementation Details.** All the experiments were implemented using PyTorch [25] and conducted on a single computer with 4 NVIDIA RTX 2080Ti GPUs.

For CIFAR-10 experiments, we chose ResNet-20 as the baseline model. During the training phase, the initial learning rate was 0.1, and the batch size was 128. The SGD optimizer with the momentum of 0.9