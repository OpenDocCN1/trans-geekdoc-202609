
**TABLE 15.2** Summary of existing adversarial attacks for tasks that use videos as input.

KEY – ○: white-box, ●: black-box, T: targeted, T̄: untargeted, DD: data input dependency, U: universal, B̄: unbounded, B: bounded, R: region-based, Gen: generative, Opt: optimization, C: video classification, ME: motion estimation, OT: object tracking.

| Reference | Method | box | T | T̄ | DD | U | B | B̄ | R | Approach | Data sets | Task |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Ranjan et al. (2019) | OFA | ○, ● |  | ✓ |  | ✓ | ✓ |  | ✓ | Opt | KITTI | ME |
| Liang et al. (2020) | FAN | ○, ● | ✓ | ✓ | ✓ |  | ✓ |  |  | Gen | OTB, VOT | OT |
| Jiang et al. (2018) | V-BAD | ● | ✓ | ✓ | ✓ |  | ✓ |  |  | Opt | UCF, HMDB, Kinetics | C |
| Li et al. (2019b) | C-DUP | ○ | ✓ |  |  | ✓ | ✓ |  |  | Gen | UCF, JESTER | C |
| Lo and Patel (2020) | MultAV | ○ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | Direct, Opt | UCF | C |

(values in the range [0,1]) of the predicted labels, or the final labels. As not all layers (e.g., pooling layers) have trainable parameters, in this chapter we will use the term layer only for those with trainable parameters (e.g., convolutional and fully connected layers).

The models that have been attacked, or target models, are LeNet, AlexNet, VGGNets, GoogLeNet and variants, ResNets and WideResNets, DenseNets, and MobileNets for image classification; FCN, HED, and Faster R-CNN, for semantic segmentation, edge detection, and object detection, respectively; C3D, CNN + LSTM, I3D, and 3D ResNet-18 for video classification; SiamFC, SiamRPN, SiamRPN + CIR, and SiamRPN ++ for visual object tracking; and FlowNet, FlowNet2, SpyNet, PWC-Net, and Back2Future for motion estimation. We also include two non-DNN models, namely Epic Flow and LDOF, for optical flow estimation.

## 15.5.1.1 Models for image-based tasks

LeNet is a convolutional neural network (CNN) with 3 convolutional layers and 2 fully connected layers for image recognition (LeCun et al., 1998).

AlexNet has 8 convolutional layers and 3 fully connected layers, and the model architecture is similar to LeNet (Krizhevsky et al., 2012).

VGGNet has deeper architectures with 16 and 19 layers, but smaller convolutional filter kernels as multiple small convolutional filters with fewer parameters outperform a single large filter (Simonyan and Zisserman, 2014).

GoogLeNet (Inception-v1) has 22 layers (only layers with parameters are counted) and 9 of these layers consist of multiple convolutional filter sizes (inception layer/module) that reduces the computational cost and resources of the architecture (Szegedy et al., 2015). Inception-v2 and Inception-v3 (Szegedy et al., 2016) and Inception-v4 (Szegedy et al., 2017) are variants that further improve accuracy and reduce computational complexity. Improvements include factorizing filter sizes to stacked smaller filter size, increasing the number of filters and their size in each model (wider instead of deeper), label smoothing (regularization term to reduce the confidence of the network on a class), adding reduction blocks, and simplification of different modules (e.g., by choosing different number of filters and their size). Reduction blocks are 1 × 1 convolutional layers, also known as projection layers, that perform pooling of the feature maps over the channel dimension, thus resulting in a dimensionality reduction.

**ResNet** may have 18, 50, 101, or 152 layers. Blocks of layers are grouped to learn a function that maps the input to the output as a residual mapping (He et al., 2016).

**DenseNet** has architectures with 121, 169, 201, and 264 layers, whose four dense blocks can contain from 12 to 128 convolutional layers. DenseNet extends the residual mapping of ResNet by providing the feature maps of all previous layers within a block as input to subsequent layers within the same block (dense connection) to reduce the number of parameters, improve the flow of information and gradients throughout the network, and reduce overfitting (Huang et al., 2017).

**MobileNet** has 28 layers and two hyper-parameters that regulate the width of the network at each layer and the resolution of an input image (Howard et al., 2017). The first 13 layers are depth-wise separable convolutional layers that split the standard convolutional layer into two layers, a separate layer for filtering and a separate layer for combining the resulting output. This factorization reduces computation and model size. The architecture can be further reduced by removing layers.

**WideResNet** has higher accuracy than ResNet on image classification tasks with a shallower architecture and a larger width of the residual blocks (Zagoruyko and Komodakis, 2016).

**Fully Convolutional Networks (FCN)** use CNN models for image classification, such as AlexNet, VGGNet, and GoogLeNet, and replace fully connected layers with convolutional layers, followed by an upsampling layer (Long et al., 2015), thus generating an output feature map of the same size as the input. Because of this FCN can be trained end-to-end for (semantic) segmentation.

**Holistically-nested Edge Detector (HED)** is an FCN-based architecture that uses average pooling to detect edges (Xie and Tu, 2015).

**Faster R-CNN** is an FCN-based architecture that learns to generate object candidates, followed by localization and classification of the objects among the candidates (Ren et al., 2017). Faster R-CNN consists of pretrained convolutional layers, such as 13 convolutional layers of VGGNet, where the output is fed into the small network, with two convolutional layers, that outputs lower-dimensional features. These features, each of which represents an object candidate, are then fed into two independent fully connected layers to find the location of bounding boxes and their classes for object candidates.

## 15.5.1.2 Models for video-based tasks

**CNN + LSTM** is a video classifier that applies 2D architectures (e.g., AlexNet or GoogLeNet) to each frame independently using shared parameters through time, and then learns how to integrate information over time by using a recurrent neural network based on the Long Short-Term Memory (LSTM) operating on frame-level CNN activations (Ng et al., 2015). The combination of LSTM with the 2D networks allows the video classifier to maintain a constant number of parameters while capturing a global description of the video temporal evolution.

**C3D** is a spatio-temporal classifier with 8 3D convolutional layers and 2 fully connected layers (Tran et al., 2015). C3D can process 16 frames for action recognition.

**Inflated 3D CNN (I3D)** is a spatio-temporal architecture, built on top of 2D DNNs for image classification (e.g., Inception-v1), that combines the output of two 3D CNNs, one processing a group of RGB frames and the other processing a group of optical flow predictions among consecutive RGB frames (Carreira and Zisserman, 2017). I3D extends filters and pooling operations from 2D to 3D (inflating). I3D can also use pretrained weights from 2D models as initialization prior to fine-tuning.

**3D ResNet** is a spatio-temporal architecture that, similarly to I3D, extends image-based ResNet models to the temporal domain using 3D CNNs (Hara et al., 2018). Additional models, such as WideResNet and DenseNet can be extended with 3D CNNs.

**SiamFC** uses a fully convolutional Siamese architecture consisting of two convolutional neural networks sharing the same parameters. SiamFC is trained to predict a similarity map between a target template (or reference patch) and a search region in a current image via cross-correlation of the features outputted by the two branches. The reference patch is provided or initialized in the first frame (Bertinetto et al., 2016).

**SiamRPN** is based on the Siamese architecture to extract the features from the template and the search area. SiamRPN adds a region proposal network consisting of two branches, one for foreground-background classification and the other for regression, based on pair-wise cross-correlation (Li et al., 2018).

**SiamRPN ++** improves SiamRPN by using a spatially aware sampling strategy that provides a strict translation invariance, as padding introduced within DNNs breaks the invariance. Moreover, SiamRPN ++ adds a depth-wise cross-correlation layer that predicts multichannel correlation features between a template and search patches, exploiting the structure of a ResNet (Li et al., 2019).

**SiamRPN + CIR** adds Cropping-Inside Residual (CIR) units to eliminate the underlying position bias given by the zero padding. SiamRPN + CIR applies CIR units to different deep and wide networks, such as ResNet and Inception, when used within SiamFC and SiamRPN (Zhang and Peng, 2019).

**FlowNet** is an autoencoder (encoder-decoder architecture) with 9 convolutional layers and a correlation layer that performs multiplicative patch comparisons between two feature maps. Pairs of images with arbitrary size are provided as input to two branches of the architecture and combined with the correlation layer. The decoder part has 4 upconvolutional layers that perform extension of the feature maps, and concatenates with feature maps from the encoder to refine the optical flow with image details (Dosovitskiy et al., 2015).

**FlowNet2** stacks multiple FlowNet architectures to improve the accuracy of the optical flow estimation for both small and large displacements. The first network is FlowNet and the stacked networks use a single branch whose input is given by the concatenation of the flow estimated by the previous network with the two images, the warped image based on the optical flow, and a brightness error. The last stage of FlowNet2 fuses the output of the stacked networks with the output of an autoencoder for small displacements to obtain the final flow (Ilg et al., 2017).

**SpyNet** (Spatial Pyramid Network) combines a coarse-to-fine strategy, based on a spatial-pyramid formulation, with convolutional neural networks to estimate large motions within the image pyramid. For each level of the pyramid, a convolutional neural network updates the estimated optical flow, as one image of a pair is warped by the estimated optical flow at the coarser level (Ranjan and Black, 2017).

**PWC-Net** is a coarse-to-fine architecture that replaces the image pyramid with a feature pyramid. For each level, PWC-Net adds a layer that warps the feature from the second image toward the first image using the upsampled flow, and a correlation layer between features of
