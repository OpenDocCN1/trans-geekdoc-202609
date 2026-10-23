
## Without horizontal stride modification

![](img/828a5d28a36454f7b3332df93f35492f_371_0.png)

## With horizontal stride modification

**Figure 10.** The spatial dimensions of the input raw data matrix and subsequent subsampled intermediate representations after each group of convolutional layers. For groups conv1, conv3, conv4, and conv5, the subsampling is completed in the first convolutional layer of the group. For group conv2, the subsampling is completed in the max pooling layer immediately before the first convolutional layer of conv2. The first diagram shows how, without any modification to the ResNet18 architecture, both the vertical and horizontal dimensions are halved five times. The vertical dimension is down-sampled from 1024 to 32, while the horizontal dimension is downsampled from 30 to 1. The second diagram shows how only the vertical dimension is subsampled after our modification to the ResNet18 architecture, while the horizontal dimension remains constant. This is because our modification sets the horizontal stride of subsampling layers to 1. Note that the dimensions in the figure are not to scale due to impracticality of displaying very tall and narrow matrices.

This modification does not change the dimensionality of any kernels of the convolutional layers, so it does not add any parameters to the model. Thus, it does not prevent us from using any pretrained set of parameters of the original ResNet18 architecture. Even though the horizontal stride of the modified network is different, which can change the horizontal scale and appearance of features in deeper layers of the network, using existing ImageNet-pretrained weights is still a sensible initialization procedure. ImageNet pretraining has been shown to be consistently beneficial in a wide array of image classification tasks, some of which have different image dimensions, scales of objects appearing in the images, and even cover an entirely different domain of images than the ImageNet-1k dataset [56,57]. We empirically validate the contribution of pretraining for weight initialization in our experiments.

The modification results in the dimension of the tensor output by the last convolutional layer in the network being (32, 30), since the input is not subsampled in the horizontal dimension. The depth of that tensor remains 512, and the global average pooling layers aggregate this tensor across the spatial dimensions into a vector of size 512. Thus, the vector representation which is fed to the fully-connected output layer is of the same dimensionality as before the modification, the output layer also does not require any changes.

## 5. Experiments

### 5.1. Experiment Setup

To evaluate our models we perform experiments on the RealSAR dataset. We evaluate and compare two main approaches, each with a number of modifications regarding data augmentation procedures, weight initialization, the size of the training set and the classification architecture used. The first approach consists of models which work on reconstructed images. We train and evaluate them on the RealSAR-IMG dataset. In the second approach, we evaluate models which work with raw radar data. Experiments for the second approach are performed on the RealSAR-RAW dataset. All experiments were completed in a multi-label classification setting, where each label denotes the absence or presence of one of the three different objects that we detect. The training procedure minimized the mean of binary cross-entropy losses of all labels.

We chose all hyperparameters manually, by testing and comparing different combinations of values on the validation set. In all experiments for both models, we use the Adam optimizer, with a learning rate of $2 \times 10^{-4}$, and the weight decay parameter set to $3 \times 10^{-4}$. Experiments on the full training set (156 examples) are performed over 30 epochs, with a batch size of 16, which results in 300 parameter updates. To ensure comparisons are fair, when training on subsets of the training set, the number of epochs is chosen, such that the total number of parameter updates stays the same.

To prevent our models from overfitting and increase robustness to noise, we use two stochastic data augmentation procedures during training: random horizontal flipping and color jittering. Since the radar moves laterally when recording a scene the raw recorded data are equivariant to changes in the lateral positions of objects in the scene. The Omega-K algorithm preserves the equivariance as well. Thus, for both the raw and the vision representation of any given scene, the horizontally flipped representation corresponds to rearranging the scene to be symmetric with respect to the middle of the lateral axis. Thus, the horizontal flip transformations do not change the semantics, i.e., the labels of that representation, and can be used as an augmentation procedure. Color jittering is used in computer vision to stochastically apply small photometric transformations on images. This artificially increases the dataset, since in every epoch, each image is transformed with different parameters, sampled randomly. One novelty we introduce is to extend this technique to raw data as well, by adding small Gaussian noise to each example. We validate this contribution empirically.

We trained both the raw and the image-based models with different modifications. To explore the contribution of transfer learning [34], we used three different weight initialization procedures: random initialization [58], initializing with ImageNet-1k pretrained weights, and initializing by pretraining on the LabSAR dataset. To test how the model improves as more data are collected, we performed experiments on 25%, 50%, 75%, and 100% of examples in the training set. The validation and test sets remained fixed throughout all experiments to ensure fair comparisons. Through these experiments we converged to the two best models: one based on raw radar data, and the other based on reconstructed images. We used these two models to perform further analyses.

To test whether combining models trained on different input modalities yields an increase in performance, we evaluated an ensemble model. The ensemble consists of the best RAW and the best IMG model. Its output vector is the mean of the output vectors of the two models.

### 5.2. Metrics

All of our models are trained in the multi-label classification setting. The model output $P$ is a vector of $n$ numbers, where $n$ is the number of different objects which can appear in a scene. The element $i$ of the output vector ($P[i]$) is the probability given by the model that the corresponding object $i$ is present in the scene. The probability of its absence is $1 - P[i]$. Thus, the detection of each individual object can be seen as a separate binary classification problem.

In binary classification evaluation, we have a set of binary ground truth labels for all examples, and the corresponding model predictions, either as probabilities or as binary values (0 and 1). When the predictions are binary values, the pair consisting of the ground truth label and the prediction for any example in the dataset can be classified into one of four sets:

- True negative (TN): the object is not present, and the model predicts it correctly;
- False negative (FN): the object is present, but the model incorrectly predicts it is not;
- False positive (FP): the object is not present, but the model incorrectly predicts it is;
- True positive (TP): the object is present, and the model predicts it correctly.

Various metrics can be defined using the described quantities. Accuracy measures the percentage of correct predictions:

$$Acc = \frac{TN + TP}{TP + TN + FP + FN}\tag{8}$$

Precision (P) measures how many positive predictions were correct:

$$P = \frac{TP}{TP + FP}\tag{9}$$

It decreases as the number of false positives increases. Recall (R) measures how many positive examples were captured:

$$R = \frac{TP}{TP + FN}\tag{10}$$

It decreases as the number of false negatives increases. If we want a strict metric which will penalize both excessive false positives and false negatives, we can use the F1-score, which is the harmonic mean of precision and recall:

$$F1 = \frac{2 \cdot P \cdot R}{P + R} = \frac{2 \cdot TP}{2 \cdot TP + FP + FN}\tag{11}$$

Since the output P[i] of the model is the probability of the positive class, we classify an example as a positive if its probability is higher than a certain threshold T[i]. Otherwise, we classify it as a negative. The natural threshold to choose is 0.5. However, the actual optimal threshold varies depending on the metric. For example, recall increases as the threshold decreases. The minimum threshold (0) will maximize recall (1.0), since it will capture all positive examples. A threshold that is higher than the highest prediction probability will minimize recall (0.0), since it will not capture any positive examples. Conversely, a higher threshold tends to result in higher precision, since only very certain predictions will be classified as positive.

To remove the variability of the choice of the threshold from model evaluation and comparison, the average precision (AP) metric is often used. It is calculated as the average over precision values for every possible recall value. To extend it to the multi-label setting (multiple binary classification problems), we use the mean average precision (mAP) which is the arithmetic mean of the AP values of all individual tasks.

Once the best model has been chosen according to mAP, in order to use it to make predictions, we have to find the optimal threshold parameter for each individual output. We want our model to perform well on all classes, i.e., all 8 possible subsets of objects that can appear in the scene. Thus, we choose a vector of thresholds such that it maximizes the macro-F1 score on the validation set [59].

The macro-F1 score is a multi-class extension of the F1 score. It is calculated as the arithmetic mean over the F1-score of each class.

$$macro\text{-}F1 = \frac{1}{n} \sum_{k=1}^{n} F1_k\tag{12}$$
