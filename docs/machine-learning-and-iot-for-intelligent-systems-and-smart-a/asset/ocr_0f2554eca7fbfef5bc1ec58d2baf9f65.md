+   * SVM works well when there is no specific trend in the datapoints.
* No overfitting problems.
* Easy to interpret nonlinear data points.

Disadvantages

+   * Selection of right kernels.
* Training the data takes more time.
* Computationally expensive.

# ### 1.4  SKIN CANCER DIAGNOSTIC SYSTEM FOR MELANOMA DETECTION

The aim of the proposed skin cancer classification system is to detect melanoma from dermoscopic images. Here PH2 dataset is considered for experimentation that contains 200 dermoscopic images having a resolution of 768×560 pixels. Out of 200 dermoscopic images, 120 are abnormal images and 80 are normal images. (Figure 1.11a and 1.11b) depict the classification of images into normal and abnormal.

Many research works have been proposed in recent years for the classification of normal and abnormal images. In this work, various feature extraction and classification techniques are presented, and the performance of the techniques are validated to measure the accuracy of the model.

In work I, the investigation utilizes the use of shearlet transform as feature extraction and K-Nearest Neighbors as classifier for the detection of melanoma. After finishing the preprocessing module, the features are extracted using shearlet decomposition for different scales and directions. The coefficients, which are 75 and 100 coefficients to start with, are selected from shearlet sub-bands. The selected coefficients are given as input to K-NN classifier to classify the image as normal or

![](bbox=[0.2, 0.6, 0.23, 0.61])

![](bbox=[0.2, 0.64, 0.38, 0.75])

![](bbox=[0.42, 0.64, 0.61, 0.75])

![](bbox=[0.65, 0.64, 0.84, 0.75])

**FIGURE 1.11A** PH2 Datasets. Normal Images.

![](bbox=[0.2, 0.78, 0.23, 0.79])

![](bbox=[0.2, 0.83, 0.38, 0.93])

![](bbox=[0.42, 0.83, 0.61, 0.93])

![](bbox=[0.65, 0.83, 0.84, 0.93])

**FIGURE 1.11B** PH2 Datasets. Melanoma Images.