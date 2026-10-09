![](bbox=[0.17, 0.1, 0.82, 0.4])

**Figure 2.** The detection results of YOLOv5 and Manual post-correction. (a) YOLOv5 pre-trained model. (b) Manual post-correction.

![](bbox=[0.05, 0.44, 0.93, 0.71])

**Figure 3.** Schematic representation of the proposed framework.

# 3.3.1. Object Detection

RetinaNet was proposed by Lin et al. [49] in 2018, which is based on three parts: the ResNet backbone, the feature pyramid network (FPN), and the object classification and bounding box regression subnetwork. Deeper neural networks capture more information, and the ResNet backbone uses identity mappings to ensure that performance does not degrade as the network’s depth increases. The FPN brings the benefits of multi-scale fusion by capturing coarse to fine semantic information, allowing for more feature details to be obtained for small object detection tasks and thus improving accuracy. The RetinaNet model runs the classification and regression sub-networks in parallel before attaching them to the FPN module. A sigmoid activation function is used to predict the classification at each location by the classification module. The regression sub-network outputs coordinate values of shape 4 via a fully connected layer. In object detection tasks [50–52], an imbalance between positive and negative samples is a major cause of classification difficulties. The