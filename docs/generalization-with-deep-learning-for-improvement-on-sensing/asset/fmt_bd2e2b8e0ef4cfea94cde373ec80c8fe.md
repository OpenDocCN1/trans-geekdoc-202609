
### Multiple branch structure should be considered
Inception module is one of the most famous multi-branch architectures [[55](#chap8.xhtml#fsr55)]. The residual structure of `ResNet` [[56](#chap8.xhtml#fsr56)] is also viewed as a collection of network paths with different lengths. The multi-branch structure has been adopted by most deep models and its positive effects have been well documented.

### Batch normalization layer is a must
Batch normalization operation is proposed to solve the internal covariate shift phenomenon [[51](#chap8.xhtml#fsr51)]. It is widely used for the ability of avoiding over-fitting and improving generalization ability.

The basic characteristics of the proposed `LMB-CNN` module is that it contains three branches. To reason the proposed model is named lightweight multi-branch convolutional neural network (`LMB-CNN`) is that it obeys the design guidelines. In [Fig. 3](#chap8.xhtml#fig3), graphical detail is displayed. In addition, there are some intentional designs that follow above design guidelines: (1) adopt several blocks with similar structures to make the model concise; (2) each branch of a module has at most two convolutional layers to limit the total count of layers; (3) to reduce complexity, partially replace the normal convolution with the depthwise separable convolution; (4) three branches are combined to extract multiple diverse features; (5) To bring in competitive mechanism for different features, `MaxOut` strategy is selected to merge multiple branches.

The `LMB-CNN` mainly contains three convolutional modules, and each of them consists of three branches. The upper branch includes two depthwise separable convolutions [[53](#chap8.xhtml#fsr53)]; compared to standard convolution operation, depthwise convolution has fewer parameters. For depthwise separable convolution, each unit contains a `3 × 3` depthwise convolution followed by a `1 × 1` standard convolution. The depth convolution is given as follows:

![](images/p185-1.jpg)

**Figure 3:**Structure of `LMB-CNN`. The kernel size and count of convolution layers are shown in the blocks. `BN` layers and activation layers are hidden. The “`DS Conv`” means depth-wise separable convolution while “`Conv`” means standard convolution.

![](images/p186-1.png)

where `F[k + i −1, l + j −1, m]` represents the data which locates in (`k + i − 1, l + j − 1`) of the mth input feature map. ![](images/in186-1.png) is the parameter that locates in (`i − 1, i − 1`) of the mth convolutional kernel, `G[k,l,m]` is the data which locates in (`k, l`) of the *m*th output feature map. The middle branch that contributes the main computation is made up of two standard convolutional layers. Finally, aiming to possibly pass the low level features forward to the higher level, the last branch uses a `1 × 1` standard convolution to adjust the count of feature map channel just following the guidelines above. In such cases, the features from the invariable receptive field are possibly kept with the `MaxOut` strategy. In addition, the standard convolution is calculated as follows:

![](images/p186-2.png)

where the variables in Eq. (6) have the same meanings as those in Eq. (5). However, there are `M × N` convolutional kernels, `M` and `N` refer to input channel counts and output channel counts.

After a pooling operation on the three branches, a `MaxOut` layer will merge their features through competitive mechanism. Therefore, the better features will be retained while the low level features also have a chance via the lower branch. Besides, the operation can fuse multiple features to maintain comparatively low computation without increasing the feature map channels.

The integrated `LMB-CNN` model consists of two standard convolutional layers, three convolutional blocks and two fully connected layers. To get the final feature vectors, the first fully connected layer is set to dimensions based on complexity, where higher dimension can lead to a rapid complexity increase of the entire model. The second fully connected layer is used for final classification which has two neurons followed by a `softmax` function. In addition, the activation function is `ELU` function that is proposed in Ref. [[66](#chap8.xhtml#fsr66)], and is as follows:

![](images/p186-3.png)

The batch normalization layer proposed in Ref. [[51](#chap8.xhtml#fsr51)] has embedded after each convolutional layer as a general operation. The dimension of final feature vectors is `256` to control the computing complexity. As for training, cross-entropy loss is selected which is described as (8), and the optimization method is `Adam` algorithm that is proposed in Ref. [[52](#chap8.xhtml#fsr52)].

![](images/p187-1.png)

### 6. Fully Convolutional Networks
The `FCN` has been successful in the semantic segmentation of natural scenes [[57](#chap8.xhtml#fsr57), [58](#chap8.xhtml#fsr58)], but the size of the images they work on is usually not very large. Here attempts to apply `FCN` to large-scale remote sensing images has been made. As shown in [Fig. 4](#chap8.xhtml#fig4), the procedure for the proposed method can be divided into three steps:

(1)Divide the image into small blocks by checkerboard partitioning as the processing unit and extract the deep features of each block via an `LMB-CNN`.

(2)Rearrange the features of the blocks into multi-channel feature maps according to spatial location. The designed `FCN` segments the multichannel feature maps into eight preliminary segmentation masks.

(3)Vote on the eight preliminary segmentation masks to determine the final extraction result.

It’s worth pointing out that an `LMB-CNN` is used to extract features which are used as the inputs of an `FCN`. The segmentation task is essentially the classification of each local image block by considering neighboring relationships, so the classification features extracted by `LMB-CNN` are suitable for subsequent segmentation tasks.

The first step of the proposed algorithm divides the image into small blocks that are used to extract the deep features as the input of `FCN`, and the block size is `64 × 64` pixels considering that the resolution of the experimental data is `1 m`. There are four reasons to do this other than to combine `LMB-CNN` with `FCN` to construct an end-to-end network. Firstly, treating small blocks as the processing units is more appropriate than pixels. Secondly, this step can handle the problem that a large remote sensing image causes considerable consumption of hardware resources while using `FCN`. More than `20 GB` of storage is required for `64` channel feature maps with a size of `10240 × 10240` pixels, and the actual image is usually larger. This operation reduces the input size of `FCN` nearly one-thousand times. Thirdly, the selected `LMB-CNN` model can be trained as a classification task, while the `FCN` model used later is trained as a segmentation task. `FCN` segmentation uses the block-level features extracted by `LMB-CNN`, combines them together sequentially in a way that both of the tasks can be learned. Finally, the block size is `64` pixels because each block can traverse two or more buildings in terms of the definition of the built-up area.

![](images/p188-1.jpg)

**Figure 4:**Main framework of the proposed algorithm.

Deep features of each block are extracted by `LMB-CNN`, and the feature dimension was `256`. Based on the spatial position of image blocks, the deep features can be rearranged into `256` channel feature maps, similar to the output of a series of convolutional layers. The first nine feature maps of the sample image are shown in [Fig. 5](#chap8.xhtml#fig5) as examples.
