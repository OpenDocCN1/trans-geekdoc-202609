
## 7.1 Lightweight Feature Extraction

In the past, most research on CNN architectures has primarily focused on improving the accuracy, yielding deeper and more complex network architectures often unpractical for real-world applications due to their model size and inference time. With the increasing demand for online processing on mobile platforms with limited resources, novel CNN architectures aiming at reducing the number of parameters and computational operations have recently been proposed. Replacing the default CNN architectures used as base network with these computation-efficient architectures bears the potential to reduce the inference time of deep learning based detection frameworks, as feature extraction is one of the most time-consuming parts of these frameworks.

In this thesis, the applicability of such lightweight architectures is examined exemplarily for SSD, which allows a straightforward exchange of the CNN architecture. For this purpose, four promising architectures are adapted as base network for the task of vehicle detection in aerial imagery. In the following, the functional principle of SSD and the structures of the employed CNN architectures are introduced. Furthermore, auxiliary techniques for runtime optimization applied in this thesis are described followed by experiments and discussion of the results. The most promising architectures are then adopted for Faster R-CNN.

### 7.1.1 Single Shot MultiBox Detector

As described in Section 2.2, SSD is a fully convolutional network whose functional principle is similar to the RPN in Faster R-CNN (see Figure 7.1). In contrast to the class-agnostic RPN introduced in Section 5.1.1, SSD predicts a fixed number of bounding boxes and confidence scores for each object category. For this, (c + 4)k convolutional filters with kernel size 3 × 3 referred to as classification head are applied at each feature map location to predict four bounding box offsets relative to the anchor boxes termed default boxes and c confidence scores, where c is the number of object classes including the background class and k is the number of anchor boxes. By default, the output of multiple convolutional layers is used as feature map to account for various object scales.

![](img/99de1214c29cbc525a14b293385af5cf_150_0.png)

Figure 7.1: Schematic structure of SSD.

For training, the objective loss is equivalent to the multi-task loss of the RPN given in eq. (5.1). The classification loss is the softmax loss over multiple class confidences, while smooth L1 loss is used as regression loss. Note that in case of vehicle detection with only one category, the classification loss is equivalent to the two-class softmax of the RPN. Regression to the anchor boxes is performed analogously to the RPN by using eq. (5.5).

In the context of this thesis, only a single feature map is exploited as the examined aerial imagery datasets comprise images with a homogeneous GSD and thus, the vehicle dimensions exhibit only small variations. As observed in [Rin19], using multiple layers may even yield a worse detection accuracy. Moreover, truncating all layers after the exploited feature map also reduces the computational costs. To further account for the characteristics of the aerial imagery, the anchor box scales are adopted according to the vehicle size distribution, i.e., the anchor box scale is set to 28 pixels and the aspect ratios are set to 1:1, 1:2 and 2:1.

In the following, VGG16, which is used by default, is employed as base network for the SSD detector baseline. VGG16 pre-trained on ImageNet is used to initialize the weights. The baseline model is trained for 20,000 iterations using the SGD optimizer with a batch size of 32 and an initial learning rate of 0.0001. All other hyper-parameters remain unchanged from the original settings¹. During deployment, the 2500 predictions with the highest confidence score are considered for NMS. The top-200 predictions after NMS are used as final detections.

¹ https://github.com/weiliu89/caffe/tree/ssd

### 7.1.2 Computation-Efficient CNN Architectures

Several computation-efficient CNN architectures have recently been proposed, achieving comparable accuracies compared to conventional CNN architectures, while the inference time is considerably reduced. In the following, the most promising of these architectures that are examined in this thesis are presented and adaptations for the usage as base network within a deep learning based vehicle detector are described.

#### MobileNet

MobileNet [How17] is a recently proposed network architecture specially developed for mobile and embedded vision applications. Instead of standard 3 × 3 convolutions, depthwise separable convolutions (see Figure 2.11) are used as main building block. Due to the factorization of a standard 3 × 3 convolution into a 3 × 3 depthwise convolution followed by a 1 × 1 pointwise convolution, the computational costs and the number of parameters are considerably reduced compared to the standard 3 × 3 convolution. Except for an initial 3 × 3 convolution and the final fully connected layer used for classification, MobileNet only comprises stacked DSCs as depicted in Table 7.1. Strided convolutions are used for down-sampling instead of pooling, which provides a cheap way to decrease the input size. All convolutional layers are followed by batch normalization and ReLU nonlinearity to stabilize and speed up the training.

to a thinner network with considerably less parameters and reduced computational costs. By applying the resolution multiplier ρ ∈ (0,1] on the input image, the width W and height H of the input image and each subsequent layer are reduced to ρW and ρH, respectively. Though reducing the input image and the internal representation of every layer reduces the computational costs by ρ², it is not practicable for the task of vehicle detection in aerial imagery due to the already small object dimensions.

For the usage of MobileNet as base network within the SSD detector, only the output of the 5th DSC layer is exploited as feature map, as deeper layers would result in coarser feature map resolutions that are unsuited to accurately localize small objects. Thus, all deeper layers are truncated, yielding a clearly reduced model size. The official MobileNet weights pre-trained on ImageNet are used for initialization¹. Therefore, the weights are converted from the TensorFlow format to the Caffe format, as no pre-trained weights are directly available for Caffe. Due to findings in preliminary experiments, each model is trained for 45,000 iterations using the Adam optimizer with a batch size of 16 and an initial learning rate of 0.001.

#### ShuffleNet

ShuffleNet [Zha18b], designed especially for mobile devices with very limited computing power, employs DSCs to reduce the computational costs. In contrast to MobileNet, 1 × 1 convolutional layers are inserted before each DSC. Thus, the number of input channels and consequently computational operations for the 3 × 3 depthwise convolutions are reduced. By replacing conventional 1 × 1 convolutions with cheaper 1 × 1 group convolutions, the number of parameters and computational costs are further reduced. Depending on the group count g, a group convolution filter only considers the D/g channels of its respective group as input instead of the full channel depth D. Channel shuffling (see Figure 2.12) is applied after the auxiliary 1 × 1 group convolutions

#### PeleeNet

Table 7.3: Schematic structure of PeleeNet. The convolutions of the initial Stem Block comprise 32 channels except for the first 1 × 1 convolution that possesses 16 channels. For each Two-Way Dense Layer, the kernel size, number of channels, stride and padding are given for the 1 × 1 convolutions, as the number of channels, i.e., 16, remains constant throughout the network for all 3 × 3 convolutions. Note that the initial network is designed for input images of size 224 × 224 pixels.

| Layer Type | Kernel Size | Stride, Pad | Output Dim. |
|---|---|---|---|
| Stem Block |  |  | 56 × 56 × 32 |
| 3×Dense Layer convolution | 1 × 1 × 16 | 1, 1 | 56 × 56 × 128 |
| convolution | 1 × 1 × 128 | 1, 0 | 56 × 56 × 128 |
| avg pooling | 2 × 2 | 2 | 28 × 28 × 128 |
| 4×Dense Layer convolution | 1 × 1 × 32 | 1, 1 | 28 × 28 × 256 |
| convolution | 1 × 1 × 256 | 1, 0 | 28 × 28 × 256 |
| avg pooling | 2 × 2 | 2 | 14 × 14 × 256 |
| 8×Dense Layer convolution | 1 × 1 × 64 | 1, 1 | 14 × 14 × 512 |
| convolution | 1 × 1 × 512 | 1, 0 | 14 × 14 × 512 |
| avg pooling | 2 × 2 | 2 | 7 × 7 × 512 |
| 6×Dense Layer convolution | 1 × 1 × 64 | 1, 1 | 7 × 7 × 704 |
| convolution | 1 × 1 × 704 | 1, 0 | 7 × 7 × 704 |
| avg pooling | 7 × 7 | - | 1 × 1 × 704 |
| fully connected |  |  | 1000 |

For the usage of PeleeNet as base network within the SSD detector, only the output of the 1 × 1 convolutional layer after the 2nd stack of Two-Way Dense Layers is exploited as feature map. All deeper layers are truncated from the network. In contrast to the other computation-efficient networks, weights pre-trained on PASCAL VOC and MS COCO are used for initialization¹, as no weights pre-trained on ImageNet were publicly available at that time. Each model is trained for 30,000 iterations using the Adam optimizer with a batch size of 16 and an initial learning rate of 0.001.

¹ https://github.com/Robert-JunWang/Pelee
