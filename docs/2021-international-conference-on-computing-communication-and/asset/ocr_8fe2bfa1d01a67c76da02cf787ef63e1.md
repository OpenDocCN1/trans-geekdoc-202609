**Resize**: The original Image in the RGB plane is resized to a matrix of 376 X 520 pixels, so that all the images are of a standard common size.
**Green component extraction**: Green Component is extracted from the RGB image for better results.
**Morphological Closing**: Dilation and erosion is performed on the image using a structuring element of radius 5 pixels. Refer figure 5(3).
**Column filtering**: The image is processed by rearranging each 5 X 5 block of the image into a temporary matrix and then applying variance (@var) function on these blocks, using this, the background reduction becomes easier. Refer figure 5(4).
**Image dilation and erosion**: First dilation then erosion is performed on the image to join two nearby exudates into a single bigger exudate. Refer Figure 5(5).
**Optical disk masking and subtraction**: Optical Disk is located and subtracted from the image. Refer figure 5(6).

![](bbox=[0.1, 0.3, 0.48, 0.53])

Fig. 5. Exudates Extraction – Output.

# V. EXPERIMENTAL RESULTS

The results that are obtained by passing the csv file obtained from the feature extraction step to the Classification Learner App that is inbuilt in MATLABR2015. The classification learner app in MATLAB takes a variable as an input in the form of predictor and response for the columns present in the table and trains the model according to the classifier selected and gives the accuracy of the classification algorithm. For this program Weighted KNN, Cubic Support Vector Machine (SVM) and Simple Tree were used to check the accuracy of the feature extraction methods. Using Weighted KNN algorithm, the overall accuracy obtained is 85.8% for exudates and blood vessel feature combination. The total number of images correctly classified overall is 188 out of 219. Table 1 represent percentage of classified images in DR and Normal categories:. This class depends on the following packages for its proper functioning.

| Features | Correctly Classified Image (%) | Misclassified Image (%) |
| :--- | :--- | :--- |
| Exudates | 89.04 | 10.95 |
| Blood Vessels | 85.39 | 14.6 |
| Exudates and Blood Vessels | 85.84 | 14.16 |

Using Cubic SVM algorithm, the overall accuracy obtained is 87.2%. The total number of images correctly classified overall are 191 out of 219.

SVM give better results when both the features are used for classifying.

| Features | Correctly Classified Image (%) | Misclassified Image (%) |
| :--- | :--- | :--- |
| Exudates | 77.17 | 25.11 |
| Blood Vessels | 83.56 | 16.44 |
| Exudates and Blood Vessels | 87.21 | 12.79 |

Using Simple Tree algorithm, the overall accuracy obtained is 88.6%. The total number of images correctly classified overall are 194 out of 219. Simple Tree too, yields better results when both the features that is blood vessel and exudates are used to classify the images, although the difference is minimal.

| Features | Correctly Classified Image (%) | Misclassified Image (%) |
| :--- | :--- | :--- |
| Exudates | 88.13 | 11.87 |
| Blood Vessels | 88.13 | 11.87 |
| Exudates and Blood Vessels | 88.58 | 11.42 |

The following table 4 shows the accuracy results obtained using SVM, KNN and Simple Tree classification Algorithms for the proposed system.

| Accuracy | Classification results for feature extracted |
| :--- | :--- | :--- | :--- |
| Classifiers | Exudates | Blood Vessels | Exudates and Blood Vessels |
| Cubic SVM | 77.2% | 83.6% | 87.2% |
| Weighted KNN | 89.0% | 85.4% | 85.8% |
| Simple Tree | 88.1% | 88.1% | 88.6% |

Based on the confusion matrix values for the all the three algorithms the sensitivity and specificity is calculated for combined feature set of exudates and blood vessel in table 5. The formula for sensitivity and specificity is given below.

```
Sensitivity = TP / TP+FN
Specificity = TN / TN+FP
```

The sensitivity and specificity values show the effectiveness of proposed system. Simple tree yields sensitivity value of 98%.