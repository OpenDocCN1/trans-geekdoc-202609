
98.7% for Cleveland, 99.0% for Hungarian, and 99.4% for Cleveland-Hungarian (CH) datasets.

Thanga Selvi and Muthulakshmi (2020) developed a heart disease classification system, using optimal artificial neural network (OANN). The OANN consist of two major processes, namely distance-based misclassified instance removal (DBMIR) and teaching and learning-based optimisation (TLBO) algorithms for artificial neural network (ANN), called TLBO-ANN. This system was designed based on a big data framework like Apache Spark. Moreover, this system works on two phases, namely offline prediction and online prediction. For offline prediction, they utilised a benchmark dataset, whereas, for online prediction, they utilised a real-time dataset. The performance of the presented OANN model has been tested using a benchmark heart disease dataset from the UCI Repository.

Oliver et al. (2021) developed an accurate system for prediction of heart disease based on a biosystem, using a regressive learning-based neural network classifier (RLNNC). The RLNNC system was a fully automated algorithm. The results of this system were accurate for patients with heart disease and the drug benefits of detecting and analysing heart disease. Analysis has shown that the RLNNC-based techniques promote greater efficiency and higher accuracy than traditional methods.

Similarly, Jiao et al. (2020) developed a one-dimensional CNN-based pulse recognition system for detecting patients with cardiovascular disease. Initially, the original data are divided and normalised. The divided dataset is then assigned for training and testing process. Then, the pulse signal is inputted to CNN, which automatically extracts the features (Vyas et al. 2022), which are characterised by a fully attached layer. The final classification accuracy ratio can reach 97.14%, which is better than traditional machine-learning classification methods, such as SVM and KNN, providing new ideas and methods for the classification and objectification of pulse signals.

Alkhodari and Fraiwan (2021) developed a valve heart disease prediction system, using convolutional and recurrent neural networks (RNN) in phonocardiogram recordings. Initially, the signal is pre-processed, using the maximal overlap discrete wavelet transform (MODWT) smoothing algorithm. Then, the signal is transferred to the combination of CNN and RNN, based on bi-directional long short-term memory (BiLSTM). The model is trained and tested following the k-fold cross-validation scheme of 10-folds, using the CNN-BiLSTM network as well as the CNN and BiLSTM networks individually. The highest performance was achieved using the CNN-BiLSTM network with an overall Cohen’s kappa, accuracy, sensitivity, and specificity measures of 97.87%, 99.32%, 98.30%, and 99.58%, respectively.

Dutta et al. (2020) developed a CNN-based coronary heart disease prediction system. Here, the forecast variables are determined using a less complete abstract and select operator (LASO)-based filtering system. Subsample methods are implemented to calculate high-class inequalities. The classifier achieves higher class-wise accuracies than traditional models. The introduced framework was used as a transfer learning model for new data. This method attained a maximum accuracy of 79.5%.

## 12.3 PROPOSED CARDIAC IMAGE-BASED AUTOMATIC HEART DISEASE DIAGNOSIS MODEL

Cardiac imaging plays an important role in diagnosing heart disease. The unavailability or shortage of radiologists and physicians in various countries, for a number of reasons, is a significant factor in barriers to early diagnosis of this high-mortality disease. Among the various efforts to develop end-support systems, computational intelligence is a growing trend in the field of clinical imaging for prognosis and diagnosis. This helps radiologists and clinicians to get relief from the heavy burden and reduce the delays in achieving timely diagnoses of patients. Therefore, in this study, automatic heart disease prognosis was proposed using a deep neural network. The proposed approach consists of four stages, namely pre-processing, feature extraction, feature selection, and classification. The cardiac image-based automatic heart disease diagnosis model is described in Figure 12.1.

### 12.3.1 Pre-processing

Consider the cardiac image Iij, which includes some noise. To remove the noise present in the input image, a median filter is applied. The median filter is typically used to lessen noise in an image. It is a non-linear filter that computes median of the pixel set that falls within the filter mask. Each pixel is addressed, and it is replaced by means of statistical median of its m×n neighborhood. Since the median value is computed from the neighboring pixel, it is more robust to outliers and does not create a new realistic pixel value, which would preserve edge

![](img/28baab106dba0e70a2f26ab75f61f184_172_0.png)

FIGURE 12.1 Proposed cardiac image-based automatic heart disease diagnosis model.

![](img/28baab106dba0e70a2f26ab75f61f184_173_0.png)

FIGURE 12.2 Graphical representation median filter.

TABLE 12.1
Steps to be followed in median filter

- Place a window over pixels.
- Sort the pixels value ascending or descending.
- Compute the median.
- The median value will be the new value of the center pixel of the window.
- Repeat the above process for all corrupting image area.

blurring and loss of image detail. It preserves the sharp high-frequency details. It is well suited to eliminate salt-and-pepper noise from the image. A graphical presentation of the median filter operation is depicted in Figure 12.2. The steps for applying the median filter algorithm are as follows (Table 12.1).

This filter works by analysing the neighborhood of pixels around an origin pixel, as shown in Figure 12.2, for every valid pixel in an image. For this case, a 3 x 3 window of pixels is used to calculate the output. For every pixel in the image, the window of neighboring pixels is found. As shown in Figure 12.2, the pixel values in the window are sorted in ascending order and the median value is chosen; in this case the median value is 50. Next, the pixel in the output image corresponding to the origin pixel in the input image is replaced with the value specified by the filter order. The value in the origin, which is 70, is replaced by 50.

The effect of median filter in removing noise increases as the window size increase. The median filter is mathematically depicted as follows:

```
\(\hat{Z}(i, j) = \text{median}_{(s,t) \in S_{ij}} \{g(s,t)\}\) (12.1)
```

where
Z(i, j) = median filter at a given coordinate, and
Sij = coordinate of sub-image window of size m x n

### 12.3.2 FEATURE EXTRACTION

After pre-processing, the texture features are extracted from each image. In this chapter, the gray-level co-occurrence matrix (GLCM) is used to extract the texture features. The GLCM gives a joint distribution of gray-level pairs of neighboring pixels within an image (Rajakumar & George 2013). For the computation of GLCM, first, a spatial relationship is established between two pixels, one being the reference pixel, and other a neighbor pixel.

Let _M(u, v)_ be the element of GLCM of a given image _A_ of size \(a \times b\), containing the number of gray levels _G<sup>L</sup>_ ranging from 0 to _G<sup>L</sup>_-1. Then, _M_ cab is defined as the matrix element and given by:

```
\( M(u, v) = \sum_{i=1}^u \sum_{j=1}^v \begin{cases} 1 & \text{if } A(a,b)=u \text{ and } I^{in} \left( a + \Delta a, b + \Delta b \right) = v \\ 0 & \text{otherwise} \end{cases} \text{ (12.2) }\)
```

where, (_a_, _b_) and (_a_+Δ _a_, _b_+Δ _b_) are the locations of the reference pixel and its neighboring pixel, respectively. Each element of GLCM, _M_\(\big(\)_u_, _v_\(\big|\) Δ_a_, Δ_b_\(\big)\), represent the relative frequency of two pixels in a given neighborhood separated by a distance (Δ _a_, Δ _b_) and having gray-level values _x_ and _y_, respectively (Esteva et al. 2019). It can be represented as _q_\(\big(\)_u_, _v_\(\big|\)_D<sup>p</sup>_, θ\(\big)\), where the parameter _D<sup>p</sup>_ is the distance of separation between two neighborhood resolution cells, with two pixels having intensities _u_ and _v_ in the image. The other parameter θ represents the direction of the neighboring pixel with respect to the reference pixel. The parameter _D<sup>p</sup>_ is also called the set distance as it specifies the distance of all neighboring resolution pairs contained in a set. For the texture calculation, the GLCM must be symmetrical and each entry of the GLCM should be a probability value. In this paper, twenty two GLCM features are extracted from each image, namely angular second moment, contrast, inverse difference moment, entropy, correlation, variance, sum average, sum variance, sum entropy, difference entropy, inertia, cluster shade, cluster prominence, dissimilarity, homogeneity, energy, autocorrelation, maximum probability, inverse difference normalised, inverse difference moment normalised, information measure of correlation I, and information measure of correlation II.

### 12.3.3 FEATURE SELECTION USING THE LPSO ALGORITHM

After the feature extraction process, the important features are selected using the LPSO algorithm. The feature selection process is to limit the number of input features to achieve optimum accuracy and also reduce computation complexity. For feature selection, in this chapter, the LPSO algorithm is used. The LPSO is a combination of the lion optimization and PSO algorithms.

_Step 1: Initialisation._ Initialization is an important process for all optimization algorithms. For feature selection, initially the solutions are randomly selected. In
