![](bbox=[0.145, 0.105, 0.835, 0.515])

**Figure 5.** The samples of the furniture dataset. (a) bed. (b) chair. (c) sofa. (d) swivel chair. (e) table.

# 4.2. Experimental Platform Parameter Settings

The experimental environment was Intel(R) Xeon(R) CPU E5-2620 v4 @ 2.10 GHz processor, 128 GB running memory (RAM), NVIDIA GeForce RTX 2080Ti GPU. In addition, the deep learning framework was Pytorch. In the experiments, the size of the input data is set to 224, the number of training epochs is set to 30, and SGD optimization algorithm is used for optimization. The momentum is set to 0.9, and the learning rate is set to 0.1. All experimental training samples are randomly selected from furniture dataset and the ratio of training set to test set is 10:1. Meanwhile, this paper uses six different methods for comparison and analysis, including MobileNetV2, AlexNet, ShuffleNetV2, GoogLeNet [13], VGG16 and VGG16 network based on group convolution (GVGG16). The average accuracy (AA) commonly is used in furniture image classification as the evaluation index to better evaluate the proposed DGOVGG16 model’s classification performance of each category.

# 4.3. Design of DGOVGG16 Model

This paper takes DGOVGG16 as the main feature extraction network, which consists of 15 ReLU layers, 12 convolution layers, 5 MaxPool layers, 3 full connection layers, 1 over-parameterized convolution layer, 1 Leaky-ReLU layer, and 2 dropout layers. In order to make DGOVGG16 model use fewer parameters to represent more features, this paper sets the size of convolution kernel as 3 × 3 to replace the large convolution kernel by stacking small convolution kernels, and the size of the largest pooling layer is 2 × 2 to retain more image information. The number of neurons in the three full connection layers was 4096, 4096 and 5, respectively. When the dropout rate is 0.5, the experimental accuracy is the highest. Table 2 shows the parameter settings of DGOVGG16 network model.