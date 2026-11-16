
## Taylor & Francis
Taylor & Francis Group
http://taylorandfrancis.com

![](img/28baab106dba0e70a2f26ab75f61f184_191_0.png)

## 13 Super-resolution in a world of scarce resources for medical imaging applications

A. Deshpande, V. V. Estrela, P. Patavardhan, G. Kallimani

## CONTENTS

- 13.1 Introduction .................................................... 183
- 13.2 Super-resolution convolutional neural network (SRCNN) architectures ..... 186
- 13.2.1 SRCNN ........................................................ 186
- 13.2.2 Fast SRCNN (FSRCNN) .................................... 187
- 13.2.3 Very deep SR convolutional networks (VDSR)............. 187
- 13.2.4 Deeply recursive convolutional networks (DRCN) .......... 187
- 13.3 DL-based SR methods ........................................ 187
- 13.4 Discussion and future work ............................... 191
- 13.5 Conclusion ................................................. 194
- References......................................................... 194

### 13.1 INTRODUCTION

Medical imaging (MI) engenders more intelligent, diversified, and useful representations of the human body’s internal organs for clinical investigation and effective medical intervention. MI makes internal structures visible and reveals problems buried by the layers of bones and skin, helping in diagnosis and treatment. The influential non-invasive MI characteristics from Computed Tomography (CT) and Magnetic Resonance (MR) Imaging achieve accurate, compelling health scrutiny and interpretation (Ogawa & Lee 1990). Body parts, like tissues, bones, heart, brain, muscles, and tumors, can be observed. However, low spatial resolution is an unrelenting problem (Onesimu & Karthikeyan 2020; Ayubi et al. 2015; Andrew 2020), affecting the diagnosis process and post-processing. Image acquisition time and equipment are the limited MI spatial resolution constraints. High-quality images are often challenging due to long sampling times, patient discomfort, stronger magnetic field, and higher expenses. Thus, to address these associated problems without affecting the hardware and scanning process, super-resolution (SR) assures promising outputs. SR methods aim to increase the images' spatial resolution and improve MI quality without an additional scanning process via low-resolution (LR) image(s) to construct a high-resolution (HR) image. Acquisition process losses can be recovered from the SR process' high-frequency (HF) content. The main SR algorithm goal is to reconstruct HR images from the observations of under-sampled LR images. SR through Deep Learning (DL) can help fight many maladies, e.g., the coronavirus disease (COVID-19). This SR via DL review can help identify superior artificial intelligence (AI)-based tools (Monda 2021). Literature searches for keywords like AI, COVID-19, machine learning (ML), CT, MRI, forecasting, DL, and X-rays are all related to detailed imaging. To improve the scrutiny of patients, mining could merge SR with semiotics/semantics to better describe findings and to speed up studies since HR demands network resources and storage. Working with various MI datasets improves and delivers different diagnosis stages, viz., subdivision, pre-processing, and feature extraction. Densely connected convolutional neural networks (CNNs) provide admirable abilities to improve the accuracy and resolution of images (Vyas & Bhargava 2021).

The 2D imaging model is shown by:

```
g_k (m, n) = d(h_k (w_k ( f(x, y))) + \eta _ { k } (m, n) \quad (\text{Eqn. 13.1})
```

where _k_ corresponds to the number of LR images. The function _g_() for _k_=1 is given by

```
g(m,n) = \frac{1}{q^2} \sum_{x=qm}^{(q+1)m-1} \sum_{y=qn}^{(q+1)n-1} f(x,y). \quad (\text{Eqn. 13.2})
```

_g_ is an acquired LR image, _d_ is a down-sampling parameter, the warping function is _w_, _h_ is a blurring function, and \(\eta\) is additive noise. _f_ represents the fundamental HR image; _q_ is a sub-sampling parameter or decimation factor equal in both horizontal and vertical directions. _x_ and _y_ are the HR image coordinates and _m_ and _n_ of the LR images, the size of which is \(L_1 \times L_2\), and the HR image has the size \(H_1 \times H_2\), where \(H_1 = qL_1\) and \(H_2 = qL_2\). The MI model in Ogawa (1990) states that an LR-observed image has been attained by averaging over a _q_<sup>2</sup>-pixel area. Other MI process parameters can be considered, i.e., blurring, warping (geometric transformation), and noise. Let _g, f,_ and \(\eta\) represent _k_-dimensional vectors. All the warping factors belong to matrix _A_. A more realistic vector-form model becomes _g_ = _A f_ + \(\eta\). High-quality SR images mitigate noisy, blurred images, artifacts, and degraded effects i) with fewer costs, ii) without fancy hardware, repurposing existing LR imaging systems, and iii) with high flexibility. SR has various applications (Deshpande et al. 2020; Deshpande et al. 2021) in realms viz. bio-metrics, MI analysis, unmanned aerial vehicles (UAVs), and many more. Table 13.1 classifies SR's threefold major strategies.

The previous three-class classification works for still images and videos. Single-image SR (SISR) processes rely heavily on learning algorithms to infer the missing data, resulting in super-resolved pictures utilising the connection between LR

TABLE 13.1 Classification of SR methods

| Methods | Algorithms | Gains | Disadvantages |
|:---|:---|:---|:---|
| 1 Interpolation-based (Frank 1982; Markov 2008) | a. Nearest-neighbor interpolation<br>b. Bi-cubic interpolation<br>c. Bilinear interpolation | Simple and easy to achieve fast computation | Perform well in low-frequency areas but poorly in edge (HF) areas prone to blurring and jaggy artifacts along edges. |
| 2 Reconstruction-based (Bertero 1998; Liu 2017) | a. Maximum a posteriori<br>b. Markov random field<br>c. Kernel steering | Image overlay, change detection | Small discontinuity and pixel losses near the edges. |
| 3 Example-based (Qu et al. 2013; Li 2016) | d. Total Variation (TV)<br>e. Markov random field<br>f. Sparse coding<br>g. Gaussian process regression<br>h. Gaussian process regression | High magnification factor | Require a huge image database.<br>Increased execution time due to searching test image patches from databases |

and HR images from a training database. Multiple-image SR (MISR) algorithms typically assume a targeted HR image, and the LR observations include equivalent geometric or photometric shifts from the intended HR image. In general, these algorithms use the differences between the LR observations to rebuild the desired HR picture, i.e., they are reconstruction-based SR algorithms. Reconstruction-based SR algorithms consider the SR issue to be inverted. Consequently, as with other inverse situations, a forward-imaging model is required.

The latest performance achieved with deep-learning (DL) algorithms has facilitated super-resolving LR images. The primary DL aim is to learn an often-superior representation of data hierarchy compared to other machine-learning (ML) algorithms. A few existing SR frameworks constructed via convolutional neural networks (CNNs) appear in Section 13.2. DL-based SR procedures emerge in Section 13.3, whereas Sections 13.4 and 13.5 cover the discussion and conclusion of the chapter, respectively.

### 13.2 SUPER-RESOLUTION CONVOLUTIONAL NEURAL NETWORK (SRCNN) ARCHITECTURES

A convolutional neural network (CNN) is a type of artificial neural network used in image recognition and processing that is specifically designed to process pixel data.

### 13.2.1 SRCNN

The first DL SISR method is the SRCNN. Thus, LR and HR images are directly learned in end-to-end mapping.

The layout of the network structure is presented in Figure 13.1. The network carries three layers, where each layer contains a layer of convolution by adding

![](img/28baab106dba0e70a2f26ab75f61f184_195_0.png)

FIGURE 13.1 Network structure layout of SRCNN (medium.com 2022).
