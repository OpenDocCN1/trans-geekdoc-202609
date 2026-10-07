# 224 Machine Intelligence

A robust methodology for detecting faults in sewer pipes has been developed. Faults of all defined type are detected in still images (81.5 percent accuracy). The methodology can be effectively applied to continuous footage (80 percent accuracy). Random Forests are identified as the most appropriate machine learning classifier. Smoothing greatly reduces the False Positive Rate [22].

This method presents the development of an automated tool to detect defects such as cracks, deformation, settled deposits, and joint displacement in sewer pipelines. The automated approach is dependent upon using image-processing techniques and several mathematical formulas to analyze output data from CCTV camera images [23]. Automated CCTV interpretation could improve the speed and accuracy of inspections. The defects in CCTV inspection use CNNs for classifying sewer defects. The CNNs were trained and tested on a set of 12,000 images collected from over 200 pipelines [24].

# 12.3 Proposed Methodologies

The deep learning technique for object detection using faster R-CNN with the combinations of different CNN architecture networks and image processing techniques are used to detect defects.

# 12.3.1 Faster R-CNN for Object Detection

The faster R-CNN is faster than R-CNN. It is used to predict the region proposals that are reshaped using a Region of Interest (ROI) pooling layer which is used to classify the image within the proposed region and predict the offset values for the bounding boxes.

# 12.3.1.1 Convolutional Layer

Every neuron takes inputs from a rectangular n*n section of the previous layer. The rectangular section is called a local receptive field. The layer is combined with bias and weights to produce a feature map. A parameter could be viewed as a trainable filter or kernel F, the convolutional process could be considered acting as an image convolution and it takes input from the previous layer (Eq. 12.1). Sometimes it may be called a trainable filter from the input layer to the hidden layer, based on the feature map with shared weights and biases.

```
x^{(l)} = \sigma(b + \sum_{c=0}^{n} W_{r,c} X^{(l-1)}_{i+r,j+c}) \quad (12.1)
```