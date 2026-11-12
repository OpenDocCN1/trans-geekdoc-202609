# First Conv. Layer Weights

![](bbox=[0.14, 0.14, 0.86, 0.37])

Figure 4.67: [a; b] (a) Low-level filters. (b) Meaningful features such as edges, nose, eyes, and face

Similarly, figure 4.68 shows a convolutional network trained on images taken from the Image net dataset. In this, a car image is shown to the network, and filters are learnt in the first convolutional layer for low-level features, edges, and color blobs. Also, these features or responses are aggregated to get much meaningful information (middle-level features) such as car headlights, some grids, and much useful color information. Finally, these middle-level features are aggregated in the next convolutional layer to get much more meaningful responses (high-level features) such as clear headlight, honeycomb structure in car design, and so on. Finally, the classifier is trained such that it classifies some random images of cars on the basis of the trained model:

![](bbox=[0.215, 0.645, 0.795, 0.905])

Figure 4.68: Feature visualization of convolution networks trained on ImageNet dataset (Zeiler & Fergus 2013)