framework based on contextual joint-representation learning. Experiments on SSDD and SMCDD show the effectiveness of the method.

# ### 4.11. Real-Time Detectors

At present, deep learning-based detectors need large computation and storage resources, which hinders the application in real-time prediction. In order to solve this problem, there are a lot of acceleration ideas in the evolution object detection algorithms. Firstly, researchers usually speed up the detection process. This idea is reflected in the evolution process of R-CNN, Fast R-CNN, Faster R-CNN, R-FCN, and Light-Head R-CNN. The above detectors share the features gradually, and the network structures become thinner and faster. Secondly, researchers usually design lightweight detection networks. The backbone network and the detection head can both be accelerated. Thirdly, researchers usually compress and accelerate CNN models. It includes lightweight neural network designing, model pruning, model quantization, and knowledge distillation [247–253].

The exploration of real-time detection algorithms in SAR ship detection can be divided into three directions, which are shown in Figure 13.

![](bbox=[0.157, 0.366, 0.841, 0.492])

**Figure 13.** The real-time SAR ship detectors.

# ### 4.11.1. Improving the Existing Real-Time Algorithms

Many improvements in this field are based on the YOLO and SSD series, because they have great advantages in running time, especially the YOLO series. Zhang et al. [40] used the idea of the YOLO algorithm and adopted depth separable convolution to accelerate the speed. MobileNet is used as the backbone network to improve the detection speed under the condition of ensuring detection accuracy. Zhang et al. [82] proposed an improved YOLOv3 (using DarkNet-19 and deleting repeated layers). It achieved 90.08% AP₅₀ and 68.1% AP on the SSDD dataset. Mao et al. [103] adopted the FCOS detection algorithm with ResSARNet as the backbone network, and center-ness on bounding box regression branch, center sampling, GIoU loss, and adaptive training sample selection were used. It can achieve 61.5% AP with only 1.17 M parameters. Zhong et al. [157] adopted CFAR and YOLOv4 to realize real-time ship detection on China HISEA-1 SAR images.

# ### 4.11.2. Designing a Lightweight Model

Zhang et al. [51] designed a lightweight feature optimization network LFO-Net based on SSD. It can be trained from scratch and reduce the training and testing time without reducing the accuracy. The detection performance is further improved by the bidirectional feature fusion module and attention mechanism. It achieved 80.12% AP₅₀ with 9.28 ms testing time on SSDD. Zhang et al. [54] used multi-scale detection, cascade, and anchor box mechanism to design a lightweight network for real-time SAR ship detection. It uses depthwise and pointwise to replace the traditional convolution. It achieved 94.13% AP₅₀ with 9.03 ms testing time on SSDD. Mao et al. [81] used the simplified U-Net as the feature extraction network, which has only 0.47 million learnable weights, it improves the operation speed and solves the problem caused by the anchor box through the anchor-free method. It has a total of 0.93 million learnable weights, and the AP on the SSDD dataset is 68.1%. Zhang et al. [84] proposed ShipDeNet-20, which has 20 convolution layers and a