
This section explores the working of the suggested technique and describes the main concepts of brain tumor classification in an efficient way. The proposed system is a two-fold process comprising the training phase, which includes sub-steps of loading the deep convolutional model, fine-tuning the existing model followed by the final testing phase. We fine tune two different deep learning models (`GoogLeNet` and `SqueezeNet`) for better results. In the first phase, a lightweight `SqueezeNet` [[18](#chap11.xhtml#fsr18)] model is loaded to easily handle brain tumor classification in real-time situations. Most of the recent researchers try to focus on increasing accuracy over different computer vision datasets and ignore the need of efficient algorithms. There are multiple architectures that can achieve much better accuracy but with too many parameters. `SqueezeNet` can achieve the AlexNet-level accuracy with 50 times fewer parameters and much less model size of about 0.5 MB. In the second phase, `GoogLeNet` [[19](#chap11.xhtml#fsr19)] model is loaded, which is also the winner of the ILSVRC (ImageNet Large Scale Visual Recognition Competition) 2014. `SqueezeNet` and `GoogLeNet` are trained on large ImageNet dataset, and in this system we used these pre-trained weights and added up our data to train the model, thus the model is more effective and efficient. After the training process models are downloaded and are ready to run through proposed algorithm to predict real-time brain tumors. Proposed framework is shown in [Fig. 1](#chap11.xhtml#fig1) and each step is explained in what follows.

### 3.1 Fine-tuning SqueezeNet model

In order to modify the `SqueezeNet` architecture, the final layer is updated as per requirements of our framework, that is classification of tumor into three classes. The overall architecture of `SqueezeNet` model is given in [Fig. 2](#chap11.xhtml#fig2), where the macro-architecture is actually system-level organization of multiple modules and integrating them into an end-to-end CNN architecture. The main strategies while designing this architecture include: (1) to replace 3 × 3 filters with 1 × 1 filters that contain 9 × less parameters than 3 × 3 filters, (2) to reduce the input channels to 3 × 3 filters that perform down-sampling in the architecture such that all the convolutional layers have large activation maps. After the `conv-10` layer, the `Softmax` layer is also modified, which contains only 3-number of classes according to requirements of our work which actually was trained on 1,000 classes of ImageNet dataset. We modified the `Softmax` layer of CNN architecture of `SqueezeNet` to three brain tumor classes, as it is responsible for the final. This layer is modified because output of `Softmax` layer is used to represent categorical distribution, like probability distribution over three different classes in our system. In `conv-10` layer, all the global and local features of the input are learned completely and these features are then input to `Softmax` classifier.

![](images/p264-1.jpg)

**Figure 1:** Overall proposed framework.

![](images/p264-2.jpg)

**Figure 2:** `SqueezeNet` [[18](#chap11.xhtml#fsr18)] architecture.

### 3.2 SqueezeNet architecture

`SqueezeNet` architecture has first convolutional layer (`conv-1`), and next 8-fire modules (`fire 2–9`) with a final convolutional layer (`conv-10`). Max pooling is also applied with 2 stride after `conv-1`, `fire4`, `fire8` and last `conv-10`.

Testing phase involves checking the accuracy of the trained model over a number of test images distributed at the beginning into training, validation and testing sets. Algorithm 1 shows the mechanism of overall proposed system.

**Algorithm 1: Computing the class of brain tumor**

**Input:** Brain MRI image

**Functions:**

**P = Train (I)**

**Train (I):**
```
1.Load the proposed CNN network architecture
2.Resize the image into 227
3.Pass the image into the loaded CNN network
4.At the last Softmax layer, make a prediction
5.Return P
```
**label = search for the prediction in label txt file**

**Output:** label

![](images/p266-1.jpg)

**Figure 3:** `GoogLeNet` [[19](#chap11.xhtml#fsr19)] architecture (left–right).

### 3.3 Fine tuning GoogLeNet model

For the training process of `GoogLeNet` model, the last three layers of the `GoogLeNet` architecture have been modified according to our proposed dataset. A detailed architecture of `GoogLeNet` model is shown in [Fig. 3](#chap11.xhtml#fig3). `GoogLeNet` architecture uses a series of nine interconnected inception modules, after the last inception module we add a new average pooling layer to our model which also connects our trained layers of the model to our new modified layers. After average pooling, we modify the architecture by adding a fully connected layer to our fine-tuned model. At the end, we modify our `Softmax` layer to 3 classes to output probabilities in accord to our desired dataset.

### 3.4 GoogLeNet architecture

`GoogLeNet` is one of the first architectures which introduced the inception module that helped significantly in dropping off the number of trainable weights in a network. It contains a parallel combination of convolution layers, i.e., 1 × 1, 3 × 3 and 5 × 5 convolutions alongside a single max-pooling layer. Furthermore, a convolutional Layer of 1 × 1 is also included in the network before the other two convolutions, i.e., 3 × 3 and 5 × 5, due to dimensionality reduction. `GoogLeNet` architecture consists of nine inception modules, holding 22 layers, four max-pooling and an average-pooling layer. In all convolutional layers and inception modules, the `ReLU` activation function is used.

## 4. Experimental Results

In this section, the performance of the proposed system is evaluated using different accuracy assessment metrics. The experimental settings with the benchmark dataset are described in subsequent subsections.

### 4.1 Brain tumor dataset

The proposed system is evaluated on brain tumor [[20](#chap11.xhtml#fsr20)] benchmark dataset. This dataset consists of 2D slices of brain T1-weighted MRI. These T1-weighted MR images are gathered from Nanfang Hospital, Guangzhou, China and General Hospital, Tianjing Medical University, China, recorded in the period 2005–2010. They collected a total of 3,064 slices of MRI from 233 different patients and divided them into three different categories.

i. Meningioma, found in 708 MRI slices.
ii. Glioma, found in 1,426 slices of MRI.
iii. Pituitary tumor, found in 930 MRI slices.

All these MRI slices have a plane resolution of 512 × 512. The gap between two slices is 1 mm, while the thickness of each slice is 6 mm. The ground truth of the dataset is manually segmented and delineated by three different experienced radiologists of those hospitals. The samples of all classes with the highlighted tumor are presented in [Fig. 4](#chap11.xhtml#fig4).

#### 4.1.1 Related research review

This section contains the contribution of researchers on Brain Tumor Dataset. First of all, in 2018 Afshar and Mohammadi *et al*. [[21](#chap11.xhtml#fsr21)] proposed a technique named capsule network architecture for brain tumor classification using standard brain tumor dataset. After that, Abiwinanda *et al*. [[22](#chap11.xhtml#fsr22)] proposed a CNN model for classification with an accuracy of 84.19%. In 2019, Hussain *et al*. [[23](#chap11.xhtml#fsr23)] improved that accuracy up to 90% using Genetic algorithm for classification.

![](images/p267-1.jpg)

**Figure 4:** Brain tumor dataset MRI sample of original and segmented slices of each class.
