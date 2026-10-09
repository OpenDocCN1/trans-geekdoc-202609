shapes, different image resolutions, and different colors in X-ray images, Gaus et al. used the transfer-learning method to evaluate the network structures of Faster R-CNN, Mask R-CNN, and RetinaNet, among which Faster R-CNN had the best detection performance [17].

In 2020, Tang Haoyang et al. used deformable convolution to reconstruct the feature-pyramid structure of the SSD network to improve the detection accuracy of the network in order to extract the deeper semantic features of dangerous goods when the feature pyramid is fused [18]. Yu et al. proposed an SSD-X detection network. Considering the position uncertainty and overlap of the target, multiple data enhancement is used to effectively improve the accuracy and over-fitting phenomenon. The focus loss is introduced into the confidence-loss function to accelerate the convergence rate of the model [19].

In 2021, Guo Shouxian et al. believed that the composite-backbone-network structure has a stronger ability to extract features. On the basis of YOLOv3, the composite-backbone network was used to build the YOLO-C network to improve the detection accuracy of the network [20]. On the basis of CenterNet, Tang et al. used ResNet-50 to improve its backbone network to improve detection speed and added a sampling layer to the feature-processing network to improve detection accuracy [21].

In 2022, Kumar et al. proposed a multi-channel region-recommendation network (MCRPN) to solve the scale difference of dangerous goods in X-ray-image recognition and achieve a faster RCRNN network, which uses different levels of convolution features in visual semantics and integrates the richer semantic information at the upper level of VGG16 and the shallower edge features at the lower level to map the multi-scale candidate-target area to the corresponding feature map [22]. Jiang et al. proposed the AM-YOLO model, adding the SE-attention module to the backbone network of YOLOv4 to distinguish the importance of feature-map channels, and proposed a new path-aggregation network to achieve the fusion of shallow and deep features, thus improving the network model-detection ability [23].

We proposed a combination of deformable convolution and the path-aggregation-network (PANet) module of the YOLOv4 network, and designed and implemented a dangerous-goods-detection algorithm for X-ray security-inspection images. The main contribution of the proposed method is summarized as follows:

+   1. This paper proposes combining deformable convolution with the PANet module of the YOLOv4 network and using the more flexible receptive field of deformable convolution to solve the problem of feature misalignment in the feature-fusion module of YOLOv4 in the process of high- and low-level feature fusion.

+   2. Based on the backbone network, a channel-pruning algorithm is designed to remove redundant channels in the network, reduce the amount of computation, and improve the reasoning speed of the network model. Experiments show that this method can effectively improve the inference speed of network models and meet the requirements of real-time security checks in terms of speed.

# 2. Related Work

X-ray security-inspection images mainly have the following characteristics:

+   (1) Serious loss of detail and color features: Due to the X-ray-imaging method and the material of the object itself, the original color information and detailed information on the contour of the object are lost during imaging.

+   (2) Background interference: When the background material is the same as the object, contour information similar to the object color is generated, which interferes with the model's learning of object-feature information during training.

+   (3) Serious-overlap phenomenon: The shape of an object undergoes significant changes under ray projection, and the random placement of positions and the overlapping placement of multiple objects results in complex, overlapping, and occluding contours of the object formed by X-rays passing through the object, increasing the difficulty of extracting effective features of various categories.