
We use $f_l^{t_1}$, $f_l^{t_2}$, with $l = \{1, \ldots, L\}$, to represent features in the $l^{th}$ layer of the first and third channels, respectively, corresponding to $t_1$ and $t_2$. For instance, $f_1^{t_1}$ represents the features extracted from the multi-scale shallow block in the first layer of the first channel (corresponding to $t_1$). Finally, we obtain the features $f_L^{t_1}$ and $f_L^{t_2}$ for $t_1$ and $t_2$, respectively.

In the second channel, which we call the intermediate channel, new features are also extracted, which we call intermediate features and represent with $f_l^{m}$. At the first layer, the features extracted in the first and third channels are subtracted, $\left(f_1^{t_1} - f_1^{t_2}\right)$, and fed to the second channel. In the second channel, $\left(f_1^{t_1} - f_1^{t_2}\right)$ enters the multi-scale shallow block and $f_1^{m}$ is extracted. In the next layers, change information is inferred from $\left(f_2^{t_1} - f_2^{t_2}\right) + f_1^{m}$, $\left(f_3^{t_1} - f_3^{t_2}\right) + f_2^{m}$, ..., $\left(f_L^{t_1} - f_L^{t_2}\right) + f_{L-1}^{m}$. That is, at each layer, the features extracted in the first and third channels are subtracted then added to the features extracted in the second channel from the previous layer, thus making our algorithm very powerful in detecting changes.

In the last layer, $\left(f_L^{t_1} - f_L^{t_2}\right) + f_{L-1}^{m}$ is extracted, flattened, and fed into a fully connected layer with ReLU activation function. Moreover, we use the ReLU after each convolutional layer as a piecewise linear activation function. The ReLU function can be formulated using Equation (5):

$$f(x) = \max(0, x) \quad (5)$$

![](img/828a5d28a36454f7b3332df93f35492f_178_0.png)

**Figure 5.** The proposed TCD-Net architecture for CD of remote sensing (RS) datasets.

The last fully-connected layer is a softmax layer. In general, this layer is used to model categorical probability distributions and calculate the probability that each pixel belongs to the *change* and *no-change* classes. Finally, the pixels are divided into two categories of *change* and *no-change*. The *softmax* function is expressed in Equation (6):

$$f(x_i) = \frac{e^{x_i}}{\sum_j e^{x_j}} \quad (6)$$

### Model Optimization

As shown in Figure 1, after the automatic training sample generation phase, the samples generated are divided into three categories: training, testing and validation datasets.

The TCD-Net is trained based on the training dataset. Additionally, the loss value was calculated by the loss function based on the validation dataset. There is no analytical method for optimizing CNN parameters. Thus, optimization is used to adjust the model parameters iteratively. In this research, an Adam optimizer is used to adjust CNN parameters. As a result, the model is trained based on the initial values of the parameters, then the output of the model is compared with the actual value. The error of the training model is fed to the optimizer, and the parameters are updated. In an iterative process, the gradient is reduced at this point to minimize the total output error. This process continues until the stop condition is reached, i.e., a certain number of repetitions or a certain error (minimum error). Due to back-propagation, the parameters are updated at each step to decrease the error of comparing the results obtained from the network with the training/validation dataset. Finally, test data is used to evaluate network performance.

In this research, cross-entropy was used to calculate the loss function of the proposed architectures. The performance of the network given the inputs and the labels with optional performance weights and other parameters is calculated by the cross-entropy function for outputs ($y$) and targets ($t$) using the following Equation (7):

$$E = -\frac{1}{n} \sum_{j=1}^{n} \sum_{i=1}^{k} \left( t_{ij} \ln y_{ij} + (1 - t_{ij}) \ln(1 - y_{ij}) \right) \quad (7)$$

where $n$ is the number of training samples and $k$ is the number of classes. Additionally, $t_{ij}$ is the $ij$th entry of the target matrix and $y_{ij}$ is the $ij$th entry of the training sample matrix.

### 2.3.5. Accuracy Assessment

Accuracy assessment is an integral part of any RS task and is done in two ways. In the first approach, the results of the proposed method are compared with GT data and in the second approach with sample data. In this study, the final results of the proposed CD method are compared quantitatively as well as qualitatively with the GT data and the results of other SOTA CD methods. The quantitative comparison is based on the metrics described subsequently.

Based on the CD results and the GT data, there are four modes: (1) if both the GT data and result are positive, it is considered as True Positive (TP); (2) if the GT data is positive and the result is negative, it is considered as False Negative (FN); (3) if both the GT data and the results are negative, it is considered as True Negative (TN); and (4) if the GT data is negative but the result is positive, it is considered as False Positive (FP). With the help of these four values, the essential criteria such as false-positive rate (FPR) (also called false alarm rate), true-positive rate (TPR) (also called hit rate and recall), false-negative rate (FNR), overall accuracy (OA), precision, detection rate (DR), F1-score, overall error rate (OER), Prevalence (PRE) and kappa coefficient (KC) are calculated by the following relationships shown in Table 1.

**Table 1.** Formulas for accuracy assessment criteria.

| Accuracy Index | Formula |
|---|---|
| FNR | $FN / (FN+TP)$ |
| TPR | $TP / (TP+FN)$ |
| FPR | $FP / (TN+FP)$ |
| OA | $(TN+TP) / (TP+TN+FP+FN)$ |
| Precision | $TP / (TP+FP)$ |
| F1-Score | $TP / (TP + \frac{1}{2}(FP+FN))$ |
| OER | $(FN+FP) / (TP+TN+FP+FN)$ |
| PRE | $[(TP+FP)\times(TP+FN)+(FN+TN)\times(FP+TN)] / (TP+TN+FP+FN)^2$ |
| KC | $(OA - PRE) / (1 - PRE)$ |

### 2.3.6. Comparative Methods

To compare the effectiveness of the intermediate layer of TCD-Net, this research compares the TCD-Net algorithm with a dual-channel deep network. This dual-channel network is similar to TCD-Net, except that the intermediate layer is removed. To make the comparison fair, the dual-channel network is trained with the same training samples extracted from the pseudo-label sample generation phase. In addition, the following unsupervised SOTA CD methods are compared and analyzed to confirm the efficiency of TCD-Net. These approaches are PCA_kmeans [65], NR_ELM [66], Gabor_PCANet [67], CWNN [57] and DP_PCANet [58], which are described in brief below:

- **PCA_kmeans [65]:** Initially, the DI is calculated by using the absolute-value difference between two SAR images. Additionally, the DI is separated into non-overlapping $h \times h$ blocks. Then, using PCA, all blocks are projected into the eigenvector space to obtain representation properties. Finally, each pixel is assigned to a cluster based on the minimum Euclidean distance between its feature vector and the cluster’s mean feature vector, using k-means clustering.

- **NR_ELM [66]:** Initially, a neighborhood-based ratio operator and the hierarchical FCM algorithm are used for generating a DI and identifying pixels of interest in it. Secondly, the ELM classifier is trained using pixel-wise patch features centered on the pixels of interest.

- **Gabor_PCANet [67]:** Initially, a pre-train step is performed using the Gabor wavelet and the FCM classifier. Secondly, by considering a neighborhood with specific dimensions for each training pixel in the two images and juxtaposing the two image patches, PCA features are extracted from the training patches. Then, the SVM algorithm is used to build a model on PCA features. After completing the training phase, the remaining pixels are divided into two categories: *changed* and *no-change* pixels.

- **CWNN [57]:** A convolutional-wavelet neural network (CWNN) method has been applied in bi-temporal SAR images. Firstly, a virtual sample generation scheme is utilized to generate pseudo-label training samples that are likely *change* or *no-change*. Secondly, the pseudo-label samples obtained in the previous step are used to train the CWNN network and create a change map.

- **DP_PCANet [58]:** Firstly, inspired by the convolutional and pooling layers in the CNN, a DDI based on a weighted-pooling kernel has been extracted. Then, using sigmoid nonlinear mapping and parallel FCM, two mapped DDIs are generated. Then, the mapped DDIs are classified into three types of pseudo-label samples, i.e., *change*, *no-change* and *ambiguous* samples. Finally, with the SVM model that is trained based on the PCA features, *ambiguous* samples are classified as *change* or *no-change*.
