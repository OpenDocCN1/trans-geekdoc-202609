
![](img/1752b062af2760b8561f6faaf183b3d0_143_0.png)

**Figure 6.** Convolutional operation using local connections.

## Ground Truth Preparation for Real Ocean Environment

After testing the CNN system with perfect images without noise. The next step is to build our own dataset of fish in the ocean. Because it is difficult to obtain images from other kinds of objects such as the sea turtle, coral and so on. As part of the research, fish is the only object to be detected. For the collection of 410 images, many of them have multiple fish in one image, so the detection is challenging. The same method was chosen to create ground truth image. And all the parameters introduced before remain the same, only the class information is made up of a 1×1×18 vector instead of 1×1×30 because of the reduction in the classes. Figure 11 illustrates one labeled image example. It is obvious that this data set is totally different from the ideal images from ImageNET.

## DATA AUGMENTATION

Since deep learning is based on large training dataset for the system to learn and build up the identification knowledge, enough data has to be provided as learning resources to extract object features [34].

The lacking of data would bring overfitting problem. Images were collected in real underwater environment from the Gulf of Mexico and are going to be used to extract object features. However, the number of original images collected from a particular environment is not large enough to train the system. Therefore, data augmentation transformation was performed geometrically, which changed the pixels location while the images features remained unchanged as shown in Figure 12. Four types of data augmentation transformation were adopted, which doubled the number of original images to make the training dataset sufficient.

- (1) Rotation: rotate the images by random angles;
- (2) Scale: the images are scaled to different sizes according to scale factors set;
- (3) Crop: crop patches of images;
- (4) Mirror symmetry: flip the original images horizontally or vertically

## Dropout Algorithm

One of the common problems in deep learning is overfitting, which refers to the fact that the testing accuracy is much lower than the training accuracy. In this case, a model with high performance feature is built using real world training data.

If it turns out to have overfitting issue, the robustness of the model is worth consideration. Apart from the lacking of learning data, which will also cause overfitting problem, the huge amount of parameters in a neural network would lead to the overfitting issue. Therefore, the dropout algorithm [35] was introduced into the system to simplify the model, which is depicted in Figure 5.

Table 1. Parameters in CNN model with image segmentation

| Layer | Input size | Filter size | Stride | Output size |
| :--- | :--- | :--- | :--- | :--- |
| Conv. 1 | [N x 448 x 448 x 3] | [7x7x3x64] | 2 | [N x 224 x 224 x 64] |
| Maxpool 1 | [N x 224 x 224 x 64] | [2 x 2] | 2 | [N x 112 x 112 x 32] |
| Conv. 2 | [N x 112 x 112 x 32] | [3 x 3 x 32 x 192] | 1 | [N x 112 x 112 x 192] |
| Maxpool 2 | [N x 112 x 112 x 192] | [2 x 2] | 2 | [N x 56 x 56 x 96] |
| Conv. 3 | [N x 56 x 56 x 96] | [3 x 3 x 128 x 256] | 1 | [N x 56 x 56 x 256] |
| Conv. 4 | [N x 56 x 56 x 128] | [3 x 3 x 128 x 256] | 1 | [N x 56 x 56 x 256] |
| Conv. 5 | [N x 56 x 56 x 256] | [1 x 1 x 256 x 256] | 1 | [N x 56 x 56 x 256] |
| Conv. 6 | [N x 56 x 56 x 256] | [3 x 3 x 256 x 512] | 1 | [N x 56 x 56 x 512] |
| Maxpool 3 | [N x 56 x 56 x 512] | [2 x 2] | 2 | [N x 28 x 28 x 256] |
| Conv. 7 | [N x 28 x 28 x 256] | [1 x 1 x 256 x 256] | 1 | [N x 28 x 28 x 256] |
| Conv. 8 | [N x 28 x 28 x 256] | [1 x 1 x 256 x 256] | 1 | [N x 28 x 28 x 256] |
| Conv. 9 | [N x 28 x 28 x 256] | [1 x 1 x 256 x 256] | 1 | [N x 28 x 28 x 256] |
| Conv. 10 | [N x 28 x 28 x 256] | [1 x 1 x 256 x 256] | 1 | [N x 28 x 28 x 256] |
| Conv. 11 | [N x 28 x 28 x 256] | [3 x 3 x 256 x 512] | 1 | [N x 28 x 28 x 512] |
| Conv. 12 | [N x 28 x 28 x 512] | [3 x 3 x 512 x 512] | 1 | [N x 28 x 28 x 512] |
| Conv. 13 | [N x 28 x 28 x 512] | [3 x 3 x 512 x 512] | 1 | [N x 28 x 28 x 512] |
| Conv. 14 | [N x 28 x 28 x 512] | [3 x 3 x 512 x 512] | 1 | [N x 28 x 28 x 512] |
| Conv. 15 | [N x 28 x 28 x 512] | [1x1x512x512] | 1 | [N x 28 x 28 x 512] |
| Conv. 16 | [N x 28 x 28 x 512] | [3x3x512x1024] | 1 | [N x 28 x 28 x 1024] |
| Maxpool 4 | [N x 28 x 28 x 1024] | [2x2] | 2 | [N x 14 x 14 x 512] |
| Conv. 17 | [N x 14 x 14 x 512] | [1x1x512x256] | 1 | [N x 14 x 14 x 256] |
| Conv. 18 | [N x 14 x 14 x 256] | [3x3x256x1024] | 1 | [N x 14 x 14 x 1024] |
| Conv. 19 | [N x 14 x 14 x 1024] | [1x1x1024x512] | 1 | [N x 14 x 14 x 512] |
| Conv. 20 | [N x 14 x 14 x 512] | [3x3x512x1024] | 1 | [N x 14 x 14 x 512] |
| Conv. 21 | [N x 14 x 14 x 1024] | [3x3x512x1024] | 1 | [N x 14 x 14 x 1024] |
| Conv. 22 | [N x 14 x 14 x 1024] | [3x3x1024x1024] | 1 | [N x 7 x 7 x 1024] |
| Conv. 23 | [N x 7 x 7 x 1024] | [3x3x1024x1024] | 2 | [N x 7 x 7 x 1024] |
| Conv. 24 | [N x 7 x 7 x 1024] | [3x3x1024x1024] | 1 | [N x 7 x 7 x 1024] |
| Fully conn. 1 | [N x 7 x 7 x 1024] | [1024x4] | Multi | [1x4096] |
| Fully conn. 2 | [1x4096] | [4096x7x7x30] | Multi | [7x7x30] |

![](img/1752b062af2760b8561f6faaf183b3d0_145_0.png)

**Figure 7.** CNN architecture for object identification [26].

![](img/1752b062af2760b8561f6faaf183b3d0_145_1.png)

**Figure 8.** Output of CNN model using ImageNET.

![](img/1752b062af2760b8561f6faaf183b3d0_146_0.png)

**Figure 9.** Intersection over union.

![](img/1752b062af2760b8561f6faaf183b3d0_146_1.png)

**Figure 10.** Object classification results from ImageNET data set.

![](img/1752b062af2760b8561f6faaf183b3d0_146_2.png)

**Figure 11.** Labeled ground truth.

Dropout means that we remove some nodes temporarily from the network according to the probability setting in the process of learning. In practice, some features can be extracted only when some hidden relationships exist, which decreased the robustness of the deep learning model. On the other hand, dropout removes a hidden fixed relationship between nodes, anti-interference ability can be improved and overfitting problem can be solved to some extent. L1 and L2 regularization are achieved by modifying the cost function, while dropout is implemented by modifying the neural network itself, which is a technique used when training the network. In each iteration of the training process, authors randomly drop some of the neurons, and set the probability of eliminating nodes in the neural network for each layer of the network. For example, the value is set to 0.5, as shown in Figure 13 on the left. The neurons are discarded, then the connections from the node are removed, and finally a network with fewer nodes and smaller scales is obtained. The network structure during this training will be simplified to the one shown in Figure 13 on the right.

![](img/1752b062af2760b8561f6faaf183b3d0_147_0.png)

**Figure 12.** Data augmentation transformation.

![](img/1752b062af2760b8561f6faaf183b3d0_147_1.png)

**Figure 13.** A standard neural network model (a) and a network model with dropout (b) [35].

## Refine Loss Function

YOLO improved loss function from Equations (4) and (5), [26]. Three coefficients were placed before the error terms in proportion to its contribution to the loss. As shown in Equation (5), the first two terms are related to coordinate the identified object with x and y to denote the object location, while w and h refer to the width and height of the bounding box. In order to have more weight in the first two terms, \(\gamma_{coord}\) was assigned to be the largest number, which had a value of 5. Thus, the weight of localization error got enhanced. In terms of IoU error computation, when the object center falls in this cell, the weight of IoU error should be increased in order to predict location accurately. The value of \(\gamma_{noobj}\) is set to be 0.5 to refine the IoU error. For the same error value, the effect of large object error on the detection should be less than the effect of small object error on the detection. This is because the same bias accounts for the proportion of large objects is much smaller than the proportion of the same deviation to small objects. Therefore, it is supposed to increase the contribution to loss due to bigger object IoU error. Square roots of width and height were chosen to replace their original forms. For same bias value, the square root error from the big box is smaller than the small one.

![](img/1752b062af2760b8561f6faaf183b3d0_148_0.png)

**Figure 14.** Enhancement of identification accuracy with data augmentation.

![](img/1752b062af2760b8561f6faaf183b3d0_148_1.png)

**Figure 15.** Comparison of training loss.
