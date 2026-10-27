
## 9.6 Image Transforms

The five transform techniques that have been proposed for feature extraction are discrete cosine transform (DCT), Walsh transform, Kekre transform, discrete sine transform (DST) and discrete Hartley transform (DHT). A comparison of classification performance for these techniques shows that feature extraction with partial DCT coefficients has outclassed Walsh transform, Kekre transform, DST, and DHT. The supremacy of the proposed technique has also been established over the existing techniques for classification performance.

The purpose of any image transform is to relocate the high frequency components toward the upper end of the image and the low frequency components toward the lower end of the image. Transformation drastically reduces the size of feature vectors by excluding insignificant coefficients. Energy compaction of transforms can pack a large fraction of the average energy into a few components. This has led to faster execution and efficient algorithm design for content-based image classification.

The extracted feature vectors from each component in transform coefficients are stored as a complete set of feature vectors. In addition, partial coefficients from the entire feature vector set are extracted to form the feature vector database. Feature vector databases with partial coefficients are constructed, starting with 50% of the complete set of feature vectors to 0.06% of the complete set of feature vectors.

## 9.7 Morphological Operations

Feature extractions with two different morphological operators, called top-hat and bottom-hat morphological operators, are compared for classification performance evaluation.

Shape is considered a vital feature for identification of object-based information. Shape features play a vital role in image recognition by identifying the structure of the object of interest with the help of structuring elements. Morphology-based operation is implemented for feature extraction from images using top-hat and bottom-hat operators. Basic morphological operations are performed by dilation and erosion functions. Initially, the image is processed with swelling by applying pixels to the object boundaries with dilation; the image is shrunk with erosion by removing the boundary pixels. The corresponding pixel in the input image is compared with the neighboring pixels to define the value of each pixel in the output image.

The contour region and background portion of individual color components of the image are grouped into two different clusters. The mean and standard deviation for the two clusters are derived by computing the feature vectors of the images.

A comparison of feature extraction using top-hat and bottom-hat morphological operators has clearly revealed that feature extraction with bottom-hat transform has better Precision, Recall and F1-Score values and a lower MR. A comparison with state-of-the-art techniques has yielded the same results.

## 9.8 Texture Analysis

Two techniques of feature extraction using texture analysis, called feature extraction by vector quantization codebook representation using Linde-Buzo-Grey (LBG) algorithm and feature extraction by gray level co-occurrence matrix (GLCM), have been compared for classification performance.

In some images, the defining characteristics of regions can be important for proper analysis. Feature extraction can be done from the spatial arrangements of color or intensities with the help of texture analysis. Some histogram distributions can have different texture representation, which can act as a tool for extraction of distinct features. Vector quantization (VQ) is used to generate codebook as feature vectors from the images. A *k* dimensional Euclidean space is mapped by means of vector quantization into a finite subset. The codebook is represented by the finite set CB.

Spatial definition of visual pattern of images has been characterized by the texture features. Specific texture detection in an image is performed by representing the texture as a two-dimensional gray level variation known as the gray level co-occurrence matrix (GLCM). GLCM is a statistical method for investigating textures that considers the spatial relationship of pixels. The texture of an image is portrayed by the GLCM function by computing the frequency of existence of pixel pairs with specific values and specific pixel relationships in an image followed by extraction of statistical measures from the matrix.

The comparisons based on Precision, Recall, MR and F1-Score have established that feature extraction with VQ using LBG is superior to the GLCM method of feature extraction for content-based image classification and to the state-of-the-art techniques.

## 9.9 Multitechnique Feature Extraction for Decision Fusion-Based Classification

The competence of the content-based image identification technique depends on the extraction of robust feature vectors. Diverse low-level features such as color, shape, texture, etc. constitute the process of feature extraction. However, an image comprised of a number of features can hardly be defined by a single feature extraction technique. Therefore, two different fusion-based classifications are carried out and compared with one another. The first technique has carried out late fusion by separately evaluating classification decision of two different feature vectors, namely, binarization features extracted with Sauvola’s local threshold selection and transform domain features extracted with partial coefficients of Discrete Cosine Transform (DCT). The second fusion based technique is early fusion of the above mentioned feature vectors. The binarization feature and transform domain feature are normalized separately using z score normalization followed by horizontal concatenation of the two. The combined feature vector with larger details of image data is now provided as an input to the classifier for better performance.

The two results for classification with fusion techniques are compared, and the results indicate that classification with decision fusion of four feature extraction techniques surpasses classification with decision fusion of three different feature extraction techniques.

Furthermore, the superior technique is used as a precursor for retrieval, and the query image is classified by the proposed fusion-based approach. The retrieval results are compared to the state-of-the-art techniques of fusion-based retrieval, and the proposed method outperforms the existing fusion-based techniques.

## 9.10 Comparison of Cross Domain Feature Extraction Techniques

The feature extraction techniques from binarization, image transform, morphological and texture analysis are compared for classification performance. The best technique selected in each domain is used for comparison in Fig. 9.3.

The comparison in Fig. 9.3 clearly reveals that classification with feature extraction by VQ using LBG has the best Precision, Recall, F1-Score and MR compared to the rest of the proposed feature extraction techniques in other domains.

## 9.11 Future Work

The book extensively covers content-based feature extraction techniques in assorted domains for image classification. The classification results divulge statistical significance of improved performances over state-of-the-art

![](img/2bc397c57b3b49c1ff177a21ce3b8fc5_185_0.png)

**FIGURE 9.3**  
Comparison of Classification with Cross Domain Feature Extraction Techniques.  
**[Observation:** Classification by feature extraction with VQ using LBG has the best performance.**]

techniques. Henceforth, these techniques can be evaluated for image datasets in diverse domain including medical imaging, satellite imagery, plant disease detection, and so on. The fusion methodologies may also be implemented for combining representation learning features to handcrafted descriptors to assess the classification performances of the hybrid feature definition.

The book provides a novel perspective to computer vision aspirants while they handle image data for classification. Moreover, the fusion-based propositions may surpass the accuracy of neural networks when used to combine traditional features with representation learning-based features.

## References

- 1. Sainath, T. N., Mohamed, A. R., Kingsbury, B. and Ramabhadran, B., 2013, May. Deep convolutional neural networks for LVCSR. In 2013 IEEE International Conference on Acoustics, Speech and Signal Processing, pp. 8614–8618.
- 2. Zhang, Y. D., Dong, Z., Chen, X., Jia, W., Du, S., Muhammad, K. and Wang, S.H., 2019. Image based fruit category classification by 13-layer deep convolutional neural network and data augmentation. *Multimedia Tools and Applications*, 78(3): 3613–3632.
