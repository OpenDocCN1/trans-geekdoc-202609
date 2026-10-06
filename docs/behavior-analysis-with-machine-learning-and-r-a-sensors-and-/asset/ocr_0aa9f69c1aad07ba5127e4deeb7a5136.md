# CHAPTER 3. PREDICTING BEHAVIOR WITH ENSEMBLE LEARNING

features as images themselves, i.e., metrics. Then, a Convolutional Neural Network (covered in chapter 8) could be trained directly from those images. For the audio part, statistical features can be extracted and stored into normal feature vectors. In this case, the two representations (views) are different. One is a matrix and the other one-dimensional feature vector. Combining them to train a single classifier could be problematic given the nature of the views and their different encoding formats. Instead, we can train two models, for each and combine the results. This is precisely the idea of Multi-view Stacking (Garcia-Ceja et al., 2018a). Train a different model for each view and combine the outputs like Stacking.

Here, Multi-view Stacking will be demonstrated using the HOME TASKS dataset. This dataset was collected from two sources. Acceleration and audio. The acceleration was recorded with a wrist-band watch and the audio using a cellphone. This dataset consists of 7 common tasks: 'm floor', 'sweep floor', 'type on computer keyboard', 'brush teeth', 'wash hands', 'eat chips', and 'watch t.v.'. Three volunteers performed each activity for approximately 3 minutes.

The acceleration and audio signals were segmented into 3 sec. windows. From each window, different features were extracted. From the acceleration, the 3 axes (x,y,z) such as mean, standard deviation, maximum values, mean magnitude, area under the curve, etc. From the audio signals, 12 features were extracted, Mel Frequency Cepral Coefficients (MFCCs). To preserve volunteers' privacy, the original audio was not released. The dataset already contains the features from acceleration and audio. The first column is the label.

In order to implement Multi-view Stacking, two Random Forests will be trained, one for each view (acceleration and audio). The predicted outputs will be stacked to form the new training set D' and a Random Forest with D' will act as the meta-learner.

The next code snippet from stacking_algorithms .R shows the multi-view stacking implemented in R.

```
mvstackacking <- function(D, v1cols, v2cols, k = 10){

# Generate folds for internal cross-validation
folds <- sample(i:k, size = nrow(D), replace = T)

trueLabels <- NULL
predicted.v1 <- NULL # predicted labels with view 1
predicted.v2 <- NULL # predicted labels with view 2
probs.v1 <- NULL # predicted probabilities with view 1
```