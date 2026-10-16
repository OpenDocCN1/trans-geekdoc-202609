
Over the years, major corporations entered the ImageNet challenge, bringing the test error rate to 2.25% recently with the DL depth increasing and novel variations in each layer of the DL models \[[31](#Chapter_1.xhtml#bk978-0-7503-2244-7ch1bib31)–[35](#Chapter_1.xhtml#bk978-0-7503-2244-7ch1bib35)\] (shown in table [1.1](#Chapter_1.xhtml#bk978-0-7503-2244-7ch1t1)). One of the major differences between ML and DL models is the nature of feature extraction. As already stated, the ML paradigm is a two-stage process where the first stage assumes the feature extraction part. In general, a pre-processing step is applied before the ML paradigm for removing noise before feature extraction. In contrast, DL models are a single-stage system and can be fed raw images for feature extraction which use several rounds of dimensionality reduction, extracting the non-linear relationship within patterns of data for characterization or segmentation. The depth of DL models allows the learning of complex relationships and non-linear dependences within data elements ultimately providing unique high-level features for the classifier. This unique character of extracting features leads to superior learning, thus leading to higher accuracy. Additionally, the automated feature extraction feature allows multi-institutional, cross-country datasets to be used for integrated learning, leading to better generalization when compared to conventional models. The DL models also allow multi-task learning, i.e. allowing classification and segmentation of the same dataset \[[36](#Chapter_1.xhtml#bk978-0-7503-2244-7ch1bib36)\]. They also explain how the VC neuronal network responds to visual stimuli \[[37](#Chapter_1.xhtml#bk978-0-7503-2244-7ch1bib37)–[39](#Chapter_1.xhtml#bk978-0-7503-2244-7ch1bib39)\]. This characteristic also allows the DL model trained on a dataset to be applied on a different dataset if the cortical representation of the objects is similar in nature. This particular paradigm of learning is called transfer learning (TL), and is popular amongst the deep learning community \[[40](#Chapter_1.xhtml#bk978-0-7503-2244-7ch1bib40)–[45](#Chapter_1.xhtml#bk978-0-7503-2244-7ch1bib45)\].

**Table 1.1.** Top performing DL models in ImageNet from 2012 to 2017. (Reproduced with permission from \[[110](#Chapter_1.xhtml#bk978-0-7503-2244-7ch1bib110)\]. Copyright 2019 Elsevier.)

| Model || Year || Top-five error rate |

| --- | --- | --- |

| AlexNet || 2012 || 15.30% |

| --- | --- | --- |

| VGG16 || 2014 || 7.30% |

| GoogleNet || 2015 || 3.58% |

| ResNet || 2016 || 3.57% |

| Squeeze-and-excitation || 2017 || 2.25% |

The most common DL model is the convolutional neural network (CNN), which is used widely in medical imaging characterization and segmentation \[[30](#Chapter_1.xhtml#bk978-0-7503-2244-7ch1bib30)\] (shown in figure [1.2](#Chapter_1.xhtml#bk978-0-7503-2244-7ch1fig2)). CNNs use a three layer model repeatedly to mine features from medical images; the layers are the convolutional, rectifier linear unit (ReLu), and pooling layers. The convolutional layer is represented as a group of convolution kernels analogous to the network connections of the ANNs \[[46](#Chapter_1.xhtml#bk978-0-7503-2244-7ch1bib46)\]. However, in a CNN these kernels are a matrix of weights multiplied point-wise with each pixel value of the input image to generate feature maps, which are basically a filtered version of the real image. However, in this case each pixel value of the feature map is a function of its neighbouring pixels. This is done to find the contextual relationship present within patterns in the image.

![Figure 1.2. A convolutional neural network. (Image courtesy of AtheroPoint™. Reproduced with permission from \[110\]. Copyright 2019 Elsevier.)](images/bk978-0-7503-2244-7ch1f2_online.jpg)

**Figure 1.2.** A convolutional neural network. (Image courtesy of AtheroPoint™. Reproduced with permission from \[[110](#Chapter_1.xhtml#bk978-0-7503-2244-7ch1bib110)\]. Copyright 2019 Elsevier.)

A representative diagram of the convolution operation is shown in figure [1.3](#Chapter_1.xhtml#bk978-0-7503-2244-7ch1fig3). The purpose of the ReLu layer is to filter the feature maps such that they contain positive values only. The reason for this is to overcome the vanishing gradient problem. The pooling layer is used for dimensionality reduction where only the significant aspect of the high-dimensional feature map is reserved in the low-dimensional version of it when applied. These layers are applied multiple times to mine high-level features. These features are used by the fully connected network for characterization. Autoencoders are unsupervised DL models used specifically for image restoration and regeneration \[[47](#Chapter_1.xhtml#bk978-0-7503-2244-7ch1bib47)\]. Autoencoders have also been used to remove noise or generate an ROI. The autoencoders are a two-stage DL model: the encoder for image dimension reduction and the decoder for dimensionality restoration. Therefore, the number of input and output neurons is the same in the autoencoder. The encoder performs dimensionality reduction so that the network learns the compact representation of the input image. Residual neural networks (ResNets) \[[34](#Chapter_1.xhtml#bk978-0-7503-2244-7ch1bib34)\] are DL networks which are able to avoid the issue of vanishing gradients by skipping learning in some layers, which helps to avoid accuracy saturation. Deep belief networks (DBNs) are unsupervised DL models which use multiple layers of restricted Boltzmann machines \[[48](#Chapter_1.xhtml#bk978-0-7503-2244-7ch1bib48)\]. The lower layer connections are directed, whereas the top layers are undirected, forming associative memory. Learning happens layer by layer. DBNs, like autoencoders, are used for image restoration, recognition etc. The classification tree of DL models is given in figure [1.4](#Chapter_1.xhtml#bk978-0-7503-2244-7ch1fig4). In the following sections the current and potential scenarios for DL in radiology are discussed, including the potential for DL in radiology, the dangers of DL are evaluated, and finally the conclusion is presented.

![Figure 1.3. Convolution operation. (Image courtesy of AtheroPoint™. Reproduced with permission from \[110\]. Copyright 2019 Elsevier.)](images/bk978-0-7503-2244-7ch1f3_online.jpg)

**Figure 1.3.** Convolution operation. (Image courtesy of AtheroPoint™. Reproduced with permission from \[[110](#Chapter_1.xhtml#bk978-0-7503-2244-7ch1bib110)\]. Copyright 2019 Elsevier.)

![Figure 1.4. Deep learning systems classification tree. (Image courtesy of AtheroPoint™. Reproduced with permission from \[110\]. Copyright 2019 Elsevier.)](images/bk978-0-7503-2244-7ch1f4_online.jpg)

**Figure 1.4.** Deep learning systems classification tree. (Image courtesy of AtheroPoint™. Reproduced with permission from \[[110](#Chapter_1.xhtml#bk978-0-7503-2244-7ch1bib110)\]. Copyright 2019 Elsevier.)

### 1.2 The present

DL has affected the medical imaging field largely due to its diagnostic accuracy and robustness. Some recent papers in radiology are presented in the following sections.

#### 1.2.1 Fatty liver disease risk stratification
