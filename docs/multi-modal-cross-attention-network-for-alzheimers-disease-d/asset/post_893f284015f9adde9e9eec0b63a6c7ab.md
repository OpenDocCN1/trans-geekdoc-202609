
J. Zhang et al.

Computers in Biology and Medicine 162 (2023) 107050

![](img/35eb289ac20da6b2112bd8090073aee2_3_0.png)

Fig. 2. Overview of the proposed framework.

The minimum-maximum normalization is used for the feature range [0, 1].

For the representing of CSF biomarkers, Aβ42, Tau, and P-tau are set to insert feature range from 170 to 200, from 0 to 1300, and from 0 to 120, respectively, according to the numerical distribution of CSF biomarkers in the dataset. In this, we get 1500, 130, and 120 for Aβ42, Tau, and P-tau respectively, for computing the CSF vector.

## 3.2. Overview of the proposed framework

In this paper, we propose a novel framework MCAD to tackle the problem of AD diagnosis using multi-modal data. In Fig. 2, the proposed framework MCAD contains three main parts: feature extraction including imaging encoder and CSF encoder (Section 3.3), multi-interaction (MI) module to manage the interactions between imaging and CSF, classification module (Section 3.4) and modality alignment (Section 3.5). Based on these fine-grained representations for images and CSF, the interaction module is designed for exploiting information across modalities. Specifically, modality alignment is introduced to align inconsistent feature distributions of imaging and CSF, which can further reduce the inter-modality gap at feature-level to improve diagnostic performance.

## 3.3. Features extraction

Since AD is believed to affect various brain regions, atrophy regions in MRI scans and metabolized regions in FDG scans vary in size. Traditional CNN can only capture the information of fixed receptive regions, and it is difficult to extract rich features due to pooling operations.

![](img/35eb289ac20da6b2112bd8090073aee2_3_1.png)

Fig. 3. Details of the CD module. Dilated convolution provides a solution to enlarge the receptive field without increasing the number of parameters and the size of convolution kernels. However, representing features without dilated convolution is crucial for AD diagnosis. Therefore, the cascaded CD module is designed to improve multi-scale representations. The use of three dilated convolutions with different sizes (256, 512, 1024), instance normalization (IN), followed by convolution layer of 3x3 and stride of 1, detect features such as the shape and contours without computational overhead.

### 3.3.1. Imaging encoder

Using an MRI-feat scan, the convolution is performed by pooling layer to produce a $B=4 \times 1024$ vector, which is $U = \{u_1, \dots, u_n\}$, where $u_i \in \mathbb{R}^{1024}$ is the representation for each image feature. Then $U$ is transformed into an $H$-dimensional vector $V$ (768) via linear projection, inspired by BERT [51] and Vision Transformer [52]. When $V$ is transformed to 768, the dense connection inside the multi-modal interaction module can be transformed as follows: where $I$ and $C$ denote the image and CSF representation, respectively. $W_Q^h$ and $W_K^h$ are the transformation matrices of head $h$, where $h$ is the $h$th head of multi-modal cross-attention. After computing $q, k,$ and $v$, they are used in multi-modal cross-attention, whose procedure can be described as follows:

$$CA(I,C) = \text{softmax}\left(\frac{(W_Q^h I)^T (W_K^h C)}{\sqrt{d_k}}\right)W_V^h C$$

$$MCA(I,C) = [CA(I,C), CA(C,I), CA(I,I)]$$

where $CA_h$ is the $h$th head of multi-modal cross-attention, $W_{CA}$ is the weight matrix for feature fusion.

$$V = W^h U + b^h,$$

where $W^h$ and $b^h$ are learned parameters. The images of MRI and PET-feat are concatenated to denote final image representation $I = \{i_k, \dots, i_n\}$, where $n=128$ is the number of slices in.

### 3.3.2. encoder

CSF measures consist of three types: A42, Tau, and P-tau. Since each CSF represents a different meaning, and each has different numbers, we need some kind of size normalization. By using positional encoding [59] and the encoder for attention, we consider using sinusoidal functions to achieve the coding of A42, Tau, and P-tau. The encoding process of each type of CSF is:

$$T(c_i) = \sin(i/10000^{2j/d})$$

$$T(c_i) = \cos(i/10000^{2j/d})$$

where $c$ represents the value from A42, Tau, and P-tau, $i=0, 1, \dots, d-1$ and $j=0, 1, \dots, d/2-1$ where $d$ is the dimension of the model.

The encodings are transformed by two fully connected layers to an $H$-dimensional vector ($h=768$). Through this operation, the scales and dimensions of encodings could be consistent with image representations. A sample, we encode each type of CSF as a vector, which is then concatenated to form the non-imaging features.

## 3.4. Multi-modal interaction

For AD diagnosis, multidata data can provide more information and potential relationships. Therefore, it is necessary to fuse image and CSF features to achieve diagnostic performance. By using a multi-modal interaction (MMI) mechanism [51] which can capture the cross-attention between image features and CSF features, the non-imaging features can be fused with imaging and non-imaging representation. The module focuses on the multi-modal interaction uses multi-head attention to fuse imaging feature and non-imaging feature. The structure in MMI can not only boost the interactions of multi-modal representations but also keep the valuable value of information among
