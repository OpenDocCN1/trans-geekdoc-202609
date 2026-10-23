# 4.4.3. Loss Function

Faster R-CNN forces the ratio of positive and negative samples to 1:3 to solve the problem of unbalanced positive and negative proposals. Similar work in the field of computer vision includes focal loss, OHEM (online hard example mining) [202], GHM (gradient harmonizing mechanism) [203], and Libra R-CNN [204]. The paper [16,78], respectively, adopted focal loss to increase the weight of hard negative samples and reduce the weight of simple samples, so as to avoid the problem that a large number of simple samples cover a small number of hard negative samples in the training process.

# 4.4.4. Anchor and NMS

Faster R-CNN uses three scales and three aspect ratios, producing a total of 60 × 60 × 9 anchor boxes. However, the ship size in the SAR image is extremely small and sparse. There will be a waste in using dense anchor boxes for ship detection in SAR images. Yue et al. [57] and Wang et al. [122] set the parameters of the anchor box based on the analysis of the actual size and distribution of the ship, mainly reducing the size of the anchor box and selecting the appropriate shape. Chen et al. [70] and Li et al. [115] used K-means to obtain the distribution of the ship size, so as to obtain the appropriate anchor box and reduce the difficulty of learning.

Wei et al. [69] and Wang et al. [78] used soft NMS [205] to replace NMS. Soft NMS improves the discrimination process of IoU and threshold in the cycle process and uses weights to attenuate scores to avoid accuracy loss.

# 4.4.5. Others

ISASDNet (instance segmentation assisted ship detection network) was proposed based on Mask R-CNN in the paper [163]. It has two branches: detection and segmentation. The two branches output interaction to improve the detection results. Gui et al. [34] proposed a lightweight detection head with a large separable convolution kernel and position-sensitive pooling, which improves the detection speed.

# 4.5. Single-Stage Detectors

The two-stage detectors generate a candidate box first and then identify and regress the candidate box, which is quite different from the principle of human eyes. The single-stage detectors only need to look at the picture once and can predict what the object is and where the object is. It is similar to the human eyes. In addition, they are quite faster than two-stage detectors.

Classical single-stage detectors are YOLO, SSD, RetinaNet [206], and CornerNet [207]. YOLO and SSD are the two most popular single-stage detection algorithms, and most of the subsequent single-stage works are based on them.

The single-stage ship detectors in SAR images are shown in Figure 8.

![](bbox=[0.25, 0.68, 0.85, 0.88])

Figure 8. The single-stage SAR ship detectors.