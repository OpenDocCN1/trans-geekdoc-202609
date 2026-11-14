![](bbox=[0.136, 0.07, 0.349, 0.233])

![](bbox=[0.387, 0.07, 0.604, 0.233])

![](bbox=[0.646, 0.07, 0.864, 0.233])

Meteor (BRAMON)

Meteor (UKMON)

Meteor (BOAM)

![](bbox=[0.264, 0.277, 0.481, 0.442])

![](bbox=[0.515, 0.277, 0.732, 0.442])

Non-meteor (BRAMON)

Non-meteor (UKMON)

Fig. 1. Examples of meteor and non-meteor images from different data sources.

Similarly, UKMON has an extensive network with 195 operating cameras in the United Kingdom. A standard detection kit, including an IMX291 POE camera, a 4 mm camera lens, and other accessories, is sold to connect to its system. Therefore, many of the raw images from UKMON are in grayscale with similar resolutions and aspect ratios. To take advantage of these characteristics, we collected approximately 17% of images of meteors and 13% of images of non-meteors from this source.

# 3.3.1. Model architectures

In turn, BOAM has 12 active operating stations that cover almost all of France’s territory. Researchers can collect various data from the BOAM repository, such as images, videos, and metadata. Here, we only extracted the image files containing meteor occurrences since only meteors are registered, representing approximately 17% of the meteor class in the dataset.

In our implementation, we used the learned weights trained on the ImageNet dataset from a VGG16 model (Simonyan and Zisserman, 2015). The VGG family outperformed other CNN architectures, such as DenseNet, Inception-V3, and ResNet, for a dataset of 7000 images (Dawson et al., 2023).

# 3.2.2. Dataset splits

From that network, we built two modified versions of the VGG16 architecture, as Fig. 2 depicts. First, we customized the VGG16 using Batch Normalization (BN) (Ioffe and Szegedy, 2015) and Dropout layers (Srivastava et al., 2014). We are aware that combining them may lead to worse performance in many modern neural networks, including CNNs, due to variance shifts (Li et al., 2019). However, these were essential techniques to reduce the computation time and prevent the model from overfitting.

In our study, we considered the split approach of the dataset performed by Dawson et al. (2023). Their work also applied a CNN architecture to classify images with the same dimensions as the meteor dataset but for the carbonate rock problem. Therefore, we split the dataset into 80% training and 20% test data. Finally, we used the training data with stratified cross-validation to create five folds of the 80% training data and the 20% validation data to evaluate the reliability of the prediction. The training and validation sets represent 64% and 16% of the total dataset.

Therefore, we added only one dropout layer before the softmax layer and set the drop ratio at 0.2, as suggested by Li et al. (2019). Next, we placed a BN layer before each max pooling layer and a second Dropout layer with a drop ratio of 0.2 before a single dense layer of 16 units. We also substituted the flattening layer with a Global AveragePooling 2D layer to reduce the feature maps towards easily understood by the single classification layer.

# 3.3. Implementation details

The basic idea of attention mechanisms is to exploit the concept of human attention by focusing on essential features and suppressing unnecessary ones. Therefore, attention also improves the representation of interests (Woo et al., 2018). In this sense, it can improve the model generalization by correctly selecting the key features to discriminate meteors from other events on limited data.

In this section, we present the implementation details of the proposed approach. We describe two comparative model architectures from the VGG16 network and the optimized training settings.

The second architecture uses the previous model to investigate that strategy but with the addition of Convolutional Block Attention Module (CBAM) attention mechanisms (Woo et al., 2018). We nominate this architecture as VGG16+CBAM. Woo et al. (2018) specifically designed the CBAM attention mechanism to boost the representation power of CNNs, consisting