
2. L2CSNet augmented with PSA incorporates multiscale spatial information and cross-channel attention into the model, selectively highlighting feature regions relevant to vision estimation and suppressing irrelevant weights. Further, it facilitates granular level feature extraction, gaze direction feature extraction, and accurate vision estimation.

3. The proposed model is tested on a real-life dataset and four representative public datasets: the MPIIGaze dataset, the Gaze360 dataset, the ETH-XGaze dataset, and the GazeCapture dataset. The robustness and accuracy of the algorithm are verified by testing on individuals of varying nationalities, skin colors, ages, partial occlusion, genders and complex backgrounds, and lighting conditions.

## 3. Materials and Methods

First, this paper constructed a feature extractor to obtain the facial features, thereby narrowing down the range of eye feature extraction and accurately locating the key points of the eyes. Then, a high-precision gaze estimation algorithm [34] is proposed in this paper, which uses ResNet50 as the backbone network, uses a separate loss function to calculate the error of each gaze angle, and regresses the gaze result separately. Furthermore, to further improve the overall performance of the model and reduce the error of gaze results, this paper also introduces the PSA attention module, which combines multiscale spatial information and cross-channel attention into the model and selectively highlights the feature areas related to gaze estimation. Finally, the accuracy and robustness of the algorithm are verified in different environments. The algorithm flowchart of FPSA_L2CSNet is illustrated in Figure 1.

![](img/e4200cc4308edaf8913e513b0f96dbb6_180_0.png)

Therefore, this paper presents a novel attention-based mechanism, FPSA_L2CSNet, for gaze estimation. This approach leverages attention mechanisms to achieve more precise and efficient gaze estimation. The FPSA_L2CSNet algorithm is trained on different datasets, including MPIIGaze, Gaze360, ETH-XGaze, and GazeCapture, and its performance is thoroughly evaluated via comparison with other models. The results confirm the effectiveness and superiority of FPSA_L2CSNet in achieving more accurate and faster gaze estimation.

### 3.1. Acquisition of Facial Feature Points

As depicted in Figure 2, the FFE (facial feature extractor) in this study utilizes an RGB input image of 128 × 128 pixels to extract facial features. Due to the inherent variation in pixel composition within the dataset, we shall employ the transformative power of the resize (\\) function to preprocess the images. By skillfully applying bilinear interpolation, we shall artfully scale the image, ultimately attaining a harmonious size of \( 128 \times 128 \) pixels. The results are obtained after passing through 5 single BlazeBlocks and 6 double BlazeBlocks. The main route of the single BlazeBlock consists of a \( 5 \times 5 \) deep convolution and a \( 1 \times 1 \) convolution, with the depth-separable convolution layer being the core component. In contrast to traditional convolution layers that perform convolution operations in both the spatial and channel directions, the depthwise separable convolutional layer focuses on these two directions separately to reduce the parameter amount. Specifically, the depthwise separable convolution uses the same convolution kernel to perform convolution on each input channel, resulting in a set of individual output channels. In this way, each convolution kernel is reused, enabling the reduction in a significant number of parameters. The element-wise convolution is the second part of the depthwise separable convolution, using a \( 1 \times 1 \) convolution kernel to transform each individual output channel into the desired shape. In this way, the depthwise separable convolutional layer establishes the connection between depth and width. The side route of the single BlazeBlock consists of max pooling and channel pad, aiming to increase the convolution kernel size and cover the entire receptive field with fewer convolution layers. The skip connections in the single BlazeBlock allow the model to learn higher-level features that match the input better. Typically, cross-layer connections that span multiple layers help capture globally or partially informative features. Additionally, through skip connections, the single BlazeBlock can integrate with deeper grid structures to enhance the model's accuracy.

![](img/e4200cc4308edaf8913e513b0f96dbb6_181_0.png)

As the network deepens and the features extracted become more advanced, the double BlazeBlock was designed on top of the single BlazeBlock. Compared to the Single BlazeBlock, it simply adds another \( 5 \times 5 \) deep convolution and a \( 1 \times 1 \) convolution to the main path. In the double BlazeBlock, the two single BlazeBlock modules are similar in composition to single BlazeBlock in that they both consist of a depthwise separable convolution layer and a skip connection. These modules perform convolutional operations on the input feature map to extract high-level features by using a depthwise separable convolutional layer. The skip connection, on the other hand, ensures that the model learns feature information at a shallower level and allows for a fine-grained combination of feature spectra. The two single BlazeBlock modules in double BlazeBlock are similar in composition to single BlazeBlock in that they both consist of a depth-separable convolutional layer and a skip connection. These modules perform convolutional operations on the input feature map to extract high-level features by using a deeply separable convolutional layer. The skip connection, on the other hand, ensures that the model learns feature information at a shallower level and allows for a fine-grained combination of feature spectra. In double BlazeBlock, after processing by two single BlazeBlock modules, the feature map size and computational burden are then further reduced using the downsampling module. This allows the model to handle large-scale objects better, thus improving the accuracy of the network.

Therefore, the single BlazeBlock can be used for the shallow depth of the network, while the double BlazeBlock can be used for the deeper depth of the network. Through the aforementioned steps, facial feature information, including the feature areas for the left and right eyes, can be obtained.

### 3.2. ResNet50

Although designing deeper neural networks can lead to better recognition results in the process of deep network design, experiments indicate that as networks become increasingly deep, models will actually perform worse. While overfitting disturbance is eliminated, the real reason behind this problem comes from “vanishing gradients”. Vanishing gradients are inherent defects in the backpropagation training algorithm. As the error is returned, gradients from earlier layers of the network will become increasingly smaller.

Equation (1) presents the loss function of the network, where $X$ represents the input of the network, and $W$ represents the weight parameters. The corresponding gradient values from backpropagation are given by Equation (2).

$$Loss = F(X,W) \tag{1}$$

$$\frac{\partial Loss}{\partial X} = \frac{\partial F(X,W)}{\partial X} \tag{2}$$

Furthermore, extending to multilayer networks, the loss function is given by Equation (3), where n denotes the number of layers in the network. According to the chain rule, the gradient of layer i can be derived, as shown in Equation (4). It can be observed that as the error is backpropagated, gradients from earlier layers of the network become progressively smaller.

$$Loss = F_{n}(X_{n}, W_{n}), L_{n} = F_{n-1}(X_{n-1}, W_{n-1}), \cdots, L_{2} = F_{1}(X_{1}, W_{1}) \tag{3}$$

$$\frac{\partial Loss}{\partial X_{i}} = \frac{\partial F_{n}(X_{n}, W_{n})}{\partial X_{n}} * \cdots * \frac{\partial F(X_{i+1}, W_{i+1})}{\partial X_{i}} \tag{4}$$

To address this issue, ResNet ingeniously introduced residual structures, as shown in Figure 3.

![](img/e4200cc4308edaf8913e513b0f96dbb6_182_0.png)
