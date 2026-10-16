
![Figure 2.27. The phase contrast input images are displayed on the left-most side and indicated by (a) and (d). The analogous segmentation output is indicated by (b) and (c). (Reproduced with permission from \[50\].)](images/bk978-0-7503-2244-7ch2f27_online.jpg)

**Figure 2.27.** The phase contrast input images are displayed on the left-most side and indicated by (a) and (d). The analogous segmentation output is indicated by (b) and (c). (Reproduced with permission from \[[50](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib50)\].)

### 2.3.4.2 Classification and segmentation of microscopy images

In \[[51](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib51)\] an approach for multi-instance learning (MIL) was combined with deep learning CNN for object detection. Instead of a single instance, multi-instance learning learns from a group of instances. In this work the similarity of the CNN pooling layer and the aggregation function of multi-instance learning was used, where features from the CNN corresponded to instance features of the multi-instance learning \[[51](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib51)\]. The CNN produced image characterization of different shapes and sizes through multi-instance pooling layers. The softmax activations of output nodes were backpropagated through the CNN network to generate Jacobian maps for class predictions. Then thresholding was applied on the sum of Jacobian maps along the network input channels to generate the segmentation masks. A loopy belief network was employed to improve the localization prospects (reference \[10\] in \[[51](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib51)\]. The CNN model consisted of seven convolutions, four pooling layers, one multi-instance learning pooling layer, and one fully connected layer. The dataset consisted of microscopic MFC-7 breast cancer cell images, of which 300 were used for training and 40 for testing. Another dataset consisting of green fluorescent protein yeast data was used out of which 2200 images were used for training and 280 images were used for testing. For validation purposes, the MNIST dataset was used where 50 and 10 images were used for training and testing, respectively. The accuracy for the MFC-7 and yeast datasets were 0.97 and 0.96, respectively. The test error was 0%. The process of the model and the segmentation output are shown in figures [2.28](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig28) and [2.29](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig29), respectively.

![Figure 2.28. Model depiction for deep multiple instance learning.](images/bk978-0-7503-2244-7ch2f28_online.jpg)

**Figure 2.28.** Model depiction for deep multiple instance learning.

![Figure 2.29. Segmentation using the FCN-MIL pooling methodology. (a) The Jacobian maps, (b) thresholding, (c) denoising using loopy bp, and (d) segmentation outlines. (Reproduced with permission from \[51\].)](images/bk978-0-7503-2244-7ch2f29_online.jpg)

**Figure 2.29.** Segmentation using the FCN-MIL pooling methodology. (a) The Jacobian maps, (b) thresholding, (c) denoising using loopy bp, and (d) segmentation outlines. (Reproduced with permission from \[[51](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib51)\].)

### 2.3.5 Dermatology application

A significant percentage of people are affected by skin cancer globally. This subsection provides a guide to DL application in melanoma recognition.

#### 2.3.5.1 DL based melanoma recognition

Among all types of skin cancers, melanoma has the highest fatality rate. If detected early melanoma can be cured. The ML based automated techniques for melanoma detection from biomedical images have limited performance, as they are dependent on an intermediate manual feature mining stage. In \[[52](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib52)\] DL was applied to detect melanoma from biomedical images. The DL architecture drew inspiration from UNet, CNN, and ResNets \[[53](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib53)\]. The two primary elements of the model were segmentation and classification. The network consisted of three layers of convolution and pooling followed by three layers of deconvolution and upsampling. Skip operations were employed to merge the feature maps in the intermediate layers of convolution and deconvolution, to recover spatial information lost during down-sampling. The dataset was derived from the ISIC2016 challenge, of which 900 images and 379 images were used for training and testing, respectively. Finally, the segmented output was segregated using an SVM. The system performed with an accuracy of 76.0% whereas the average performance of eight dermatologists was 70.5%. This proved that the DL based automated diagnosis system performed better. The process model and segmentation outputs are displayed in figures [2.30](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig30) and [2.31](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig31), respectively.

![Figure 2.30. Segmentation and classification of melanoma.](images/bk978-0-7503-2244-7ch2f30_online.jpg)

**Figure 2.30.** Segmentation and classification of melanoma.

![Figure 2.31. Segmentation of melanoma of nine patients using FCN-UNet. Row one shows the input images, row two is the corresponding ground truth, and row three is the analogous segmentation output. (Reproduced with permission from \[52\].)](images/bk978-0-7503-2244-7ch2f31_online.jpg)

**Figure 2.31.** Segmentation of melanoma of nine patients using FCN-UNet. Row one shows the input images, row two is the corresponding ground truth, and row three is the analogous segmentation output. (Reproduced with permission from \[[52](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib52)\].)

### 2.3.6 Gastroenterology applications

DL has been applied to liver tumor detection and risk characterization for diagnosis and the preparation of treatment plans for patients from biomedical CT images.

#### 2.3.6.1 Segmentation of liver tumors

In a recent report by WHO, liver cancer was the second main cause of death among all forms of cancer. The appearance of liver lesions in CT images is fuzzy and heterogeneous, with varying densities, shapes, and sizes, hence making detection difficult. In \[[54](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib54)\] DL was applied for segmentation of tumor lesions from liver CT images. A patch based method was applied for characterization. The CNN model comprised two convolution layers, two max-pooling layers, and one softmax layer. A 30 CT image dataset was used for the experiment. Initially, the patches were pre-processed and annotated as positive if they comprised >50% lesion, otherwise they were annotated as negative. Three ML techniques were also applied for benchmarking, i.e. AdaBoost, random forest, and an SVM. The results show that the DL method outperformed the other techniques with a DM coefficient of 80.06% (SVM = 79.78%, random forest = 79.47%, and AdaBoost = 75.67%). The process of the model and segmentation outputs are shown in figures [2.32](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig32) and [2.33](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig33), respectively.

![Figure 2.32. Segmentation of CT liver tumor.](images/bk978-0-7503-2244-7ch2f32_online.jpg)

**Figure 2.32.** Segmentation of CT liver tumor.

![Figure 2.33. Segmentation of CT liver tumor for four patients using AdaBoost (purple) in row one, random forest (green) in row two, an SVM (blue) in row three, and a CNN (red) in row four. The ground truth is displayed in yellow in all rows. (Reproduced with permission from \[54\].)](images/bk978-0-7503-2244-7ch2f33_online.jpg)

**Figure 2.33.** Segmentation of CT liver tumor for four patients using AdaBoost (purple) in row one, random forest (green) in row two, an SVM (blue) in row three, and a CNN (red) in row four. The ground truth is displayed in yellow in all rows. (Reproduced with permission from \[[54](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib54)\].)

#### 2.3.7 Pulmonary application
