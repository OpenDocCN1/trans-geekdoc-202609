# 4.1.2. Calculation Formula for Evaluation of Foreign Object Indicator

The foreign object indicator performance index based on the target detection algorithm is the recall rate and accuracy rate, where TP + FN = 126. AveragePrecision(AP) is the integral of the PR-curve, which is the area under the curve (8)–(10):

$$Precision = \frac{TP}{TP + FP}\tag{8}$$ $$Recall = \frac{TP}{TP + FN}\tag{9}$$ $$Average\ Precision = \int_{0}^{1} Precision(Recall)\,dRecall.\tag{10}$$

# 4.2. Classification Performance Evaluation

In Figure 7, the blue dashed line is referred to as the "random chance", which means that the probability of the sample being classified as a positive or negative sample is random. In the ROC coordinate system, the classification threshold at the (0,0) point is the largest, and the classification threshold at the (1,1) point is the smallest. According to the ROC curve, it can be clearly observed that when the classification recall rate is 100% (corresponding to the ordinate value is 1), the InceptionV3-retrain model has the lowest error rate. At the same time, the InceptionV3-retrain model reduced the AUC value by 0.4% compared to the InceptionV3-fine-tuning model, but reduced the error rate by 8%.

![](bbox=[0.28, 0.48, 0.65, 0.72])

Figure 7. ROC of the classifier. (1) in the case of a 100% recall. The threshold points of the classifier are marked with triangles, indicating that all images with foreign objects can be screened when the images are classified by the threshold corresponding to the points. The abscissa value corresponding to the threshold point is the misclassification rate, which means that the triangle mark closer to the left side corresponds to the lower classification error rate, and the performance of the algorithm is better. (2) We calculate the optimal classification threshold by using the Yoden index. The optimal threshold point of the classifier is marked by a pentagon, which means that only a part of the foreign object image can be selected when the image is classified by the threshold value of the mark point, and the classification error rate is also decreased. (3) InceptionV3-fine-tuning has AUC = 0.977 as the maximum value and SVM has AUC = 0.843 as the minimum value.