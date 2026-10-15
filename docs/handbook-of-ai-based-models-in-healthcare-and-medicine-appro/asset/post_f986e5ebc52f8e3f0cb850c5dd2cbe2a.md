
![](img/a2fc2296b12812e9151e817bff1de16d_181_0.png)

FIGURE 9.2 Sample MRI scans depicting various stages of AD. The MD and MOD images are visible in the first and second columns, respectively. A few ND and VMD images are represented in the third and fourth columns, respectively.

## 9.3.2 PROPOSED FRAMEWORK

The typical workflow of the suggested approach is illustrated in Figure 9.3. It has three primary modules: preprocessing, feature extraction and classification, and ensemble learning. The oversampling data-level technique and image resizing are carried out during preprocessing. The feature extraction and classification module extracts the pertinent attributes and classifies them using customized EfficientNet-B0 and customized ViT models. The best configurations from CNN and ViT are picked for further processing. To enhance the overall performance, ensemble learning is adopted in the final stage. This stage involves ensemble selection, probability averaging, and classification.

### Preprocessing
Generally, deep CNN yield better outcomes with huge data. The data distribution confirms the presence of a class imbalance problem. To address this, an oversampling data-level technique is utilized. The training set images are enlarged using a rotation augmentation technique to yield a balanced dataset. Table 9.1 depicts the details of the augmentation method with relevant parameters.

![](img/a2fc2296b12812e9151e817bff1de16d_182_0.png)

FIGURE 9.3 Workflow of the suggested approach for AD classification.

### TABLE 9.1
Details of Augmentation Technique

| Number of Images in Original Dataset | Step Size | Angle of Rotation | Number of Images in Generated Dataset |
|---|---|---|---|
| MD: 717 | 1 | 0 and 6 | MD: 5019 |
| MOD: 52 | 0.1 | 1 and 10 | MOD: 5200 |
| ND: 2560 | 1 | 0 and 1 | ND: 5120 |
| VMD: 1792 | 1 | 0 and 2 | VMD: 5376 |

Classification using customized EfficientNet-B0: EfficientNet-B0 is trained with a larger number of samples from the ImageNet database. Due to this, the model learns descriptive image features effectively. Therefore, fine-tuning the model simplifies the learning process. The model is modified by tweaking the final layers. Figure 9.4 illustrates the attribute extraction using the EfficientNet-B0 model.

### Feature extraction
EfficientNet models proposed by Tan et al. have garnered considerable interest because of the inclusion of the compound scaling technique [26]. It scales resolution, depth, and width evenly using a group of parameters represented by the following equations:

depth: d = δ^θ
(9.1)

width: w = φ^θ  (9.2)

resolution: r = ζ^θ  (9.3)

where θ is a compound parameter and δ, φ, and ζ are the scaling parameters of individual dimensions. A grid search technique is employed to select the optimum values of coefficients by validating the constraints δ φ² ζ² ≈ 2 and δ ≥ 1, φ ≥ 1, ζ ≥ 1. The layers of the model are outlined in Table 9.2.

![](img/a2fc2296b12812e9151e817bff1de16d_183_0.png)

FIGURE 9.4 Pertinent attribute extraction using modified EfficientNet-B0 CNN.

### TABLE 9.2
Details of EfficientNet-B0 Model

| Stage | Operator | Resolution | No. of Channels | No. of Layers |
|---|---|---|---|---|
| 1 | Conv k3 | 224×224 | 32 | 1 |
| 2 | MIBConv1, k3 | 112×112 | 16 | 1 |
| 3 | MIBConv6, k3 | 112×112 | 24 | 2 |
| 4 | MIBConv6, k5 | 56×56 | 40 | 2 |
| 5 | MIBConv6, k3 | 28×28 | 80 | 3 |
| 6 | MIBConv6, k5 | 14×14 | 112 | 3 |
| 7 | MIBConv6, k5 | 14×14 | 192 | 4 |
| 8 | MIBConv6, k3 | 7×7 | 320 | 1 |
| 9 | Conv k1/pooling/FC | 7×7 | 1280 | 1 |

k3: 3×3, k5: 5×5, and k1: 1×1

### Feature selection
Choosing robust features may aid in the effective categorization of AD stages. Haar wavelet transform and PCA are employed to accomplish this. First, the extracted features are decomposed using the Haar wavelet. Approximation and detail bands are provided by the decomposition. It is evident that the approximation band has a greater impact on AD characteristics. Thus, exploring only the low-frequency band may drastically decrease the number of attributes required for classification [27]. Secondly, PCA is utilized to obtain the valid attributes from the bands. Reconstruction of the attributes is carried out by zeroing the parameters of the detail band and unaltering the parameters of the approximation band. Then, PCA is employed to generate relevant attributes for categorization.

### Classification
The appropriate selection of the classifier may significantly improve the outcome of AD categorization. The robust features are classified into four classes using the Bi-LSTM network [28]. This is a group of two LSTMs, with one taking the input sequence from beginning to end and the other taking the input sequence in reverse order.

### Classification using customized ViT
This work employs the customized ViT for AD classification. This is accomplished through the use of the transfer learning approach. The ViT model utilized for the natural image task is fine-tuned for the AD classification stage. The basic representation of customized ViT is presented in Figure 9.5. The transformer encoder is a crucial component of ViT. It includes a group of several equivalent layers. Each layer is made of multi-head attention and the MLP. Two Gaussian error linear unit (GELU) nonlinear layers are included in MLP. After layer normalization, a residual connection is used around each of the two sub-layers (Lnorm). The transformer accepts a sequence of N-embedded patches ($L_p^i$) and a special token ($L_{sp}$). Each patch embedding is appended with learnable position embeddings, mathematically represented by the following equations:

![](img/a2fc2296b12812e9151e817bff1de16d_184_0.png)

FIGURE 9.5 Extraction of pertinent features using customized ViT.

$X_o = [L_{sp}; L_p^1; L_p^2; ...; L_p^N] + L_{pos}$  (9.4)

$X_l^* = MSA(Lnorm(X_{l-1}) + X_{l-1})$  (9.5)

$X_l = MLP(Lnorm(X_l^*) + X_l^*)$  (9.6)

$Y = Lnorm(X_0)$  (9.7)

### Ensemble learning
Ensemble learning is predominantly employed to enhance performance as well as to improve robustness. In this work, a stacking ensemble technique is employed [29]. The best configuration of the EfficientNet-B0 model and the best ViT model are selected. The metric classification accuracy is considered for the selection process. The likelihood scores of the selected models are averaged using:

$P_{Final}(B_k) = \left( \sum_{i=1}^{N} P_{s(i)}(B_k) \right) / N$  (9.8)

where $P_{Final}(B_k)$ represents the ultimate likelihood score of $B_k$, $k$ is the class indicator, $P_s(B_k)$ represents the likelihood score, and $N$ denotes the total models used in the ensemble. Final prediction is performed using the SVM classifier.

## 9.4 EXPERIMENTAL FINDINGS

Throughout training, the preliminary layers of the model are preserved, whereas the end layers are customized to four-class tasks. Figure 9.6 depicts the amount of samples in unaugmented and generated databases. The model is trained with 5019 MD images, 5200 MOD images, 5120 ND images, and 5376 VMD images. Since the Adam optimizer [30] performs well for a majority of image classification tasks [31], it is employed with a learning rate of 0.0001. Experimentation is carried out with epochs of 20 and a batch size of 32. The trainable variables are modified to mitigate the cross-entropy loss specified by

$loss = - \sum_{i=1}^{S} \sum_{j=1}^{C} t_{ij} ln(p_{ij})$  (9.9)

where $S$ is sample length, $C$ is total classes, $t_{ij}$ indicates target output, and $p_{ij}$ indicates the predicted output. The model is evaluated with 1279 images (179 MD, 12 MOD, 640 ND, and 448 VMD) in different settings, which are mentioned below.

![](img/a2fc2296b12812e9151e817bff1de16d_186_0.png)

FIGURE 9.6 Distribution of images in the dataset. This dataset includes 896 MD, 64 MOD, 3200 ND, and 2240 VMD images.

- S1: The likelihood scores obtained from the softmax function are employed to categorize the images into different classes.
- S2 and S3: SVM and KNN classifiers are used to categorize the extracted features in settings S2 and S3, respectively. The attributes are acquired from the global average pooling layer.
- S4: The Bi-LSTM network is used in this setting. The model is assessed using pertinent attributes. Classification is carried out based on the likelihood scores acquired through the softmax function.
- S5, S6, and S7: These settings explore the efficacy of feature selection using the Haar wavelet transform. SVM, KNN, and Bi-LSTM are used to classify the transformed attributes in S5, S6, and S7 settings, respectively.
- S8, S9, and S10: The relevance of robust features for AD classification is analyzed in these settings. PCA is used to select robust features. SVM, KNN, and Bi-LSTM are used to classify robust features in settings S8, S9, and S10.

The following metrics are used to assess the efficacy of the various settings:

### Accuracy (ACC)
This indicates the total samples predicted correctly by the model. It is specified as

$$ACC = \frac{TPM + TPMO + TPVM + TPN}{N} \qquad (9.10)$$
