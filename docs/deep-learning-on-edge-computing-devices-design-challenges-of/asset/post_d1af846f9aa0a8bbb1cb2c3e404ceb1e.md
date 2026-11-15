
![](img/5fa4874adaccc5ede04575a2e9e5662a_138_0.png)

Figure 7.9 (a) Classification accuracy of the DANs and DBNs with different weight decay approaches. The connection weights are thresholded with the \(\sigma\%\) significant weights reserved and represented using single-bit integers. (b) Memory required for weight parameters of the DBN and DAN.

To achieve higher hardware efficiency, the DAN can use binary activations and binary weights. Fig. 7.9(a) also shows the influence of adopting binary activation on classification accuracy. The activations of the DAN_B are thresholded and binarized using a constant 0.5. As shown in Fig. 7.9(a), the accuracy of the neural network classifier proceeded by the DAN_B is significantly higher than the DBN. By adopting binary weights and activations the DANoC coprocessor can replace the complex floating-point multipliers with simple fixed-point accumulators and implements the sigmoid activation function using simple threshold operations.

By adopting the sparse binary connections the DAN becomes 99.3% (\(\sigma = 20\%\)) to 99.9% (\(\sigma = 5\%\)) more memory efficient than the single-precision DBN. Fig. 7.9(b) shows the theoretical results of the memory used by the DAN and original DBN. The memory complexity of the deep neural networks increases as the number of neurons increases. The present DBNs are usually implemented using 32-bit representation; however, with sparse and binary weights, the DAN_B can improve the memory efficiency by two to three orders of magnitude.

## 7.4.3 Hyperspectral remote sensing images

The second experiment applies the DAN algorithm and the DANoC system to the hyperspectral remote sensing application. Differently from visible-light images, the hyperspectral images contain information from across the electromagnetic spectrum. Fig. 7.10 shows the Pavia Center

![](img/5fa4874adaccc5ede04575a2e9e5662a_139_0.png)

Figure 7.10 The Pavia Center image and the ground-truth labels for each pixel. The Pavia Center set has 1.2 million samples. The DBN-based classification of each sample contains 10.9 million operations, and the Zynq7100-based DANoC achieves 2036 effective GOPS at 1.9 watts power consumption.

| Datasets | Bands | Samples (million) | Features | Classes |
|---|---|---|---|---|
| Indian Pines | 224 | 0.02 | 2016 | 16 |
| Salinas | 224 | 0.11 | 2016 | 16 |
| Pavia University | 103 | 0.37 | 927 | 9 |
| Pavia Center | 102 | 1.20 | 918 | 9 |

dataset, which contains 1.2 million samples. Each pixel in the image is recorded with 102 spectral bands covering the wavelengths from 401 nm to 889 nm. The goal of classification is determining nine labels associated with each pixel.

Our experiments examine four well-known datasets of hyperspectral images (Table 7.1). All the examined datasets are downloaded from the hyperspectral website [32]. The scene of the Indian Pines is gathered by the AVIRIS sensor and consists of 21025 samples with 224 spectral reflectance bands in the wavelength ranging from 0.4 × 10−6 to 2.5 × 10−6 meters. The label of each pixel falls into sixteen classes. The Salinas dataset is collected by the 224-band AVIRIS sensor over the Salinas Valley, California, and is characterized by high spatial resolution (3.7-meter pixels). The area covered comprises 11.11 thousand samples of 16 classes. Similar to the Pavia Center data set, the Pavia University set has nine classes and 0.37 million samples recorded with 103 spectral bands.

Differently from traditional technologies, the hyperspectral imaging can get the spatial and spectral data simultaneously, resulting in high-dimensional samples. For practical remote sensing applications, the number of labeled training samples for each class is usually less than a few hundreds.

| Author | Approaches | Salinas | Indian Pines | Pavia University |
|---|---|---|---|---|
| Zhou | DANoC hardware<sup>a</sup> | 94.19 | 89.03 | 95.33 |
| Yue [33] | CNN regression | - | - | 95.18 |
| Yuan [34] | CART kNN | 89.00 | 81.00 | 89.00 |
| Wang [35] | sparse coding | - | 93.11 | 90.41 |
| Kuo [36] | kernel SVM | - | 88.70 | 94.00 |
| Ramzi [37] | adaboost SVM | 93.12 | 91.59 | 94.28 |
| Li [38] | Markov random field | - | - | 94.96 |
| Plaza [39] | multinomial regression | - | 76.71 | 76.03 |
| Li [40] | Tikhonov method | - | 89.00 | 92.00 |
| Chen [41] | Autoencoder | - | - | 98.52 |
| Liu [42] | Autoencoder | 95.50 | - | 96.40 |
| Zhao [43] | BLDE+CNN | - | - | 96.98 |

<sup>a</sup> The DANoC hardware implements the DAN with binary connections and activations. The compared approaches are generally implemented using 32-bit floating-point representation.

The scarcity of labeled training samples can cause a significant drop in classification accuracy for supervised approaches, which is known as the Hughes phenomenon. Therefore an unsupervised feature extraction process is usually applied before hyperspectral classification. Recently, there has been a lot of interest in the remote sensing area to apply the deep learning algorithms for hyperspectral classification, and the DBN has been reported as the state-of-the-art for extracting features from hyperspectral images [4]. However, it is usually a challenge to deploy the DBN to process remote sensing images in real time, because the embedded systems carried by satellites or unmanned aerial vehicles are generally limited in hardware resources. In this experiment, we show that the efficient DAN algorithm and the DANoC system can provide competitive results with the state-of-the-art approaches for classifying hyperspectral images (Table 7.2).

Fig. 7.11 shows our DAN-based classification process of the spatial-spectral samples, which consists of four steps: (1) Normalization and whitening are applied to reduce the correlation between features; (2) The neighbor region of the target pixel is selected (red square), and the spatial-spectral sample is flattened and arranged as a vector; (3) A DAN is trained and built to extract the features from the high-dimensional vector; (4) The extracted features are classified using a neural network classifier.

Given a target pixel, a neighbor region of nine pixels is constructed to form a high-dimensional spatial–spectral sample.

![](img/5fa4874adaccc5ede04575a2e9e5662a_141_0.png)

Figure 7.11 Spatial–spectral classification of the hyperspectral data using the proposed Deep Adaptive Network. Each pixel in the hyperspectral data is recorded with 102 spectral bands covering the wavelengths from 401 nm to 889 nm.

Different deep neural networks are trained over the Indian Pines dataset (1800–2000–2000), the Salinas dataset (1836–2000–2000), the Pavia Center dataset (918–1000–1000), and the Pavia University dataset (927–1000–1000) for feature selection. Our experiment compares the proposed method with the Deep Belief Network (DBN), the Principal Component Analysis (PCA), and the Independent Component Analysis (ICA), all of which have been proven to be effective for processing the hyperspectral data. Different classifiers, including the Neural Network classifier (NN), the Logistic Regression classifier (LR), the Support Vector Machine (SVM), the Naive Bayes (NB), and the Decision Tree (DT), are examined. All the compared classifiers are implemented using the WEKA software [44]. To calculate the classification accuracy, we randomly selected 50% of unlabeled hyperspectral samples for training the unsupervised DAN, the PCA, and the ICA, and used the remaining samples for testing. The classifiers are trained with 25% labels randomly selected from the training set. The experiment was repeated ten times, and the average classification accuracy and derivation were calculated. Experiment results in Table 7.3 show that the DAN algorithm achieves the highest classification accuracy among all compared approaches over three of the examined datasets (90.90% to 99.59%).

Table 7.2 compares the binary DAN implemented in the DANoC system with the optimal results reported by the latest hyperspectral researches [33–40]. All these researches use the same spatial–spectral samples and similar experiment settings. It seems that the DANoC system can achieve competitive results with the state-of-the-art approaches by taking the advantage of the large-volume unlabeled samples. It is worth noting that the DAN even outperforms some deep learning based approaches including the CNN. Since the labeled training samples are limited and expensive for
