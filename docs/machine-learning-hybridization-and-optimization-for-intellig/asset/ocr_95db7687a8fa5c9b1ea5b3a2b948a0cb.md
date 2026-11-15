![](bbox=[0.175, 0.09, 0.78, 0.39])

# **FIGURE 15.3 Block diagram of the proposed model**

The live cam feed is taken using OpenCV, and an ROI is created. The background and foreground (ROI) are differentiated. This is done by calculating the cumulative weighted average of the background and then subtracting it from the frames that include an object in front of the background that may be recognized as foreground. The threshold values are calculated for every frame, and contours (for converting the image obtained to black and white such that the background is black and the objects detected in ROI are white) are determined by which we can know if there is any foreground object being detected in ROI (i.e., a hand). When contours are recognized (or a hand is present in the ROI), the image of the ROI is saved in the train and test sets for the relevant letter or number being detected.

# **15.2.2 TRAINING THE CNN MODEL ON THE DATASET CREATED**

A sequential CNN model is chosen and constructed with a total of 13 layers as shown in Figure 15.4: 3 convolution layers, 3 max pooling layers, 1 flattening layer, 4 dense layers, and 2 dropout layers. In the first, third, and fifth layers, ReLU is used as the activation function in convolutional layers