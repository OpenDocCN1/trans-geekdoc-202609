
# DIABETESWEB

DASHBOARD

DIABETICS PREDICTION

DIABETICS RETINOPATHY PREDICTION

# 2019 Survey

All over the world

# Not so sweet

India has the second-highest number of diabetes patients aged 20-79 years as of 2019

China
India
U.S.
Pakistan
Brazil

- 0
- 25
- 50
- 75
- 100

# Diabetic Retinopathy

Four stage of Diabetic Retinopathy

![](img/f07153152e20646619066fcf6f1ecf5b_144_0.png)

Figure 6.4 View of Diabetes Web dashboard page 2.

Figure 6.5 Diabetes prediction page.

# Machine Intelligence

![](img/f07153152e20646619066fcf6f1ecf5b_146_0.png)

Figure 6.6 Diabetic retinopathy prediction page.

![](img/f07153152e20646619066fcf6f1ecf5b_146_1.png)

Figure 6.7 Diabetic retinopathy prediction page: choosing an image.

# DR Detection Using Machine Learning Algorithms

ImageDataGenerator constructor that specifies the minimum and maximum ranges as a float representing a percentage to select a brightness amount. Values less than 1.0 darken the image, e.g., 0.5, 1.0, whereas greater than 1.0 brighten the image, e.g., 1.0, 1.5, where 1.0 has no effect on brightness. The example in https://machinelearningmastery.com/how-to-configure-image-data-augmentation/training-deep-learning-neural-networks/ demonstrates brightness image augmentation, allowing the generator to randomly darken the image between 1.0 (no change) and 0.2 or 20 percent.

DenseNet is composed of dense blocks. In those blocks, the layers are densely connected. A dense block is a group of layers connected to all their previous layers. A single layer consists of the following:

- Batch Normalization
- ReLU activation
- 3x3 Convolution

The authors found that the pre-activation mode (BN and ReLU) before the Conv was more efficient than the usual post-activation mode.

## 6.4.2.1 Transition Layer

Instead of summing the residual as in ResNet, DenseNet concatenates all the feature maps. It would be impracticable to concatenate feature maps of different sizes. Thus, in each dense block, the feature maps of each layer have the same size. However down-sampling is essential to CNN. A transition layer is made of Batch Normalization, 1x1 Convolution, Average pooling.

## 6.4.3 DenseNet for Semantic Segmentation

The typical segmentation architecture is composed of a down-sampling path responsible for extracting coarse semantic features and an up-sampling path trained to recover the input image resolution at the output of the model. Densely Connected Convolutional Networks (DenseNets) have shown excellent results on image classification tasks. The idea of DenseNet is based on the observation that if each layer is directly connected to every other layer in a feed-forward fashion, the network will be more accurate and easier to train (Chablani, 2017). DenseNets are built from dense blocks and pooling operations, where each dense block is an iterative concatenation of the previous feature maps. This architecture can be seen as an extension of ResNets, which performs iterative summation of the previous feature maps. These small modifications have interesting implications, such as parameter efficiency, implicit deep supervision and feature use. The characteristics of DenseNet make them a very good fit for semantic segmentation as they naturally skip connections and multi-scale supervision, in the following manner:

- visualizing first 10 test images (Figure 6.8)
- visualizing images by training of DenseNet121 and predicting the scale of DR for each label (Figure 6.9)
- DenseNet121 Architecture for transfer learning (Figure 6.10) (Jee et al., 2021).

We analysed six models for diabetes prediction and also analysed two models for DR detection.

## 6.4 Dataset Description

The system's dataset comes from the Mendeley Diabetes dataset. This information was gathered from Iraqi society at the Medical City Hospital's laboratory (The Specialized Center for Endocrinology and Diabetes-Al-Kindi Teaching Hospital). The data from patients' file is extracted and entered into the database. Medical information and laboratory analysis make up the data. There are 103 patients with no diabetes, 53 with pre-diabetes, and 844 with diabetes in the database.

For diabetic prediction, the results are as shown in Table 6.1. Here the accuracy for the KNN (k nearest neighbours) algorithm, so we have connected KNN with the frontend.

For DR detection, the images are accessed from www.kaggle.com/competitions/diabetic-retinopathy-detection/data, and we have created a couple of models and the results are as shown in Table 6.2.

Here we obtained more accuracy for DenseNet so we taken DenseNet model to connect the user interface.

## 6.5 Conclusion

In this chapter, a web application called Diabetes Web is introduced to analyse the degree of diabetic retinopathy in a patient. Basic machine learning applications are used to detect if the patient is diabetic or not. Deep learning techniques such as CNN and DenseNet121 are used to analyse the retinopathy level of a patient. This application can be used by clinicians, ophthalmologists and physicians. One of the major problems faced by diabetes today is the inability to track blood sugar levels that can lead to blindness. This application can also be used for diagnosis and early recovery.

![](img/f07153152e20646619066fcf6f1ecf5b_149_0.png)
![](img/f07153152e20646619066fcf6f1ecf5b_149_1.png)
![](img/f07153152e20646619066fcf6f1ecf5b_149_2.png)
![](img/f07153152e20646619066fcf6f1ecf5b_149_3.png)

Figure 6.8 Test images. DR Detection Using Machine Learning Algorithms 125

```
test pic.1
raw output from model :
1.000 0.966 0.520 0.268 0.109
```
![](img/f07153152e20646619066fcf6f1ecf5b_150_0.png)

Figure 6.9 Testing images by training of DenseNet121.

```
test pic.2
raw output from model :
0.998 0.999 0.999 0.931
```
![](img/f07153152e20646619066fcf6f1ecf5b_150_1.png)

Figure 6.10 One deeper look at DenseNet-121. Dense Block and Transition Block.

| Algorithm | Accuracy |
|---|---|
| Logistic Regression | 71.428 |
| K nearest neighbours | 78.571 |
| Support Vector Classifier | 73.376 |
| Naive Bayes | 71.428 |
| Decision tree | 68.181 |
| Random Forest | 75.974 |

| Table 6.2 Diabetic Retinopathy Prediction Models |
| Algorithm | Accuracy |
|---|---|
| CNN | 74.4 |
| DenseNet121 | 96.4 |

# Note
1 The Diabetes Web is available from the authors at: C:/Users/Yadukishna/Downloads/yadu_web(2)/yadu_web/light-bootstrap-master/BS3/dashboard.html

# References

Antal, B. and Hajdu, A. (2014) “An Ensemble-System for Automatic Screening of APTOS (2019) “Kaggle: APTOS 2019 Blind Detection”. Available at: www.kaggle.com/c/aptros2019-blindness-detection (accessed 12 April 2021).

Bader Alazzam, M., Asher, F. and Almuhi, A. (2021) “Identification of Diabetic Retinopathy through Machine Learning”. Mobile Information Systems, 21: 1–8.

California Healthcare Foundation (2015) “Kaggle Data Repository”. Available at: www.kaggle.com/diabetic-retinopathy-detection (accessed 5 April 2021).

Chablami, M. (2017) “Towards Diabetic Science”. Available at: https://towardsdatascience.com/rdlist.com/diabetic_retinopathy/definition.htm (accessed 5 April 2021).

Conrad Stöder, M. (2021) “Definition of Diabetic Retinopathy List”. Available at: www.rdlist.com/diabetic_retinopathy/definition.htm (accessed 5 April 2021).

Douillard, A. (2018) “Deep Connected Convolutional Networks”. arXiv. 1608.06993. Available at: https://ieeplore.ieee.org/document/809972

Gondhalekar, A. (2020) Data Augmentation: Is It Really Necessary? Delhi: Analytics Vidhya. Available at: https://medium.com/analytics-vidhya/data-augmentation-is-really-necessary-b3cb12abc3cf.

Gee, G., Harvardhan, G. M., Goursaria, M. H., Singh, V., Rautaray, S. S. and Pandey, M. (2021) “Efficacy Detection of Various Bases in Single Shot Detector for Automatic Mask Location in a Post COVID Setup”. Journal of Experimental & Theoretical Artificial Intelligence, 35(3):345–364.doi: 10.1080/0952813X.2021.960638.

Narasimha-Iyer, H. A., Roys, B., et al. (2006) “Robust Detection and Classification of Longitudinal Changes in Color Retinal Fund Images for Monitoring Diabetic Retinopathy”. IEEE Transactions on Biomedical Engineering, 53: 1084–1098.

Niemijer, M., Abramoff, M. D., and van Gneeken, B. (2009) “Information Fusion for Diabetic Retinopathy CAD in Digital Color Fund Photographs”. IEEE Transactions on Imaging, 28:775–785.
