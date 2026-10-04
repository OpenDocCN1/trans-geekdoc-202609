# 10 Featured Examples

details, we Pretrained Deep Neural Networks). This example uses ResNet-18 for feature extraction. You can also use other pretrained networks such as MobileNet v2 or ResNet-50 depending on application requirements. The detection sub-network is a small CNN compared to the feature extraction and is composed of a few convolutional layers and layers specific for YOLO v2.

Use the yolov2Layers function to create a YOLO v2 object detection network automatically given a pretrained ResNet-18 feature extraction network. yolov2Layers requires you to specify several inputs that parameterize a YOLO v2 network:

+   - Network input size
- Anchor boxes
- Feature extraction network

First, specify the network input size and the number of classes. When choosing the network input size, consider the minimum size required by the network itself, the size of the training images, and the computational cost incurred by processing data at the selected size. When feasible, choose a network input size that is close to the size of the training images and larger than the input size required for the network. To reduce the computational cost of running the example, specify a network input size of [224 224 3], which is the minimum size required to run the network.

```
inputSize = {224 224 3};
```

Define the number of object classes to detect.
numClasses = width(vehicleDataset)-1;

Note that the training images used in this example are bigger than 224-by-224 and vary in size, so you must resize the images in a preprocessing step prior to training.

Next, estimateAnchorBoxes to estimate anchor boxes based on the size of objects in the training data. To account for the resizing of the priors prior to training, resize the training data for estimating anchor boxes. Use transform to preprocess the training data, then define the number of anchor boxes and estimate the anchor boxes. Resize the training data to the input image size of the network using the function ypreprocessData.

```
trainingDataForEstimation = transform(trainingData,@data)yolo_preprocessData(data,inputSize);
Anchors = 7;
meanIoU = estimateAnchorBoxes(trainingDataForEstimation,numAnchors)
```

```
anchorBoxes = 7x2

145 126
91 86
161 132
41 34
67 64
136 111
23
```

```
meanIoU = 0.8651
```

For more information on choosing anchor boxes, see Estimate Anchor Boxes From Training Data (Computer Vision Toolbox (Computer Vision Toolbox™) and Anchor Boxes for Object Detection (Computer Vision Toolbox).

# 10-126