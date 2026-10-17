
transfer of the pretrained model may provide the new target model with a powerful feature extraction capability and reduce its training computations and memory cost. Transfer learning has been used extensively in medical imaging, and it showed a great efficacy in terms of accuracy, training time, and error rates \[10, 31, 32\]. In this paper, we present a modified pretrained model, AlexNet, that has been employed for the classification of CT brain haemorrhage images into normal and abnormal classes.

`# AlexNet`

AlexNet is the first convolutional neural network that achieved the highest classification accuracy at the ImageNet Large Scale Visual Recognition Challenge (ILSVRC) in 2012 \[10\]. This deep structure is comprised of eight main layers; the first five layers are mainly convolutions, while the last three are fully connected layers. Each convolutional layer is followed by an activation function layer, i.e., rectified linear units layer (ReLU), proposed to improve the performance of the network by making the training faster than equivalents of “tanh” activation functions \[10\]. After each convolution layer, a max pooling is used in AlexNet, in order to reduce the network size.

Moreover, a dropout layer is added after the first two fully connected layer which helps to reduce the number of neurons and prevent overfitting \[33\].

Finally, a layer is added after the last layer to classify the input given data.

Figure 1 shows the structure of the AlexNet.

## MATERIALS AND METHODS

This work addresses the problem of the classification of the CT brain images into normal or haemorrhage, which can be a hard task for some junior radiologists and doctors. The problem is addressed by the implementation of a deep learning network trained extensively to acquire the power of extracting low to high levels of features from normal brain CT images and 本书版权归Arcler所有

![Image 976](index-224_1.png)

![Image 977](index-224_2.png)

![Image 978](index-224_3.png)

Deep Learning Algorithms

198

others with haemorrhage medical conditions using its designed and trained filters. These features are then what distinguishes the class of the brain images, i.e., haemorrhage or not. Nonetheless, the transfer of knowledge from original to target task, which is here Haemorrhage identification, is also considered by transferring the knowledge of a pretrained model known as AlexNet, into a new classification task and testing it by the same number of images used for testing the CNN created from scratch.

In this manner, we aim to address the central issue in medical image analysis and diagnosis: training deep CNN from scratch is not needed;

' # ¶~

+

' <#

CNN created from scratch and the pretrained models will demonstrate the truth and accuracy behind this central issue.

## Data

The two employed models are trained and tested using normal and diseased brain computer tomography (CT) images collected from the Aminu Kano Teaching Hospital, Nigeria \[34\]. It is important to note that the abnormal images collected from this database are of different types of haemorrhage, but they were all labeled as haemorrhage, because this work aims to classify whether the CT slice contains haemorrhage or not; haemorrhage identification from set of images regardless of the haemorrhage pathology type it may have is feasible \[35\].

## Data Augmentation

Deep networks are data-hungry systems \[36\], hence the more data you feed them, the more powerful and accurate they become. Therefore, in this work we decided to use data augmentation in order to multiply the number of images collected for the database, which can help in preventing the overfitting that may be encountered during training \[37\].

< $ {

and 270 degrees. Overall, a total number of 12635 normal and haemorrhage CT brain images are obtained. Note that 70% of the data are used for training the employed networks while 30% are used for testing, i.e., 8855 and 3790

images, respectively. Table 1 shows the learning scheme that is used in this work.

本书版权归Arcler所有

![Image 979](index-225_1.png)

![Image 980](index-225_2.jpg)

![Image 981](index-225_3.png)

![Image 982](index-225_4.png)

![Image 983](index-225_5.png)

Application Of Deep Learning In Neuroradiology: Brain Hemorrhage ...

199

**Table 1**. Learning scheme of the networks.

Figure 2 shows some normal and haemorrhage CT slices of the brain that are the used for training and testing the deep networks.

**Figure 2**. Sample of the databases training and validating images. (a) Haemorrhage images; (b) normal images.

The images of this database are originally of size 1024 1024 1 pixels;

227 227 3.

Note that we decided to use the same input images size for the CNN

created from scratch, only for networks performance comparison purposes, although any size could be used. Moreover, the images of the database are of grayscale type, and since the AlexNet model requires 3-channels input data, images were all converted to RGB by concatenating their grayscale channel for three times to become 227 227 3.

## Training the Network Models

The two employed deep models are simulated using MATLAB environment.

The networks were trained on a Windows 64-bit desktop computer with an Intel Core i7 4770 central processing unit (CPU) and 16 GB random access memory. It is important to mention that there was no graphical processing unit (GPU) available in the used desktop.

本书版权归Arcler所有

![Image 984](index-226_1.jpg)

![Image 985](index-226_2.jpg)

![Image 986](index-226_3.png)

![Image 987](index-226_4.png)

![Image 988](index-226_5.png)

Deep Learning Algorithms

200

The performance evaluation of the networks was carried out using a held-out test set 30% of the data. The calculation of the loss and accuracy was achieved as follows:

(1)

`| ##`

number of images, while N is the total number of images during the training and/or testing phases.

***CNN Training***

The model architecture and training settings for the CNN employed to perform the classification of brain haemorrhage are presented in this section. Extensive tests are performed to determine the best learning parameters that optimize the neural network.

Note that out of the retrieved 12635 brain CT images, 8855 images are used for training and 3790 images are used for validating the trained network.

< #

images is shown in Figure 3, where “Conv” denotes a convolution layer,

“BN” denotes batch normalization, “FM” denotes feature maps, and “FC”

denotes fully connected layer.

In this paper, all convolution operations are performed using convolution

! »!

'! »

! ”

For designing the proposed architecture, we take into consideration the size of available (i.e., limited) training data for constructing a learning model that is considerably regularized.

For example, we employ batch normalization and dropout training schemes which have been shown to improve model generalization \[38–40\].

For optimizing the proposed model, we employ minibatch optimization via gradient descent; we use a batch size of 60. In addition, we use a learning rate of 0.001 and train the model for 100 epochs. The learning curve for the trained CNN is shown in Figure 4; a validation accuracy of 90.65% is achieved.

本书版权归Arcler所有

![Image 989](index-227_1.jpg)

![Image 990](index-227_2.png)

![Image 991](index-227_3.png)

![Image 992](index-227_4.png)

Application Of Deep Learning In Neuroradiology: Brain Hemorrhage ...

201

**Figure 3**. Proposed CNN architecture.

In addition, we observe a slight drop in validation performance when dropout and batch normalization are not employed for training the model; a validation accuracy of 87.33% is obtained. e overall proposed

\# < #
