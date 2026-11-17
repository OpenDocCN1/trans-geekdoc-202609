
practiced, we are more likely to find scenarios of such distribution of classes. For testing the model accuracies, a dataset consisting of 300 total images was used which included 66 COVID, 126 Pneumonia, and 108 Normal CXR images.

## EXPERIMENTS

In this section, let us understand the approach undertaken by the researchers. This research presents a pragmatic and comprehensive comparative study. Here, the deep learning models used to detect the abnormalities of the lungs are: VGG-16, AlexNet, ResNet101, and DenseNet121. In the first step of the process, all the models are foremost run individually on each of the silos, i.e., the individual clients. In this study, the researchers have assumed 3 clients each with the data distribution as shown in Tables 1, 2, 3 and 4. The images used as input for the experiments are all scaled to the size of 255x255. When the individual client completes training of their dataset on the selected model, the parameters of the saved model are saved. These parameters obtained from respective local centers are then transmitted to the central server model for aggregation. And hence in lieu of sharing raw data for further training, only the parameters obtained from the respective clients are forwarded. The individual clients can revise the parameters time and again as and when the data might keep getting updated. The overview of the approach is demonstrated in Fig. (1).

Table 1. Distribution of training dataset.

| Dataset Distribution | Client 1 | Client 2 | Client 3 |
|---|---|---|---|
| Normal | 1400 | 1350 | 1250 |
| COVID-19 | 500 | 700 | 798 |
| Pneumonia | 1100 | 900 | 1000 |

Table 2. Client-wise distribution of dataset.

| Client-wise Distribution | Client 1 | Client 2 | Client 3 |
|---|---|---|---|
| Total CXR images | 3000 | 2950 | 3048 |

Table 3. Class-wise Distribution of Dataset.

| Class-wise distribution | Normal | COVID-19 | Pneumonia |
|---|---|---|---|
| Total CXR images | 4000 | 1998 | 3000 |

| models | Client 1 loss | Client 1 accuracy | Client 2 loss | Client 2 accuracy | Client 3 loss | Client 3 accuracy | Server loss | Server accuracy |
|---|---|---|---|---|---|---|---|---|
| VGG-16 | 0.47 | 89.33 | 0.79 | 84.67 | 0.28 | 90.67 | 0.14 | 95.00 |
| AlexNet | 0.62 | 80.00 | 0.59 | 78.67 | 1.07 | 80.00 | 0.37 | 87.67 |
| ResNet101 | 0.44 | 92.00 | 0.98 | 82.99 | 1.24 | 83.00 | 0.03 | 97.00 |
| DenseNet121 | 0.31 | 92.00 | 0.88 | 86.00 | 0.32 | 90.00 | 0.05 | 98.33 |

It is clear from Fig. (1) that parameters of trained model are transferred to the central model. For this purpose, we use the models described below.

### VGG-16 [30]

The VGG model stands for the Visual Geometry Group as proposed by Oxford and hence it is also called OxfordNet. Here, 16 refers to the fact that the model has 16 layers with weights. VGG16 is a convolutional neural network model. The model includes 3 fully connected layers that follow a stack of convolutional networks. VGG16 is known for having multiple 3×3 kernel-sized filters instead of a large number of hyper-parameters. The model uses convolution layers of 3X3 filter with a convolutional stride of 1 and padding and max pool layer of a 2x2 filter of stride 2. Here, stride refers to the number of pixels shifted over the input matrix where stride 1 means that the filters will be moved one pixel at a time and stride 2 shows that the filters will be moved to two pixels at a time. The first two layers of VGG16 have 64 channels of a 3X3 filter size and the same padding. This is followed by a maxpool layer of 2x2 pool size and stride 2x2 and then 2 convolution layers of 128 channels of 3X3 kernel and the same padding. Then again comes a max-pooling layer similar to the previous one. This is then followed by 2 convolution layers of filter sizes 3X3 and 256 filters. After that, there are 2 sets of 3 convolution layers and a similar max-pooling layer. Each convolution layer has 512 filters of 3X3 size with the same padding. The image then obtained at the end of this architecture is then passed on to the stack of two convolution layers. The final convolution layer of the model is the soft-max layer. All the hidden layers of the VGG16 have rectification (ReLU) non-linearity as their activation function as the ReLU is found to be more efficient computationally due to its faster learning rate.

### AlexNet [31]

AlexNet is a convolutional neural network with deep layers with a higher number of filters than the previously proposed models like LeNet, etc. The architecture of AlexNet includes 8 layers; out of which five are convolutional layers and three are fully connected layers. The first convolution layer consists of 96 filters of size 11x11 and stride 4. This is followed by the first max-pooling layer of size 3X3 and stride 2. The next convolution layer has 256 filters of size 5x5 with stride 1 and padding 2. Next is a similar max-pooling layer that we already used before. Further, the third convolution layer has 384 filters. These filters are of size 3X3 stride 1 and padding is 1. Then we have a fourth convolution layer with 384 filters of size 3X3 and the same stride and padding as the third one. The final convolution layer is of size 3X3 with 256 such filters with stride 1 and padding 1. And finally, the third max-pooling layer of size 3X3 and stride 2 is applied. When AlexNet was proposed, tanh was a standard activation function used. AlexNet on the other hand used Rectified Linear Units (ReLU) instead, which significantly reduced the model training time. AlexNet also uses overlap pooling which in turn reduces the size of the network.

### ResNet101 [32]

ResNet refers to the residual network. This is because instead of the layers cramming the underlying mapping of the layers, ResNet fits the residual mapping of the layer. And ResNet-101 is a deep convolutional network that is 101 layers deep. The network has a default image input size of 224x224 and hence the tensor input will be of (224,224,3). Each block in ResNet101 is 3 layers deep. The architecture involves the issue of vanishing gradient and hence provides an approach to reduce the number of parameters to ensure faster computation. This is done with a max-pooling layer of size 3X3 and stride 2. And finally, a fully connected average pooling layer is applied with softmax activation.

### DenseNet121 [33]

DenseNet stands for Dense Convolutional Network. In this network, the layers connect deeper to other layers for efficient training and maximum data transfer between layers. Due to this type of connection, we observe that DenseNet architecture requires a lesser number of parameters as compared to standard convolution neural networks. The DenseNet 121 includes 5 primary kinds of layers out of which one is a 7x7 size convolutional layer along with a max-pooling layer of the size of 3X3 with stride 2. Then there are the 3 transitional layers with an average pooling layer of size 2x2 with stride 2. And finally, a fully connected classification layer with a global average pooling layer of size 7x7. This final layer uses softmax activation.

## RESULTS AND DISCUSSION

In this section, we present the results of the federated learning experiments on a test dataset. The results are generated on a local device i.e. client-side and on the aggregated server model. The procedure is demonstrated in Fig. (2). The models trained on the client devices are aggregated and the global server model is updated. Here, we use the “FedAvg” algorithm to aggregate the local models by averaging their model parameters.

Categorical cross-entropy is used to evaluate the loss of the models. Categorical cross-entropy is suited for multi-class classification as one image can belong to one category with a probability of 1, while other categories are given a probability of 0.

![](img/0616422b380b1bd62613a261ed51be87_30_0.png)

Fig. (2). Procedure followed for updating the server model.

In the table above, each model is subdivided into: client 1, client 2, client 3, and server. Here, each client is the local hospital/organization and the server is the final global aggregated server. First, each client is given the deep learning model which is trained on their individual dataset. The clients are evaluated locally and then they communicate the model parameters to the server. Each client sends its model parameters to the server, here we have 3 models, so there will be 3 model parameters that will be aggregated by the FedAvg algorithm on the server.
