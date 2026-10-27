![](bbox=[0.156, 0.095, 0.833, 0.411])

**FIGURE 9.5**  Object detection algorithms.

The two-stage detectors perform object region proposals and then perform the feature-extraction–based object classification. The one-stage detection methods can work without finding the region proposal work. The methods usually predict the bounding box over the input image or video.

# 9.5.2  REGION PROPOSAL NETWORKS

The region proposal networks form the backbone for an object detection process in the two-stage detectors. The reason behind using the RPN is the identification of the available objects in the input image helping toward real-time object detection.

# 9.5.2.1  One-Stage Object Detection Algorithms

# a. YOLO

YOLO is the You Only Look Once object detection algorithm for fast object detection which has benefits like speed and accuracy as compared to other algorithms.

The object detection problem in YOLO can be considered as the regression problem to detect the objects in the real-time input through bounding box. The noted applications include detection of traffic signals, animals and people. The YOLO bounding box regression example is shown in Figure 9.6:

# b. Bounding Box Regression

The bounding box method is used to identify possible location of an object in the image and outline the object to highlight it as shown in Figure 9.7. Each created bounding box consists of width, height, class and