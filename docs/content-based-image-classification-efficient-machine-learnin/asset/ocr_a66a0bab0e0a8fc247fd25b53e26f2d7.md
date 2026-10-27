**TABLE 5.2**  
**Comparison of Computational Complexity of Applied Transforms**

| Transforms | Number of Additions For *N* × *N* image | Number of Multiplications | Total Additions for Transform of 256 × 256 Image Dimension | Total Computations Comparison (For 256 × 256 Image Dimension) |
|---|---:|---:|---:|---:|
| DCT | 2*N*²(*N* − 1) | *N*²(2*N*) | 301858816 | 100 |
| Walsh | 2*N*²(*N* − 1) | 0 | 33423360 | 11.07 |
| Kekre | *N*[*N*(*N* + 1) − 2] | 2*N*(*N* − 2) | 17882624 | 5.92 |
| DST | 2*N*²(*N* − 1) | *N*²(2*N*) | 301858816 | 100 |
| Hartley | 2*N*²(*N* − 1) | *N*²(2*N*) | 301858816 | 100 |

> **[Observation:** Here one multiplication has been considered as eight additions for the second-last row computations, and DCT computations have been considered to be 100% for comparison in the last row.**]

# 5.6 Feature Extraction with Partial Energy Coefficient

Five different image transforms—namely, DCT, Walsh transform, Kekre transform, DST and Hartley transform—have been applied on the test images to extract features with partial energy coefficient for content-based image classification. The classification results are evaluated by a 10-fold cross-validation scheme. Each of the techniques has been described in the following subsections and the classification results with various percentages of partial energy have been compared with four different metrics—namely, Precision, Recall, Misclassification Rate (MR) and F1-Score. Four different classifiers—namely, K Nearest Neighbor (KNN), Ripple-Down Rule (RIDOR), Artificial Neural Network (ANN) and Support Vector Machine (SVM)—are used for appraising the classification of four widely used public datasets, namely, Wang dataset (1000 images and 10 categories), Oliva Torralba (OT-Scene) dataset (2688 images and 8 categories), Corel dataset (10,800 images and 80 categories) and Caltech dataset (8127 images and 100 categories). defined The classifiers and the datasets have been described in Chapter 1. Initially, feature extraction with all the percentages of partial coefficients of all the considered transforms are assessed for MR and F1-Score values of classification. Test images from the Wang dataset are utilized for this purpose and the similarity measure of images is carried out with Mean Squared Error (MSE) distance measure.

# 5.6.1 Discrete Cosine Transform

Discrete cosine transform (DCT) has a close link to the discrete Fourier transform (DFT) and has been defined as a separable linear transformation