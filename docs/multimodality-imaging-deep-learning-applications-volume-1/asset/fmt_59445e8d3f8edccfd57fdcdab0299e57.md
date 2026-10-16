
The occurrence of mitotic cells in histology images is a precursor to breast cancer. These mitosis processes represent the complex transformations that the cell nucleus undergoes. Although similar structures of same intensity, shape, and size exist, only a very few are mitotic cells and therefore require extensive evaluation using deep learning models. In this study, DL based CNN models were applied to characterize mitotic and non-mitotic cells \[[48](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib48)\]. An ensemble classifier based on two separate CNN models was developed. The first CNN consisted of 13 layers (input + five convolution + five max-pooling + two fully connected layers) and the second CNN consisted of 11 layers (input + four convolution + four max-pooling + two fully connected layers). The outputs were later pooled in the ensemble version. The ensemble DL based classifier was trained and tested using 50 images taken from the MITOSIS dataset. The performance parameters of precision and F1 score were 0.88 and 0.78, respectively. The process model and the outputs are shown in figures [2.22](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig22) and [2.23](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig23), respectively. Although the results were better compared to others in the ICPR2012 challenge, a greater number of training images would have led to better generalization.

![Figure 2.22. DL based breast cancer detection.](images/bk978-0-7503-2244-7ch2f22_online.jpg)

**Figure 2.22.** DL based breast cancer detection.

![Figure 2.23. The left-most image show by arrow (a) represents the image with three dotted areas. The three dotted areas are displayed in detail as indicated by arrows (b), (c), and (d). Mitosis detected by the system is shown in green, red represents a false positive, and cyan signifies mitosis not detected by the given approach. (Reproduced with permission from \[48\]. Copyright 2013 Springer.)](images/bk978-0-7503-2244-7ch2f23_online.jpg)

**Figure 2.23.** The left-most image show by arrow (a) represents the image with three dotted areas. The three dotted areas are displayed in detail as indicated by arrows (b), (c), and (d). Mitosis detected by the system is shown in green, red represents a false positive, and cyan signifies mitosis not detected by the given approach. (Reproduced with permission from \[[48](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib48)\]. Copyright 2013 Springer.)

#### 2.3.3.2 Digital mammographic tumor classification

The conventional model of breast cancer diagnosis involves feature mining and application of statistical modeling for predicting malignancy. In \[[49](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib49)\] CNN transfer learning is used for categorization of breast lesions from mammography images. Further, this study also compared the features mined from a deep learning model and hand crafted lesion features. The CNN model used in the work was first trained in general object recognition, which is entirely different from breast cancer data. Finally, the trained CNN model was tested on the mammography images. It is hypothesized that models trained in a general setting are able to recognize minute details of specialized biomedical images such as breast cancer. Here, the dataset constituted 219 breast lesions from digital mammography images. A total of 607 ROIs were mined. AlexNet, a popular CNN model, was used for feature mining. The AlexNet model consisted of five convolution layers and three fully connected layers. Another set of features was mined using analytically mined handmade features. Two SVM classifiers were trained separately on the two sets of features: deep features (process P1) and handmade features (process P2). The classification outputs were combined from both P1 and P2 to make the ensemble classifier (P1 + P2). It can be seen that the performance of the ensemble classifier AUC was better than that of P2 (an AUC of 0.86 versus an AUC of 0.81). The process model and analogous output images are shown in figures [2.24](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig24) and [2.25](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig25), respectively.

![Figure 2.24. DL based breast tumor detection.](images/bk978-0-7503-2244-7ch2f24_online.jpg)

**Figure 2.24.** DL based breast tumor detection.

![Figure 2.25. The outputs of different layers of AlexNet are shown: (a) the ROI input; (b) the output of pooling layer one; (c) the outputs of pooling layer two; (d) the output of convolution layer four; and (e) the output of pooling layer five. These are fed into conventional methods for characterization. (Reproduced with permission from \[49\]. Copyright 2016 Society of Photo‑Optical Instrumentation Engineers.)](images/bk978-0-7503-2244-7ch2f25_online.jpg)

**Figure 2.25.** The outputs of different layers of AlexNet are shown: (a) the ROI input; (b) the output of pooling layer one; (c) the outputs of pooling layer two; (d) the output of convolution layer four; and (e) the output of pooling layer five. These are fed into conventional methods for characterization. (Reproduced with permission from \[[49](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib49)\]. Copyright 2016 Society of Photo‑Optical Instrumentation Engineers.)

#### 2.3.4 Microscopy applications

The applications of deep learning in microscopy are discussed in here.

##### 2.3.4 1 Analysis of individual cells in a live-cell imaging experiment

In cellular biology, a powerful research technique is dynamic live-cell imaging experiments. Cells are cultivated manually for hours for proper identification. Automated techniques such as deep learning can provide faster and more accurate results in both segmentation and accuracy. In \[[50](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib50)\] a DL based model was employed for automated segmentation and characterization. Several CNNs were employed to track the growth of bacterial cells and individual mammalian nuclei without manual intervention. The patching methodology was applied, where the patches were mined from the image and annotated with their respective class. This process of patching and annotating was repeated for all the images. Thereafter, the classifier was trained and tested to characterize each patch. After classification all the labelled patches were combined to give the segmented image. The cost function applied for the function is

``` 
C = - \sum_{i} \log \left( \frac{e^{label}}{\sum_{l}e^{l}} \right) + \tau \sum_{w \in \mathbf{W}} w^{2},
```

(2.14) graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch2eqn46.gif" position="float"/

where *C* is the cost function, *i* is the images, *l* is the labels, *w* is the weights, *τ* is the regularization parameter, and *W* represents all the weights. The weights are updated as per the formula

``` 
w_{i + 1} = w_{i} - \eta \frac{\\partial C}{\\partial w},
```

(2.15) graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch2eqn47.gif" position="float"/

where *i* denotes the iterations, *η* represents the learning rate, and $\\frac{\\partial C}{\\partial w}$ inline-graphic style="height:1.75em;" xlink:href="bk978-0-7503-2244-7ch2ieqn48.gif" is the gradient of cost with respect to weight. The mammalian cells were categorized into five types. In each image there were approximately 300 nuclei, 500 nuclei, and 100 mammalian cells. The images were pre-processed and artificially augmented using rotation. The Jaccard index and Dice metric for the operation were 0.89 and 0.94, respectively. Model parallelism was achieved using GPUs. The process model and segmented output are shown in figures [2.26](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig26) and [2.27](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig27), respectively.

![Figure 2.26. Model depicting the segmentation of individual cells using DL.](images/bk978-0-7503-2244-7ch2f26_online.jpg)

**Figure 2.26.** Model depicting the segmentation of individual cells using DL.
