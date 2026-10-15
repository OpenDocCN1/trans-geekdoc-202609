
network to categorize exudates, hemorrhages, and microaneurysms. Green channel extraction, masking, smoothing, and bitwise AND improve exudate estimations. Hemorrhages and microaneurysms are found by morphological methods like opening. Dilation and erosion occur here. Microaneurysms, hemorrhages, and exudates determine diabetic retinopathy.

## 10.3 METHODS AND MATERIALS

### 10.3.1 DR DETECTION METHODOLOGY

In this research, the proposed approach is named RetinalAlexU-Net, a deep learning-based vessel segmentation method having U-Net as its core architecture. In 2015, Ronneberger et al. introduced U-Net, a contracting and expanding route network, for biomedical segmentation, essentially composed of convolution layers, which provide the model the ability to recognize information automatically and adaptively. U-Net is being used as the foundational architecture because of its efficacy in pixel-level segmentation challenges, especially in the field of medical image analysis. Figure 10.3 shows our RetinalAlexU-Net. It is divided into three sections: encoding, bridge, and decoding.

**RetinalAlexU-Net:** The modified model makes an effort to retain the majority of the salient characteristics and architectural components as the original implementation of the U-Net design. However, a few improvements are made to the standard model to enhance the efficiency of the model, as well as to improve the speed and simplicity of the model and reduce its time consumption. RetinalAlexU-Net is a kind of encoding-decoding network architecture that relies on a single set of encoder and decoder blocks connected by an AlexNet bridge.

**Encoder:** The flow on the left, known as the contracting path, contrasts with the provided flow on the right, which is known as the expansion path. The contracting path is the typical convolutional network architecture, consisting of 3 × 3 convolutions replicated three times. The feature map that was produced as a result of the convolution process is then given to the rectified linear activation function (ReLU) layer, as shown in the equation below, which is then followed by the 2 × 2 max-pooling operation, which is done to minimize the overall size of the feature map. After each maximum pooling process is complete, downsampling is carried out, and, in parallel, feature channels are increased by double.

```
R(x) = max (0, x) 
(10.1)
```

Thereby,

if x < 0, R(x) = 0 and if
x ≥ 0, R(x) = x whereas x=Positive Value

### AlexNet Interconnectivity:

![](img/a2fc2296b12812e9151e817bff1de16d_201_0.png)

FIGURE 10.3 The proposed RetinalAlexU-Net architecture.

The bridge of the U-Net model is comprised of a simple AlexNet convolutional neural network. (Alom et al., 2018). This network has a total of five convolution layers, some of which are followed by max-pooling layers, and it concludes with three fully connected layers that are combined with a softmax layer. AlexNet’s connection mandates that the model gets the input data through the encoder’s downsampling channel. The five convolutional layers in the network are composed of a collection of feature maps and kernels for extracting feature information, like edges, corners, and other angular characteristics. The term “convolution operation” refers to the procedure of sliding and overlaying the kernels across the entire image. The ReLU layer is inserted in AlexNet after each fully connected (FC) layer of the convolutional portion of the network. This network mitigates the overfitting issue by inserting a dropout layer after every FC layer.

**Decoder:** The decoder flow is the counterpart of the encoder flow, which uses downsampling, and consists of phases for upsampling of feature maps before proceeding to a convolution procedure with a kernel size of 2 × 2. Convolution results in a two-channel reduction in feature channels compared to their encoder equivalent. The ReLU activation function is utilized at the end of every stage of the convolutional layers. The suggested paradigm reduces the computational burden of the network, making its use simple and effective. This improves network training while transforming dense features into sparse features, which effectively makes the features more robust.

In addition, the model utilizes stochastic gradient descent (SGD). This is an optimization approach for training neural network models. To derive updated values for the model variables, this method has to compute gradients denoted by Equation 10.2 for each variable and carry out a parameter change for every single training sample x^(i) and label y^(i).

θ = θ - η Δ, J(θ; x^(i); y^(i)) (10.2)

Where:

- θ = Model parameter.
- η = The learning rate of the size of the steps we take in order to attain a (local) minimum.
- Δ, J(θ) = Objective function for parameters.

We utilized the binary cross-entropy loss function represented by Equation 10.3 throughout the training process because we used a sigmoid with a zero to one range.

Cross Entropy = 1 / Σ_{T=1..M_y,or} log(p_o,t) (10.3)

For lowering the loss, which refers to the value that is assumed by the loss function, at the initial stage the learning rate of the Adam optimizer is set to 0.0005. Finally, we evaluated the outcome using Intersection over Union for the segmentation of the RetinalAlexU-Net and ground truth. The accuracy increases with the value of the Dice coefficient.

![](img/a2fc2296b12812e9151e817bff1de16d_203_0.png)

FIGURE 10.4 Classification of diabetic retinopathy based on deep neural networks.

Finally, diabetic retinopathy is classified by the retinal vascular network using the proposed RetinalAlexU-Net, as shown in Figure 10.4.

### 10.3.2 DATASETS AND VARIOUS METRICS OF PERFORMANCE

Retinal Fundus Images: Here, we summarize the most common performance metrics and standard datasets used in DR research. For training and evaluating the framework for algorithms used in different DR detection tasks, many datasets comprising retinal fundus pictures have been created. Listed below are several publicly available benchmark datasets that we will briefly discuss: Kaggle (Kaggle Dataset, 2022), MESSIDOR (Messidor Dataset, 2022), high resolution fundus (HRF), DRIVE (DRIVE Dataset, 2022).

KAGGLE: This data was given by EyePACS clinics and comprises several high-resolution retinal pictures captured in a variety of illumination situations. Expert ophthalmologists annotated each picture at the pixel level, and a DR grade between zero and four was applied to each image.

MESSIDOR: The Ministry of French Research and Defense supported this dataset’s creation as part of the MESSIDOR research program. This data was obtained by three different ophthalmology clinics using a Topcon non-mydriatic retinography and a 45° field of view (FOV) colour video 3CCD camera. Image-level annotations for DR grades and macular edema risk were given by ophthalmologists.

HRF: The HRF database includes 45 high-resolution eye fundus pictures with a size of 3504 × 2336 pixels. These photographs were segmented by a group of professionals who work in the area of retinal image processing as well as clinicians from the ophthalmology clinics who participated in the research. To be more explicit, the dataset may be separated into 15 photos of healthy patients, 15 images of diabetic retinopathy patients, and 15 images of glaucoma sufferers. For each picture, there is an associated ground truth image as well as a mask with a determined field of view. In this study, we choose 41 photos at random for training purposes, and we use the remaining four images for testing purposes, to segment retinal vessels.

DRIVE: To facilitate comparative analyses of vascular segmentation in retinal pictures captured with a non-mydriatic Canon camera. Forty randomly chosen fundus photos are used: thirty-three don’t exhibit any symptoms of DR, whereas seven indicate mild to severe early DR.

### 10.3.3 PERFORMANCE MEASURES

Metrics for evaluating DR detection techniques are defined below. Accuracy, sensitivity (recall), specificity, precision, F-score, receiver operating characteristic (ROC) curve, IoU, and the Dice similarity coefficient are all common metrics used to evaluate the efficiency of classification algorithms.

**Accuracy:** This metric measures the ratio of the proportion of properly categorized occurrences relative to the total number of occurrences. It is precisely defined as shown in Equation 10.4:

Acc = (TP + TN) / (TP + TN + FP + FN)  (10.4)

**Sensitivity (SE):** This statistic, shown in Equation 10.5, sometimes called the “true positive rate” or “recall”, measures the percentage of correctly labelled positive instances.

Recall(SE) = TP / (TP + FN)  (10.5)

**Specificity (SP):** This metric is more often referred to as the true negative rate, and it is the fraction of negative cases that are correctly identified, as defined by Equation 10.6.

SP = TN / (TN + FP)  (10.6)

**Precision (P):** Often known as PPV (positive predictive value), this is a metric for determining how accurately positive occurrences are identified, as shown in Equation 10.7.

P = TP / (TP + FP)  (10.7)

Where:

- TP (true positive) refers to the total amount of positive occurrences.
- TN (true negative) is the total number of adverse occurrences.
- FP (false positive) and FN (false negative) are numbers of positive and negative instances.

**F-score (F):** This is a combination of the two measures of precision and recall represented in Equation 10.8: F = 2 * Precision * Recall / (Precision + Recall)  (10.8)

**Intersection over Union (IoU):** The ratio of the area of intersection to the sum of the areas of prediction and ground truth constitutes the IoU measure. It can be estimated as follows (Equation 10.9), where TP, FP, and FN are just areas or the number of pixels.
