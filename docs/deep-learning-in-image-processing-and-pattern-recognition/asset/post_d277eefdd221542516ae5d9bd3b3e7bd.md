
This means that the output layer is $y = x + F(x)$, which implies that, in the process from Equation (4) to Equation (5), the gradient will not vanish even if the network becomes deeper.

$$\frac{\partial X_{i+1}}{\partial X_i} = \frac{\partial X_i + \partial F(X_i, W_i)}{\partial X_i} = 1 + \frac{\partial F(X_{i+1}, W_{i+1})}{\partial X_i} \quad (5)$$

The introduction of residual structures in ResNet allows for training neural networks that are deeper and more efficient, reducing the risk of overfitting while improving model performance. Specifically, there are several advantages to using residual structures: mitigate the problem of gradient disappearance, solve the problem of degradation, and avoid the problem of overfitting.

ResNet [35] has five different structures, namely ResNet18, ResNet34, ResNet50, ResNet101, and ResNet152, representing different model depths and widths. The main differences between them are the depth and number of parameters of the models. ResNet-18 and ResNet-34 have the same basic structure and are relatively shallow networks. The basic structure of the last three models, ResNet-50, ResNet-101, and ResNet-152, is different from ResNet-18 and ResNet-34, representing deeper networks. Overall, the ResNet network structure has a large amount of computation and is complex, although the use of $1 \times 1$ convolution reduces the number of parameters. The depth of the network determines that the number of parameters is large. Therefore, choosing a network with too many layers may lead to overfitting and difficulty in convergence, while choosing a network with too few layers may result in poor training outcomes and low accuracy. Considering the above, in order to improve the accuracy of the network and prevent overfitting, ResNet50 is chosen as the backbone network in this paper. Its residual structure is shown in Figure 4.

![](img/e4200cc4308edaf8913e513b0f96dbb6_183_0.png)

Figure 4. The residual structure of ResNet50.

This model comprises a main branch from top to bottom and skips connections on its right side. Its core idea is to transmit input information directly to the output via skip connections and to learn only the differences between the output and input through the main branch, thereby simplifying the learning process. In the main branch, $1 \times 1$ convolution is used to reduce the number of dimensions and generate 64 feature maps. Then, $3 \times 3$ convolution is performed to extract the main features. Subsequently, $1 \times 1$ convolution is executed to increase dimensionality and generate 256 feature maps. Additionally, batch normalization (BN) is utilized in ResNet to improve the model’s generalization ability by subtracting the mean and dividing by the variance of the same batch of data. Furthermore, rectified linear units (ReLu), a nonlinear activation function, are employed to enhance the model’s nonlinear adaptability.

Figure 5 shows the overall architecture of ResNet50, which adds branches between every two layers of the network and can sample input images with a convolutional sequence of 2. It is evident from the structure that there are four layers in the ResNet50 structure, and each layer is comprised of 3, 4, 6, and 3 residual blocks, respectively. The “3 4 6 3” in the basic block structure refers to the number of residual units in each layer, and these residual units are the basic subelements with interlayer connections. A large number of convolutional layers in ResNet are composed of these basic subelements arranged according to certain rules. Therefore, these numbers actually reflect the overall network depth of ResNet. The advantage of this design is that it enables ResNet to use the depth of the network more effectively and avoids the performance degradation problem that occurs when the number of layers increases in traditional deep networks.

![](img/e4200cc4308edaf8913e513b0f96dbb6_184_0.png)

**Figure 5. The overall architecture of ResNet50.**

## 3.3. Attention Mechanism

As a data processing method in machine learning, the attention mechanism mainly focuses the network’s learning on important areas. Studies have shown that embedding attention modules into convolutional neural networks can greatly improve network performance. In recent years, the method has been widely applied in computer vision, such as image classification, object detection, and semantic segmentation. Overall, attention mechanisms are mainly divided into channel attention and spatial attention; the most commonly used methods are the SE attention mechanism module [36] and the convolutional block attention module (CBAM) [37], respectively. The former has a simpler structure, consisting of two parts: squeeze and excitation. The main purpose of the squeeze part is to represent the importance of each channel feature, while the excitation part multiplies the feature map channels with the weighted channel importance obtained by the squeeze. Thus, it can make the model aware of the importance of each channel. However, the global average pooling of the squeeze module in the SE attention module is too simple to capture complex global information, and the fully connected layer of the excitation module increases model complexity, ignoring spatial information and leading to long calculation time and overfitting. The characteristic of the CBAM is that it focuses on the densest positions of effective information in an image, concatenates the feature maps generated by max pooling and average pooling, and applies convolutional and activation functions to form spatial attention maps. However, the CBAM has not captured spatial information at different scales to enrich the feature space, and its spatial attention only considers local information, failing to establish long-distance dependencies.

The PSA module not only has the ability to process tensors at multiple scales but also extracts spatial information at different scales by compressing the channel dimension of the input tensor. The PSA attention module [38] consists of four parts, as shown in Figure 6. First, the SPC module is used to obtain multiscale feature maps with channel diversity. Then, the SE weight module is used to obtain channel attention across multiscale feature maps. Next, the softmax function is used to adjust channel attention again and obtain the weight of multiple-scale channels. Finally, element-wise multiplication is applied to the recalibrated weights and corresponding feature maps. Based on the above four steps, multiscale feature information can be outputted. In this structure, the spatial information of the input feature maps is obtained by using a multibranch method, which can obtain rich position information and conduct parallel processing for multiple scales. Moreover, the pyramid structure generates different spatial resolutions and depths of multiscale convolution kernels, effectively extracting spatial information at different scales on each channel feature map. Therefore, by integrating multiscale spatial information and cross-channel attention into the original model, multiscale spatial information can be extracted at a more granular level.

![](img/e4200cc4308edaf8913e513b0f96dbb6_185_0.png)

Figure 6. Structure of PSA module.

First, the SPC module is used to obtain feature maps with multiple channel scales. Although each input image in this structure has feature maps with different scales $F_i$, they have the same channel dimension $C'$. Their relationship is expressed as follows:

$$ C^i = \frac{C}{S} \quad i=0,1,\dots, m-1 \quad (6) $$

Each branch independently learns multiscale spatial information, allowing them to establish cross-channel interactions in a local manner. The number of parameters changes with the increase in kernel size. In order to handle input tensors with different kernel scales, group convolution is used and applied to the convolution kernel. The quantity n is the kernel size, and Z is the group size. The relationship between them is expressed as follows:

$$ Z = 2^{\frac{n-1}{2}} \quad (7) $$

As a result, the generation function for multiscale feature map is expressed as follows:

$$ H_i = Conv(n_i \times n_i, Z_i)(X) \quad i=0,1,2\dots, m-1 \quad (8) $$

The preprocessed multiscale feature map is expressed as follows:

$$ H = Cat([H_0, H_1, \dots, H_{m-1}]) \quad (9) $$
