
## 13.1.2 CNN (CONVOLUTIONAL NEURAL NETWORK)

Convolutional neural networks (CNNs) serve the purpose of image classification and recognition. CNNs automatically extract features from images, unlike traditional neural networks. CNNs use convolutional layers to apply learnable filters to input images. These filters identify edges and textures, and the convolutional layer output is routed via nonlinear activation functions to build a feature map. Pooling layers downsample the feature maps to minimize their spatial dimensions while retaining the most relevant characteristics. CNNs finish with fully connected layers to classify learned features. Backpropagation with stochastic gradient descent reduces a loss function by modifying filter weights and biases.

CNNs excel at picture classification, object recognition, and segmentation. Natural language processing, voice recognition, and other applications employ them.

## 13.2 RELATED WORK

Proposal for three datasets on masked faces: mask occlusion face detection dataset, real-world masked face recognition dataset (RMFRD), and synthetic masked face recognition dataset [1]. These datasets would be free for both academia and industry to use to make different applications for masked faces. RMFRD is the biggest real-world facemask dataset in the world right now [2]. Study and overview of image segmentation techniques in CNN, covering region-based, feature extraction, clustering, and loosely supervised learning, with a forecast of image segmentation development trend [3]. Implementation of a technique using computers for the detection and segmentation of brain tumors in magnetic resonance (MR) images, reducing analysis time, and displaying the tumor's exact position and shape [5]. The creation of a technically enabled drone for recognition of mask and social distancing surveillance, which uses a quicker R-CNN model to find people who do not have their face masked and send out notifications to keep people apart [7] from creating a neural network approach (region proposal network) that works with the detection network to share full-image convolutional features allows for practically cost-free area proposals and achieves the highest item detection performance on PASCAL VOC 2007 and 2012 [9] masked face detection using MobileNetV2 architecture with two-layer max pooling, average pooling, with high training, and validation accuracy [10]. Using the ResNet-50 architecture, as a superresolution and classifier framework, arbitrary trigonometric transform-based convolution with multilayer perceptron is employed for tumor identification and classification, obtaining 98.14% accuracy rate.

## 13.3 PROBLEM FORMULATION

### 13.3.1 PROBLEM STATEMENT

The COVID-19 has made us rethink our daily routines. Face masks are a popular and effective way to reduce infection risk. Face mask detection devices are in demand for safety. This project extends points to build a profound learning-based face mask detector to prevent coronavirus spread utilizing image processing algorithms for improved optimization.

### 13.3.2 PROBLEM DESCRIPTION

Due to its contagious and sometimes fatal characteristics, the coronavirus has become a major health concern in recent years. Exhalation transfers viral particles to surfaces that susceptible people breathe in, infecting them. We must avoid people, wash our hands, and use masks to avoid this situation. Due to its enormous population density, India is the most affected by public mask use.

A convolutional neural network can detect face masks in vast workplaces. Real-world data trains and live video streams validate the model. Testing hyperparameters, more people at varied distances, and frame positioning determines the model’s precision. Disinfectant and hand washing are also advised.

## 13.4 SYSTEM DESIGN

### 13.4.1 HIGH-LEVEL SYSTEM ARCHITECTURE

- 1. Data collection: Gather a database of pictures of individuals wearing and not wearing masks.
- 2. Data preprocessing: Divide the existing dataset into three parts, namely training, validation, and testing, and resize the photos, supplement the data (rotate, flip, alter brightness/contrast), and also implement the preprocessing image algorithms.
- 3. Feature extraction: Extract features from the images using a pretrained ResNet-50 model.
- 4. Fine-tune the model: Adjust the model by adding a few more layers to distinguish between “with mask” and “without mask” image classifications.
- 5. Model evaluation: Assess the performance of the model on the validation set and make any required adjustments to the hyperparameters.
- 6. Deployment: Deploy the model as an application that can analyze live video or still photos from a camera and decide whether or not individuals in them are wearing masks, then respond appropriately (e.g., alerting a security guard, denying entry to a building, etc.).

### 13.4.2 SYSTEM ARCHITECTURE

The following three components make up the whole of the proposed system in its entirety (Figure 13.1).

![](img/e7e1b4040cce350b0d1520d1f0df754d_233_0.png)

FIGURE 13.1 System architecture for facemask detection.

### 13.4.3 DATASET

For the purpose of this study, we are utilizing different datasets in order to produce results that are more precise and accurate. We are creating a more accurate dataset with the help of Masked Face Net [12], face mask dataset [9], face mask detection data [10], face mask detection [11] 12k images dataset, and masked face recognition dataset and application. This dataset will have over 6000 images of people wearing masks and approximately 5100 images of people without masks. We planned the dataset in such a way that it would include both generic and medical masks, each of which would have a variety of colors and textures.

The dataset aims to detect whether people are wearing masks or not. Additionally, a mask-to-face deformable model is presented in this study, enabling the creation of additional masked face pictures using certain masks. This dataset provides a granularity of classification that permits mask-wearing analysis, making it a valuable resource for research on masked face recognition (Figure 13.2).

![](img/e7e1b4040cce350b0d1520d1f0df754d_234_0.png)

FIGURE 13.2 View of the dataset.

## 13.4.4 PREPROCESSING AND SEGMENTATION

### 13.4.4.1 BILINEAR INTERPOLATION

Bilinear interpolation estimates pixel values between neighboring pixels on a regular grid in image processing and computer graphics. The weighted average of the four closest known pixels is used to estimate the value of an unknown pixel.

The method estimates the pixel value by weighting the distance between the unknown pixel and its nearby known pixels. The equation uses weights from each known pixel to the unknown pixel. The interpolated value takes into account the unknown pixel’s proximity to a known pixel.

Bilinear interpolation helps resize photos. The technique estimates new pixel values between known pixels when a picture is enlarged, delivering a smoother result than duplicating pixels. Bilinear interpolation can estimate pixel values to preserve image quality when reducing image size (Figure 13.3).

![](img/e7e1b4040cce350b0d1520d1f0df754d_235_0.png)

Overall, bilinear interpolation is a simple and effective method for estimating pixel values in image processing and computer graphics, particularly in situations where smooth transitions between adjacent pixels are desired.

### 13.4.4.2 BILATERAL FILTER

Image processing often uses the bilateral filter. It weights pixels based on their spatial and intensity distances and averages them. The filter smoothens photos while preserving borders, texture, and small details.

The bilateral filter calculates the space and intensity distance between the center pixel and the surrounding pixels. Bigger disparities in pixel values are given less weight when calculating intensity distance. Pixels closer together are weighted more in the Euclidean distance calculation. Multiplying the intensity and distance weights yields a weighted average of nearby pixel weights. Pixel outputs are weighted averages of surrounding pixels. Similar-intensity pixels nearby weighted more (Figure 13.4).

![](img/e7e1b4040cce350b0d1520d1f0df754d_236_0.png)

FIGURE 13.4 Bilateral filter.

Overall, the bilateral filter is used in image processing applications such as denoising, texture removal, and picture enhancement. It smoothens pictures while keeping edges and other high-frequency details.

### 13.4.4.3 FUZZY C-MEAN SEGMENTATION

Image segmentation often uses the unsupervised fuzzy c-mean segmentation (FCM) clustering algorithm. Data points can belong to several clusters with varying degrees of affiliation using the FCM method. FCM can partition images using pixel values. Each pixel’s membership value reflects its cluster affiliation.

The algorithm updates the cluster centroids and membership values iteratively until convergence, having the aim of lowering the distance between the data points and the cluster centroids. FCM is capable of dealing with visual ambiguity and overlap, making it appropriate for picture segmentation.
