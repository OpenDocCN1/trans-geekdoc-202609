
# CHAPTER 3. PREDICTING BEHAVIOR WITH ENSEMBLE LEARNING

New train set D'

![](img/91c149cc24c3e5af2971580c9dda9d8b_122_0.png)

Figure 3.5: Process to generate the new train set D' for the meta-learner by column-binding predictions of the first-level learners and adding the true labels.

In the next section, I will introduce Multi-view Stacking which basically is the same as Generalized Stacking but each first-level learner is trained with features from a different view.

## 3.4 Multi-view Stacking for Home Tasks Recognition

```
stacking_algorithms.R stacking_activities.R
```

Multi-view learning refers to the case when an instance can be characterized by two or more independent ‘views’. For example, one can extract features for webpage classification from a webpage’s text also from the links pointing to it. Usually, there is the assumption that the views are independent and each is sufficient to solve the problem. Then, why combine them? In many cases, each view provides additional and complementary information, thus allowing to train better models.

The simplest thing one can do is to extract features from each view, aggregate them, and train a single model. This approach usually works well but it has some limitations. Each view may have different statistical properties, thus different types of models may be needed for each view. When aggregating features from all views, variable correlations may be introduced which could impact the performance. Another limitation is that features need to be in the same format (feature vectors, images, etc.), so they can be aggregated.

For video classification, we could have two views. One represented by sequences of images, and the other one by the corresponding audio. For the video part, we could encode the features as images themselves, i.e., metrics. Then, a Convolutional Neural Network (covered in chapter 8) could be trained directly from those images. For the audio part, statistical features can be extracted and stored into normal feature vectors. In this case, the two representations (views) are different. One is a matrix and the other one-dimensional feature vector. Combining them to train a single classifier could be problematic given the nature of the views and their different encoding formats. Instead, we can train two models, for each and combine the results. This is precisely the idea of Multi-view Stacking (Garcia-Ceja et al., 2018a). Train a different model for each view and combine the outputs like Stacking.

Here, Multi-view Stacking will be demonstrated using the HOME TASKS dataset. This dataset was collected from two sources. Acceleration and audio. The acceleration was recorded with a wrist-band watch and the audio using a cellphone. This dataset consists of 7 common tasks: 'm floor', 'sweep floor', 'type on computer keyboard', 'brush teeth', 'wash hands', 'eat chips', and 'watch t.v.'. Three volunteers performed each activity for approximately 3 minutes.

The acceleration and audio signals were segmented into 3 sec. windows. From each window, different features were extracted. From the acceleration, the 3 axes (x,y,z) such as mean, standard deviation, maximum values, mean magnitude, area under the curve, etc. From the audio signals, 12 features were extracted, Mel Frequency Cepral Coefficients (MFCCs). To preserve volunteers' privacy, the original audio was not released. The dataset already contains the features from acceleration and audio. The first column is the label.

In order to implement Multi-view Stacking, two Random Forests will be trained, one for each view (acceleration and audio). The predicted outputs will be stacked to form the new training set D' and a Random Forest with D' will act as the meta-learner.

The next code snippet from stacking_algorithms.R shows the multi-view stacking implemented in R.

```
mvstackacking <- function(D, v1cols, v2cols, k = 10){

# Generate folds for internal cross-validation
folds <- sample(1:k, size = nrow(D), replace = T)

trueLabels <- NULL
predicted.v1 <- NULL # predicted labels with view 1
predicted.v2 <- NULL # predicted labels with view 2
probs.v1 <- NULL # predicted probabilities with view 1
probs.v2 <- NULL # predicted probabilities with view 2

# Perform internal cross-validation.

```
for(i in 1:k){
  train <- D[folds != i
```

```
((probs.v1 + probs.v2) / 2),
pred1 = predicted.v1,
pred2 = predicted.v2)
```

```
#train meta-learner
metalearner <- randomForest(label ~,
metaFeatures, nt = 100)
```

```
res <- structure(list(metalearner=metalearner,
learnerV1=learnerV1,
learnerV2=learnerV2,
v1cols = v1cols,
v2cols = v2cols,
class = "mvstacking")
```

```
return(res)
}
```

The first argument D is a data frame containing the training data. v1cols and v2cols are the column names of the two views. Finally, argument k specifies the number of folds for the internal cross-validation to avoid overfitting (Steps 2 and 3 as described in the generalized stacking procedure).

The function iterates through each fold and trains a Random Forest with the train data for each of the views. Within each iteration, the trained models are used to predict the labels and probabilities on the internal test set are concatenated across all folds (predicted.v1, predicted.v2).

After cross-validation, the meta-features are generated by creating a data frame with the predictions of each view. Additionally, the average of class probabilities is added as a metafeature. The true labels are also added. The purpose of cross-validation was to avoid overfitting but at the end, we do not want to waste data so that both learners are re-trained with all data.

Finally, the meta-learner which is also a Random Forest is trained with the meta-features data frame. A list with all the required information to make predictions is created. This includes first-level learners, the meta-learner, and the column names for each view we know how to divide the data frame into two views at prediction time.

The following code snippet shows the implementation for making predictions using a trained stacking model.

```
mvstackacking <- function(D, v1cols, v2cols, k = 10){

# Generate folds for internal cross-validation
folds <- sample(1:k, size = nrow(D), replace = T)

trueLabels <- NULL
predicted.v1 <- NULL # predicted labels with view 1
predicted.v2 <- NULL # predicted labels with view 2
probs.v1 <- NULL # predicted probabilities with view 1
probs.v2 <- NULL # predicted probabilities with view 2

# Perform internal cross-validation.

```
for(i in 1:k){
  train <- D[folds != i
```

```
((probs.v1 + probs.v2) / 2),
pred1 = predicted.v1,
pred2 = predicted.v2)
```

```
#train meta-learner
metalearner <- randomForest(label ~,
metaFeatures, nt = 100)
```

```
res <- structure(list(metalearner=metalearner,
learnerV1=learnerV1,
learnerV2=learnerV2,
v1cols = v1cols,
v2cols = v2cols,
class = "mvstacking")
```

```
return(res)
}
```

The first argument D is a data frame containing the training data. v1cols and v2cols are the column names of the two views. Finally, argument k specifies the number of folds for the internal cross-validation to avoid overfitting (Steps 2 and 3 as described in the generalized stacking procedure).

The function iterates through each fold and trains a Random Forest with the train data for each of the views. Within each iteration, the trained models are used to predict the labels and probabilities on the internal test set are concatenated across all folds (predicted.v1, predicted.v2).

After cross-validation, the meta-features are generated by creating a data frame with the predictions of each view. Additionally, the average of class probabilities is added as a metafeature. The true labels are also added. The purpose of cross-validation was to avoid overfitting but at the end, we do not want to waste data so that both learners are re-trained with all data.

Finally, the meta-learner which is also a Random Forest is trained with the meta-features data frame. A list with all the required information to make predictions is created. This includes first-level learners, the meta-learner, and the column names for each view we know how to divide the data frame into two views at prediction time.

The following code snippet shows the implementation for making predictions using a trained stacking model.

```
mvstackacking <- function(D, v1cols, v2cols, k = 10){

# Generate folds for internal cross-validation
folds <- sample(1:k, size = nrow(D), replace = T)

trueLabels <- NULL
predicted.v1 <- NULL # predicted labels with view 1
predicted.v2 <- NULL # predicted labels with view 2
probs.v1 <- NULL # predicted probabilities with view 1
probs.v2 <- NULL # predicted probabilities with view 2

# Perform internal cross-validation.

```
for(i in 1:k){
  train <- D[folds != i
```

```
((probs.v1 + probs.v2) / 2),
pred1 = predicted.v1,
pred2 = predicted.v2)
```

```
#train meta-learner
metalearner <- randomForest(label ~,
metaFeatures, nt = 100)
```

```
res <- structure(list(metalearner=metalearner,
learnerV1=learnerV1,
learnerV2=learnerV2,
v1cols = v1cols,
v2cols = v2cols,
class = "mvstacking")
```

```
return(res)
}
```

The first argument D is a data frame containing the training data. v1cols and v2cols are the column names of the two views. Finally, argument k specifies the number of folds for the internal cross-validation to avoid overfitting (Steps 2 and 3 as described in the generalized stacking procedure).

The function iterates through each fold and trains a Random Forest with the train data for each of the views. Within each iteration, the trained models are used to predict the labels and probabilities on the internal test set are concatenated across all folds (predicted.v1, predicted.v2).

After cross-validation, the meta-features are generated by creating a data frame with the predictions of each view. Additionally, the average of class probabilities is added as a metafeature. The true labels are also added. The purpose of cross-validation was to avoid overfitting but at the end, we do not want to waste data so that both learners are re-trained with all data.

Finally, the meta-learner which is also a Random Forest is trained with the meta-features data frame. A list with all the required information to make predictions is created. This includes first-level learners, the meta-learner, and the column names for each view we know how to divide the data frame into two views at prediction time.

The following code snippet shows the implementation for making predictions using a trained stacking model.

```
mvstackacking <- function(D, v1cols, v2cols, k = 10){

# Generate folds for internal cross-validation
folds <- sample(1:k, size = nrow(D), replace = T)

trueLabels <- NULL
predicted.v1 <- NULL # predicted labels with view 1
predicted.v2 <- NULL # predicted labels with view 2
probs.v1 <- NULL # predicted probabilities with view 1
probs.v2 <- NULL # predicted probabilities with view 2

# Perform internal cross-validation.

```
for(i in 1:k){
  train <- D[folds != i
```

```
((probs.v1 + probs.v2) / 2),
pred1 = predicted.v1,
pred2 = predicted.v2)
```

```
#train meta-learner
metalearner <- randomForest(label ~,
metaFeatures, nt = 100)
```

```
res <- structure(list(metalearner=metalearner,
learnerV1=learnerV1,
learnerV2=learnerV2,
v1cols = v1cols,
v2cols = v2cols,
class = "mvstacking")
```

```
return(res)
}
```

# CHAPTER 3. PREDICTING BEHAVIOR WITH ENSEMBLE LEARNING

Table 3.1: Stacking results.
| | Accuracy | Recall | Specificity | Precision | F1 |
|---|---|---|---|---|---|
| Audio | 0.8463203 | 0.8413690 | 0.9741266 | 0.8487849 | 0.8438718 |
| Accelerometer | 0.8585559 | 0.8493635 | 0.9764988 | 0.8548481 | 0.8511572 |
| Multi-view Stacking | 0.9393939 | 0.9349011 | 0.9989275 | 0.9371645 | 0.9358082 |

The **object** parameter is the trained model and **newdata** is a data frame from which we want to make the predictions. First, labels and probabilities are predicted using the two views. Then, a data frame with the *meta-features* is assembled with the predicted label and the averaged probabilities. Finally, the *meta-learner* is used to predict the final classes using the meta-features.

The script *stacking_activities.R* shows how to use our *mystacking()* function. With the following lines we can train and predict.

```
m.stacking <- mystacking(trainset, v1cols, v2cols, k = 10)
pred.stacking <- predict(m.stacking, newdata = testset[-1])
```
