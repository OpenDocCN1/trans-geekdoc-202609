
```
+ }
> par(mfrow=c(4,4), mar=c(0.1,0.1,0.1,0.1))
> for (i in 1:16) {
+ outputData <- as.array(executor$ref.outputs$convolution11_output[,,i,2])
+ image(outputData, xaxs='n', yaxs='n', col=grey.colors(255))
+ )
+ }
```

We plot the outputs of the second convolutional layer for two images, respectively:

![](img/da8fb67f2acf661518076e08b6ffd9b9_58_0.png)

The second convolutional layer extracts higher-level features of the input images, such as shape and contour. All these 50 feature maps combined together, provide rich representations which are then fed into the fully connected layers. Therefore, classification performance is increased thanks to the convolution operations.

So far, we have examined the effectiveness of our CNN model by plotting the learning curve and visualizing the convolution extracted features. We can do one more inspection on the generalization of our model. For instance, we can take out a subset of data from the testing set to simulate a validation set, and use the remainder as the new testing set. We perform **early stopping** based on the validation set, which provides instruction on how many iterations is good enough and does not overfit the model. Finally, we employ the trained model with early stopping on the testing set and see how well the model is able to generalize to unseen data.

We first split the testing set into validation (40%) and final testing set (60%):

```
> validation_perc = 0.4
> validation_index <- createDataPartition(data_test.y, p=validation_perc, list=FALSE)
>
```

```
> validation.array <- test.array[, , , validation_index]
> dim(validation.array) <- c(28, 1, length(validation.array[1,1,]))
> data_validation.y <- data_test.y[validation_index]
> final_test.array <- test.array[, , , -validation_index]
> dim(final_test.array) <- c(28, 1, length(final_test.array[1,1,]))
> data_final_test.y <- data_test.y[-validation_index]
```

To conduct early stopping, we write our custom callback function and will assign it to the parameter, epoch.end.callback. The callback function checks the classification performance on the validation set, and if it is greater than the threshold we set, the training stops:

```
> mx.callback.early.stop <- function(eval.metric) {
+ function(iteration, nbatch, env, verbose) {
+ if (!is.null(eval.metric)) {
+ result <- env$metric$get(env$eval.metric)
+ if (result$value >= eval.metric) {
+ return(FALSE)
+ }
+ }
+ return(TRUE)
+ }
```

Now, we train the CNN model with early stopping based on the validation set where we set the stopping criteria as a validation accuracy greater than 0.985:

```
> model_cnn_earlystop <- mx.model.FeedForward.create(softmax, X=train.array, y=data_train.y, eval.data=list(data=validation.array, label=data_validation.y), ctx=devices, num.round=30, array.batch.size=100, learning.rate=0.05, momentum=0.9, wd=0.00001, eval.metric=mx.metric.accuracy, epoch.end.callback = mx.callback.early.stop(0.985))
Start training with 1 devices
[1] Train-accuracy=0.284571428571429
[1] Validation-accuracy=0.921395348837209
[2] Train-accuracy=0.95145569620254
[2] Validation-accuracy=0.972325581395349
[3] Train-accuracy=0.980221518987343
[3] Validation-accuracy=0.97906976744186
[4] Train-accuracy=0.986613924050634
[4] Validation-accuracy=0.982790697674419
[5] Train-accuracy=0.990537974683546
[5] Validation-accuracy=0.981627906976744
[6] Train-accuracy=0.992848101265824
[6] Validation-accuracy=0.985348837209302
```

Training stops after the sixth iteration as the criteria is met. Finally, the performance on the new testing set is examined:

```
> prob_cnn <- predict(model_cnn_earlystop, final_test.array)
> prediction_cnn <- max.col(t(prob_cnn)) - 1
> cm_cnn = table(data_final_test.y, prediction_cnn)
> cm_cnn
```

| data_final_test.y | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|---|---|---|---|---|---|---|---|---|---|---|
| 0 | 626 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 |
| 1 | 0 | 701 | 1 | 0 | 0 | 2 | 1 | 3 | 4 | 0 |
| 2 | 1 | 0 | 598 | 4 | 0 | 0 | 0 | 6 | 0 | 0 |
| 3 | 0 | 0 | 0 | 658 | 0 | 5 | 0 | 0 | 2 | 1 |
| 4 | 0 | 0 | 0 | 0 | 585 | 1 | 3 | 3 | 1 | 4 |
| 5 | 1 | 0 | 1 | 3 | 0 | 558 | 5 | 0 | 0 | 2 |
| 6 | 4 | 0 | 0 | 0 | 0 | 0 | 595 | 0 | 0 | 0 |
| 7 | 0 | 1 | 3 | 0 | 1 | 0 | 0 | 675 | 0 | 0 |
| 8 | 4 | 0 | 1 | 1 | 1 | 7 | 3 | 0 | 621 | 2 |
| 9 | 1 | 0 | 0 | 0 | 2 | 1 | 0 | 4 | 0 | 589 |

```
> accuracy_cnn = mean(prediction_cnn == data_final_test.y)
> accuracy_cnn
[1] 0.9855487
```

Our CNN model is able to generalize decently.

## Summary

We have just finished our first mile in the R and deep learning journey! Through this chapter, we got more familiar with the important concepts of deep learning. We started with what deep learning is all about, why it is important and the recent success of applications, as well. After we were well equipped, we solved the handwritten digit using shallow neural networks, deep neural networks and CNNs in sequence, and proved that CNNs are the best suited to exploiting strong and unique features that differentiate images of different classes.

Inspired by the human visual cortex, CNNs classify images by first deriving rich representations such as edges, curves and shapes, which was demonstrated in the visualization of the outputs of convolutional layers. In addition, we verified the performance and generalization of the CNN model using early stopping as a technique to avoid overfitting. Overall, we not only covered the mechanics of CNNs, including the concepts of convolution and pooling, but also implemented a CNN model with `MXNet`, as one of the most popular deep learning packages in R.

## Traffic Sign Recognition for Intelligent Vehicles

**Convolutional neural networks (CNNs)** are so useful in computer vision that we are going to use one for another application, traffic sign detection for intelligent vehicles. We will also cover several important concepts of deep learning in this chapter and will get readers exposed to other popular frameworks and libraries for deep learning.

We continue our R deep learning journey with one of the core problems in self-driving cars, object recognition, and to be specific, traffic sign classification. To avoid accidents and ensure safety, robust traffic sign classification is critical to realizing driving autonomy. We will start with what self-driving cars are and what aspects deep learning is applied to. We will also discuss how deep learning stands out and becomes the state-of-the-art solution for object recognition in intelligent vehicles. With the background knowledge in mind, we'll get started with our project when we first conduct an exploratory analysis of the data and performance data preprocessing, including Y'UV color encoding conversion. We'll make our first attempt at using CNNs with MXNet and achieve more than 99% accuracy. Then we'll move on to another powerful deep learning framework called TensorFlow and an API built on top of it called Keras.

We'll also introduce the dropout technique as a regularization approach similar to Lasso (L1) / Ridge (L2) regularization. Besides overfitting, we'll demonstrate how to deal with a lack of training data, utilizing data augmentation techniques. We'll wrap up the chapter by summarizing approaches to prevent overfitting in CNN models. Once again, we will prove that deep learning models remove manual or explicit feature extraction steps that are taken in traditional approaches, and they instead automatically discover useful patterns underneath input data during the training process.

We will get into the details of the topics mentioned here:

- What self-driving cars are
- How deep learning is applied in self-driving cars
- How deep learning becomes a state-of-the-art solution for object recognition in intelligent vehicles
- Exploratory analysis on the German Traffic Sign Recognition Benchmark dataset's data
- Traffic sign recognition using convolutional neural networks with the MXNet package
- Keras and TensorFlow
- Traffic sign recognition using convolutional neural networks with the `keras` package
- Reducing overfitting with dropout
- Data augmentation and common augmentation methods
- Using data augmentation for a small training set
- Summarizing approaches to prevent overfitting in CNN models

## How is deep learning applied in self-driving cars?

A self-driving car (also called an autonomous/automated vehicle or driverless car) is a robotic vehicle that is capable of traveling between destinations and navigating without human intervention. To enable autonomy, self-driving cars detect and interpret environments using a variety of techniques such as radar, GPS and computer vision; and they then plan appropriate navigational paths to the desired destination.

In more detail, the following is how self-driving cars work in general:

- The software plans the routes based on the destination, traffic, and road information and starts the car
- A **Light Detection and Ranging (LiDAR)** sensor captures the surroundings in real time and creates a dynamic 3D map
- Sensors monitor lateral movement to calculate the car's position on the 3D map
