
ICAR–Central Institute of Agricultural Engineering, Nabi Bagh, Berasia, Bhopal, India

## Abstract

Traditional machine learning (ML) models and convolutional neural networks (CNN)-based deep learning (DL) models have been extensively used in the agriculture sector for plant disease detection, weed and plant classification. Color, texture, shape, and spectral features help to identify and classify objects into different classes. Traditional ML and DL algorithms for classification are simpler and faster than traditional scanning techniques or manual classification techniques. Feature extraction using transfer learning models (`VGGNet`, `AlexNet`, `GoogleNet`, and `DenseNet`) has attracted more attention than shape and texture feature extraction using traditional image processing techniques. `Python` offers several free libraries for image processing and building ML algorithms. `TensorFlow` is the most commonly used `Python` library for developing CNN-based DL models. These DL models have been converted to `TensorFlow Lite` and deployed on edge computing devices, such as `Raspberry Pi`. These advancements in science and technology will empower robots to detect pests and apply insecticides to diseased plants in the future. Moreover, robots will apply herbicides in a site-specific manner and minimize the need for herbicides.

## 9.1 Introduction

Over the last two decades, advancements in opto-electric systems, coupled with improved computational capabilities, have enabled users to capture and analyze images in real time. Image processing, machine learning (ML), and deep learning (DL)-based computer vision have been continuously used for fast and accurate detection of plant diseases and weeds in a non-destructive manner within crop fields \[[1](#ch9.xhtml#ref9_1)\]. ML allows machines to learn from datasets, rather than relying on a set of rules and explicit programming. Real-time, sitespecific application of pesticides or herbicides has become a highly promising technology in modern-day agriculture, thanks to advancements in sensing devices and high computational power of hardware components. Consequently, an automated detection system is crucial for identifying weeds and diseased plants for early diagnosis and immediate implementation of necessary control measures. An automated detection system saves time and assists farmers in improving crop quality and reducing disease occurrence through early diagnosis and prompt treatment \[[2](#ch9.xhtml#ref9_2)\].

The process of detecting plant diseases and weeds begins with image acquisition, followed by pre-processing and image segmentation. Various ML and DL models have been utilized to classify features extracted from segmented images into clusters \[[3](#ch9.xhtml#ref9_3)\]. `Google Colab`, `Microsoft Azure`, and `Kaggle Notebooks` are public cloud computing platforms that provide graphical processing units (GPU) and tensor processing units (TPU) for ML and CNN-based DL applications. `Scikit-learn` is an open-source `Python` library that assists in building regression, clustering, and classification models. `TensorFlow` is the most commonly used `Python` library for developing CNN-based DL models. ML and DL models have been applied in various agricultural applications, including crop disease identification, weed and pest classification \[[4](#ch9.xhtml#ref9_4)\].

## 9.2 Types of Features

Color, shape, texture, and spectral features of the soil background, weeds, main crops, healthy and unhealthy crops are essential for detection and classification using machine and DL models. The accuracy of color-based classification mainly depends on the color difference and the specific plant being studied. The color feature is robust to scale, position, and size \[[5](#ch9.xhtml#ref9_5)\]. The color feature is commonly used for vegetation segmentation from the soil background. The performance of several vegetation indices, such as the excess green index (`ExG`), excess red index (`ExR`), and excess green minus red index (`ExGR`), on vegetation segmentation accuracy has been extensively studied \[[6](#ch9.xhtml#ref9_6)\]. However, the color feature alone is not sufficient to classify the main crop from weeds or different types of weeds, as both the main crop and weeds are typically green in most cases.

Shape feature is the most commonly used for weeding or crop detection and crop species identification. A list of shape features is provided in [Table 9.1](#ch9.xhtml#tab9_1). Shape features have been successfully employed for plant species recognition tasks \[[7](#ch9.xhtml#ref9_7), [8](#ch9.xhtml#ref9_8)\]. Plant leaves are typically flat, with varying vein textures and leaf surface roughness. In texture-based weed or plant disease detection, the most commonly used techniques for feature extraction are given in [Table 9.1](#ch9.xhtml#tab9_1). Texture information obtained from the main crop, weeds, or diseased plants plays a significant role in classification tasks \[[9](#ch9.xhtml#ref9_9)\].

[Table 9.1 Types of Features](#ch9.xhtml#R_tab9_1)

| Category | Technique |
| --- | --- |
| **Color Feature** \[[15](#ch9.xhtml#ref9_15)\] | |
| --- | --- |
| Color models | Red (`R`), green (`G`), blue (`B`) hue (`H`), saturation (`S`), value (`V`) luminance, chrominance, chroma (`YUV`) |
| **Shape Features** \[[5](#ch9.xhtml#ref9_5)\] | |
| Shape parameters Region-based descriptorsContour-based descriptors | Perimeter, compactness, area, diameter, minor axis length, rectangularity, major axis length, circularity, eccentricity, convexity, and solidity.Two dimensional Fourier descriptors (`FD`) and `Hu` moment invariants.Spatial position descriptor, one dimensional `FD`, curvature scale descriptors. |
| **Texture Features** \[[5](#ch9.xhtml#ref9_5)\] | |
| Statistical methodStructural methodModel-based methodTransform-based method | Gray level co-occurrence matrix (`GLCM`): 10 statistics, gray level gradient co-occurrence matrix (`GGCM`): 15 statistics.Local binary pattern (`LBP`)Fractal dimension`Gabor`-based |

Along with color, shape, and texture features, spectral features also play a significant role in plant or weed classification problems. When the spectral reflectance of the weed class is significantly different from the main crop’s spectral feature, it can be employed to distinguish weeds from the main crop \[[10](#ch9.xhtml#ref9_10)\]. Compared to shape and texture features, the spectral feature is robust to partial occlusion of leaves \[[11](#ch9.xhtml#ref9_11)\]. Researchers have investigated the use of fluorescence \[[12](#ch9.xhtml#ref9_12)\], multispectral or hyper-spectral imaging (`HIS`) \[[13](#ch9.xhtml#ref9_13)\], visible and near-infrared spectra \[[14](#ch9.xhtml#ref9_14)\] for the classification of plants and weeds.

## 9.3 Types Of Machine Learning (Ml) Models

Machine learning (`ML`) models are divided into regression, classification, and clustering. Regression and classification techniques are called supervised learning algorithms. The class label or target is a continuous variable for regression problems ([Figure 9.1](#ch9.xhtml#fig9_1)). However, the class label is a categorical variable in the case of classification and clustering problems. The clustering algorithms are called unsupervised learning algorithms. Supervised `ML` models require features and corresponding true labels to train and test the models. Linear regression, decision trees (`DT`), logistic regression (`LR`), artificial neural network (`ANN`), random forest (`RF`), support vector machine (`SVM`), and K-nearest neighbors (`KNN`) are supervised `ML` models.

![Figure 9.1 Types of machine learning (`ML`) models.](images/fig9_1_B.jpg)

[Figure 9.1 Types of machine learning (`ML`) models.](#ch9.xhtml#R_fig9_1)
