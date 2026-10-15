
Due to the abundance of data readily available, deep learning is growing quickly in every sphere of life. It is replacing knowledge-based applications that have predefined knowledge. The use of a lot of data to train deep neural networks is producing cutting-edge results. Earlier, neural networks were not of much use because of the unavailability of large amounts of data and processing units like GPUs (graphics processing units) and TPUs (tensor processing units) [20].

Nowadays, deep learning is used in every domain to solve problems which were not feasible or require many resources, like data, processing units like GPUs, and time. They are called deep neural networks because they contain neural networks with millions of variables in them. The tuning of these variables is known as the learning of the network. This tuning is done by providing a large amount of data so that the network can learn the relationship between the ground truth and the input variables. At first, the model will give random results, but as training goes on, it gets better and gives good results. Training accuracy and training loss are used as measures to calculate the training performance of the neural network. Once training is done, the model is evaluated on an unseen dataset known as a test dataset [21]. This evaluation tells us the actual performance quality of the model. Deep learning models during training extract the important features present in the training images and then predict the output of unseen test images based on the features learned by the training. Therefore, the models require a lot of data so that they can learn all the important features present in the images. Overfitting occurs when the model memorizes the training data and fails to perform well on the unseen data when there is less data.

## 5.8 CONVOLUTIONAL NEURAL NETWORKS

A class of neural networks called convolutional neural networks – also known as ConvNets or CNNs – is used to process data like images, videos, and signals, among other things. A digital image consists of a series of pixel values stored in a grid-like structure. These pixel values denote the colour and the brightness of the image pixel.

Like the human brain, convolutional neural networks help process data of an image for computers. The human brain processes information through large and complex structures consisting of neurons. Similarly, convolutional neural networks consist of deep hidden layers which can obtain simpler types of features like lines, edges, etc., and complex features like faces and objects from an input image. So, it is like an eye for the computer [3]. A CNN typically consists of three kinds of layers:

- 1. Convolution layer
- 2. Pooling layer
- 3. Fully connected layer

**Convolution layer:** This is the primary layer that is utilized in the process of obtaining various kinds of features from the input layer. The kernel also known as the filter is made to run over the input image and obtains the important attributes from the given image. Each time the kernel runs over the image, it performs the dot product operation with the input image pixel values and gives a two-dimensional output known as an activation map [22]. The size of the sliding of the kernel is known as stride. Consider an image of size W × W × D pixels, where D is the number of channels. When D_out number of kernels, each of size F × F with stride (S) and padding (P) are applied on the image, it gives W_out, as in Equation 5.2 below:

W_out = (W − F +2P)/S + 1  (5.2)

The size of the output volume is W_out × W_out × D_out.

### Pooling layer

This layer reduces the computational cost and the dimensions of the attribute map by removing the most important features. There are various kinds of pooling layers. The most routinely used are max pooling and average pooling layers. In max pooling, the greatest pixel value is selected from the region of the image, and in average pooling, all the pixel values over the region are averaged to give the output feature map [22]. Consider an activation map of W × W × D pixels at a particular stage, where D is the number of channels, having filter size F × F and of stride (S) gives W_out, as in Equation 5.3 below:

W_out = (W − F) / S + 1  (5.3)

The size of the output volume is W_out × W_out × D.

### Fully connected layer

In a fully connected layer, neurons from one layer are connected with each neuron in the following layer. So, this forms a full connection between each layer and the following layer. The final layer is prior to the fully connected layers at the network’s end [3].

Take the CIFAR-10 dataset as an example: here, there are 60,000 images across ten different classes in the dataset. The classes are truck, ship, horse, frog, airplane, automobile, cat, dog, bird, and deer, which are labelled from zero to nine, respectively. Out of 60,000 images, 50,000 images are reserved to train the CNN architecture and 10,000 pictures are used to test the trained network. Convolution, max pooling, and fully connected are the three layers that make up a straightforward CNN architecture. 50,000 images are used to train the network, which learns important features from the training images. The accuracy of the trained model is verified with testing data after the network has been trained [22].

Figure 5.3 shows the CNN architecture. It has two max pooling layers and two convolution layers. The network receives an input image sized 32 × 32 × 3 pixels, having 3 channels and length and width of 32, and processes it through the Conv1 layer to generate an output image sized 32 × 32 × 32 pixels, with 32 channels used. After that, it is sent to the max pooling layer, which extracts useful features to reduce the feature map. So, it reduces the size of the image to 16 × 16 × 32 pixels. Now, this is passed to the Conv2 layer and then the max pooling layer giving output image sized 8 × 8 × 64 pixels, where the number of channels used is 64. Finally, the fully connected layer connects all the preceding and succeeding neurons and maps the features to the output labels [3].

![](img/a2fc2296b12812e9151e817bff1de16d_98_0.png)

FIGURE 5.3 CNN architecture.

## 5.9 DEEP LEARNING TECHNIQUES FOR 3D CT RECONSTRUCTION

As deep learning has progressed, it has given state-of-the-art in every domain. In the medical field, deep learning is used in the classification of medical data, the segmentation of organs from medical images, 3D CT reconstruction, medical image denoising, and many other domains [17, 23]. It is used to classify whether a disease is present in images or not. Also, in segmentation like generating 3D images of organs from CT scan images. Denoising the background noise in X-ray and computed tomography pictures by deep convolutional networks helps to better understand the disease present in the body. There has been ongoing research in medical imaging using deep learning and it has helped a lot by providing state-of-the-art technologies. But there are some fields, like 3D CT reconstruction, in which much is needed to be explored [24].

Here, we will be focusing on deep neural network-based methods, which have manifested great results compared to traditional methods in 3D CT reconstruction. Deep learning-based methods have advanced significantly as a result of the abundance of available data. CNN-based methods, GAN (Generative Adversarial Network)-based methods like cyclic GAN, and a recent method based on transformers have shown better results than traditional statistical modelling-based methods. All these procedures have provided state-of-the-art three-dimensional reconstruction from two-dimensional X-ray images [20].

CT reconstruction from 2D X-ray images using deep learning-based strategies can be classified into three methods, as shown in Figure 5.4. In the first method, by using a single X-ray image, a deep learning model can estimate multiple CT images

![](img/a2fc2296b12812e9151e817bff1de16d_99_0.png)

FIGURE 5.4 Deep learning-based procedures for 3D CT reconstruction.

of various depths, thereby giving a 3D understanding. Secondly, given multiple two-dimensional X-ray images as input, a deep learning model can generate a great number of CT images, thereby enabling further insight. Thirdly, by using a single X-ray image, a deep learning model can generate a 3D structure of the scanned body part [22]. We will talk about the various deep learning models under these three categories in the following subsections.

### 5.9.1 SINGLE X-RAY INPUT TO GENERATE VOLUMETRIC CT IMAGES

CT restoration from two-dimensional X-ray images has not been observed for long; only in recent years has it evolved. Shen et al. [6] developed a deep CNN-based encoder-decoder architecture comprising three modules – a representation network, a transformation network, and a generation network – to reconstruct volumetric CT images. The experiment is conducted with different input projections (one, two, five, and ten), which are stacked together. The experiment was carried out for three different cases: lung, upper abdomen, and head and neck. The experiment gives promising results. Zhiqiang Tan et al. [11] developed XctNet, which uses a single X-ray image to reconstruct three-dimensional CT images. It uses prior knowledge from X-ray images and helps in the reconstruction of CT images. The proposed method is based on U-Net and comprises a self-attention module and a multiscale feature fusion module. Almeida et al. [13] reconstructed three-dimensional CT images using a single X-ray image by a novel deep convolutional encoder-decoder-based architecture for lower limbs. The architecture gives promising results. Jiang et al. [15] developed a GAN-based architecture for CT restoration from a single X-ray image of the lung and upper abdomen. Peng et al. [16] developed a two-stage deep CNN-based network used to restore 3D CT volumes from a single 2D X-ray input. The images used to train the architecture were from LIDC/IDRI (Lung Image Database Consortium/
