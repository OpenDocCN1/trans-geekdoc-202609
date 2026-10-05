
# Melanoma detection by hybrid attention DCNN-BiLSTM architecture

classified melanoma. The DCNN showed exceptional accuracy when tested on different datasets. The primary objective of the DCNN's design was to effectively extract features from dermoscopic images, resulting in significantly better performance compared to alternative approaches. Yet a limitation of this approach is the need for more elucidation regarding the network's handling of misclassified samples. Considering these methods and their limitations, a novel attention-based DL model is designed for melanoma detection.

# 18.3 PROPOSED METHODOLOGY

The excessive growth of skin cells, which can result in malignant tumours, lead to skin cancer. UV radiation on exposed skin is connected to the majority of skin malignancies. Even with advanced training and dermoscopy use, clinical test sensitivities for dermatologists are limited to 80%. Clinical research requires accurate and automated medical image segmentation and classification. However, traditional methods occasionally perform these jobs inefficiently, especially when dealing with massive datasets. DL models in computer-assisted skin cancer have become prevalent. Their primary function is image classification, and they perform more effectively in this task with more information. Considering this, the identification of melanoma begins with the preprocessing, segmentation, feature extraction, feature selection, and detection using attention-based learning framework.

The initial process starts with the collection of melanoma images from the public resources. In the preprocessing phase, the input images eliminate obstructive spots and hairs employing the Gaussian filter. The Cross-Attention-Net method separates the non-target areas from the preprocessed images. The most discriminative features are extracted using the GLCM technique to enhance classification performance. The feature dimensionality problem is then solved using the AWSO. Using the input samples, a novel Hybrid Attention DCNN-BiLSTM model is proposed to identify skin cancer. Thus, the suggested detection successfully identifies skin cancer with the given inputs. The newly suggested framework is shown in Figure 18.1.

## 18.3.1 Preprocessing

High diagnostic accuracy is achieved through precise lesion area segmentation and feature extraction, primarily dependent on preprocessing techniques. The Gaussian filter is used in the preprocessing stage to remove distracting spots and hairs from the input images [26], thereby improving image quality. This makes it possible to separate the skin lesion from the background of the picture, which makes it possible to use a segmentation technique to identify the affected area precisely [27].

# Transforming Healthcare

![](img/bb14ad24e4d4babb616ee31f6e899c86_396_0.png)

External or natural sources, including hair, distracting items, lighting, shadows, and different image capture techniques, are frequently sources of noise and artifacts. The Gaussian filter is used in images to eliminate Gaussian-weighted average values of nearby or surrounding pixels. One linear filter implemented to minimise noise and enhance image quality is the Gaussian filter. A softened image is produced by the Gaussian smoothing, and the Gaussian distribution's standard deviation dictates the degree of smoothing [28].

Due to the huge size and excellent quality of the images (768×560 pixels with the RGB colour scheme), processing can be computationally intensive. The pixels are shrunk to a resolution of 52×52 pixels while maintaining all of the important details to speed up calculation. The bigger image size is subjected to the Gaussian filter. Unwanted components like hair and stray spots can be eliminated using the Gaussian filter by substituting incorrect pixels with the average of nearby pixels. The selection procedure uses three images—three malignant and three benign. Equation (18.1) illustrates how the Gaussian equation enhances photos by removing noise and unwanted artifacts.

```
$G(p,q) = \frac{1}{2\pi\omega^2} e^{\frac{p^2-q^2}{2\omega^2}} (18.1)$
```

where $p$ represents the distance from the 0, $q$ is the distance along the $x axis, and $\omega$ is the standard deviation of the Gaussian distribution.

Figure 18.1 Melanoma skin cancer detection framework.

## 18.3.2 Segmentation

The Cross Attention-U-Net technique separates the non-target areas from the preprocessed images after preprocessing. The segmentation process extracts significant features from the designated regions of interest. Size, shape, texture, and intensity are a few examples of these characteristics, and each offers important details for tasks involving detection and categorisation. It makes possible to identify regions of interest consistently and reliably across various images. This is especially crucial for medical imaging because accurate results depend on consistent diagnosis of diseases.

### 18.3.2.1 Cross attention-U-Net approach

The cross attention module [29] receives as input $C=\begin{pmatrix}A\\B\end{pmatrix}=\{t_i...t_i;u_i\}$, $C\in A^{(i+n)\times d}$ is the layered properties of image regions. After computing, the subsequent transformer unit is received. Here, the fragments' query key, and value are created using the following formula:

```
$Q_C=CK^Q=\begin{pmatrix}AK^Q\\BK^Q\end{pmatrix}\begin{pmatrix}Q^A\\Q^B\end{pmatrix} (18.2)
```

```
$E_C=CK^K=\begin{pmatrix}AK^E\\BK^E\end{pmatrix}\begin{pmatrix}E^A\\E^B\end{pmatrix} (18.3)$
```

```
$V_C=CK^V=\begin{pmatrix}AK^V\\BK^V\end{pmatrix}\begin{pmatrix}V^A\\V^B\end{pmatrix} (18.4)$
```

The 'Scaled Dot-Product Attention' is then concluded in agreement with the following equation:

```
$Attention(Q_C,E_C,V_C)=soft\max(\left(\frac{Q_CE_C^{E_R}}{\sqrt{d}}\right)\right)V_C (18.5)$
```

By modifying equation (18.5), it can be developed as follows:

```
$Q_CE_C^{E_R}-V_C=\begin{pmatrix}Q_A\\Q_B\end{pmatrix}(E_AE^{E_R}E_BE^{E_R})\begin{pmatrix}V_A\\V_B\end{pmatrix}=\begin{pmatrix}Q_AE_A^{E_R}Q_AE^{E_R}\\Q_BE_A^{E_R}Q_BE^{E_R}\end{pmatrix}\begin{pmatrix}V_A\\V_B\end{pmatrix} (18.6)\n=\begin{pmatrix}Q_AE_AR_V_A+Q_AE^{ER}V_B\\Q_BE^{ER}V_B+Q_BE^{ER}V_A\end{pmatrix}$
```

where $\left(\begin{matrix} A_{up} \\ B_{up} \end{matrix}\right) = Q_C E_C^S \cdot V_C$. The updated features are:

$A_{up} = \{a_{up1}; \dots; a_{upk}\} = Q_A E_A^S V_A + Q_A E_B^S V_B \quad (18.7)$

$B_{up} = \{b_{up1}; \dots; b_{upk}\} = Q_B E_B^S V_B + Q_B E_A^S V_A \quad (18.8)$

The outline shows that this Transformer's multi-head sublayer simultaneously considers its output-intra and intermodality connections.

$\left(\begin{matrix} A_{up} \\ B_{up} \end{matrix}\right)$ can subsequently be transmitted to the position-wise feed-forward sublayer that follows.

The production of the cross-attention module's Transformer unit should be expressed as $C_C = \left(\begin{matrix} A_{up} \\ B_{up} \end{matrix}\right)$.

The decoder and the encoder are the two halves of the symmetric U-Net architecture. The encoder, is the initial part, transforming the input space into lower-dimensional space. Repetitive convolutional blocks support the encoder's modular architecture. Each block used for transformation is split into two smaller blocks. Using a convolutional layer with kernels and strides of $3\times3\times3$ and $2\times2\times2$, the first smaller block reduces the spatial dimensions of the input feature map by a factor of two. When 0.01 is used, the leaky ReLU activation and normalisation slope will be negative. The following feature map is modified using nearly identical techniques, except that the convolutional layer has a stride of $1\times1\times1$.

After the spatial dimensions of the feature map are adjusted to $2\times2\times2$, the decoder part of the procedure occurs. The decoder, having a modular design, to enhance spatial dimensions by reducing the encoder feature. The decoder block is composed of three smaller blocks. The first uses a transpose convolution with kernels and strides of $2\times2\times2$ to quadruple the spatial dimensions of the feature map. Following this, the upsampled and the encoder feature maps from the spatial level are joined.

## 18.3.3 Feature extraction

The GLCM technique was created to classify images with various textures. GLCM is also known as a back-level dependency matrix. In essence, the GLCM method uses a pixel-based methodology. It is a technique for
