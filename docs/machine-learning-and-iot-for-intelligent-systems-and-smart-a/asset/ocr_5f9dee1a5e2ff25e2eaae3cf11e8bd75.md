![](bbox=[0.2, 0.09, 0.82, 0.34])

# **FIGURE 1.13** KNN Classifier Performance.

From the comparison of results, it is evident that the 100-coefficient extracted from the second level of decomposition produces better performance accuracy compared to the 75-coefficient from any decomposition level.

In work II, Poovizhi et al. [23] carry out bendlet transform for feature extraction and support vector machines as classifier to demonstrate how to classify normal and abnormal images from PH2 dataset. The proposed work is compared with the other image decomposition methods discussed in section 1.3. Initially the preprocessing is done by median filtering method to remove unwanted noise and hair from the dermoscopic images. The statistical features such as texture descriptors are extracted by bendlet decomposition. The energies are calculated from the coefficients of sub-bands obtained from bendlet transform. Then, the features are ploughed into support vector machines to classify normal and abnormal images. (Figure 1.14) depicts the block diagram of bendlet and SVM based SCC system.

The validation is carried out by k-fold cross validation, and the performance metrics such as sensitivity, specificity and accuracy are measured.

+   - Where, $T_{r}P_{b}\to$ True Positive (#correct classification of abnormal cases), $F_{r}N_{c}\to$ False Negative (#misclassification of abnormal cases), $T_{r}N_{c}\to$ True Negative (#correct classification of normal cases) and $F_{r}P_{o}\to$ False Positive (#misclassification of normal cases)

Table 1.3 reviews the performance of classification system for classification of normal and abnormal images. The decomposition level (from 1 to 4) and directions (2,4,8,16,32) are computed.

It is observed from Table 1.4 that bendlet transform with level 3 and direction 8 performs better with 98.50% accuracy, sensitivity of 97.50%, and specificity of 100%. (Figure 1.15) depicts the performance of various image representation techniques.

From the performance comparison of wavelet, curvelet, contourlet, shearlet and bendlet, it is bendlet transform whose sensitivity, specificity and accuracy are better compared to other representation systems.