
![](img/146f9a713528a3fbc62fcad0f0d5a352_117_0.png)

Figure 7.1 Flowchart

## 7.2.2 Image Preprocessing

The most vital step in any image-based analysis is the preprocessing which performs operations on the image to enhance the image so that the images can be interpreted in the right way without any errors in the upcoming steps. The basic steps to be carried out in MR image processing are Filtration, Contrast Enhancement, and Skull Stripping [5].

- a) Median Filtering

Median filtering is a non-linear filtering technique which is used to remove noise from the input by smoothening the parts of the image except the edges. Median filtering mostly focuses on the preservation of edges. Each pixel in the image is compared with its neighboring pixels. The pixel is then replaced with the median of the surrounding pixels. The median filter removes salt and pepper noise with greater efficiency. Since MR images are prone to salt and pepper noise, the median filtering technique is used to eliminate unwanted noise parameters [6].

- b) Contrast Enhancement

Adaptive Histogram Equalization (AHE) is a process to enhance the contrast of the image. This method computes several histograms for different sections of the image and these are used to distribute the lightness value all over the image while the normal histogram technique used in the histogram is derived from the whole image to transform all the pixels in the image. The adaptive histogram equalization technique is widely used because it enhances the local contrast and edge definition in every section of the image [7]. The ordinary histogram equalization technique suitable for images does not have large variations in the pixel value throughout the image. Adaptive Histogram Equalization (AHE) can sometimes over-amplify the homogenous regions of the image since the regions are highly concentrated. To prevent this, a varied technique called Contrast Limited Adaptive Histogram Equalization (CLAHE) is used. The clipping of the histogram is done at a predefined value before the computation of the CDF in CLAHE, thereby limiting the slope of CDF and the transformation function. This predefined value where the clipping of histogram takes place is called the clip-limit and depends on the histogram normalization and the size of the neighbourhood region. Common values that limit the resulting amplification are between 3 and 4.

- c) Skull Stripping

Magnetic Resonance Imaging is a high resolution imaging technique which also contains non-brain tissues like skull, skin, fat, muscles, the neck, and eyeballs. These non-brain tissues are considered as obstacles in image processing and analysis procedures like automatic segmentation. Therefore, a preliminary process to isolate brain tissues from extra-cranial or non-brain tissues is always required before any quantitative morphometric studies of MRI brain images. This process is called Skull Stripping.

The Skull Stripping in this work is done by initially converting the image into a binary image with the help of a threshold and eliminating the connected pixels which are less than a particular number, producing a binary mask for the image. Then, this mask is used to isolate the central region of the MR image where the main image is present. After this process, the borders of the masked region are eroded by about 15 to 20 pixels to obtain a Skull Scrapped image. This helps us eliminate the non-brain region of the MR image in a simple way [8].

## 7.2.3 Segmentation

The process of dividing or partitioning a digital image into multiple divisions or segments is called Image Segmentation. This process is mainly used to separate the region of interest from the rest of the image and to locate the objects and boundaries in an image. Segmentation is a pre-eminent step in image analysis. One of the most successful methods in Image Segmentation is Otsu's Method. Otsu's Method is an automatic threshold selection method which works on the basis of region based segmentation [9].

Otsu's Method is a class variance method which has the ability to select the threshold automatically [10]. This method computes the probability of each intensity level, iterates along every possible threshold value, and creates an evaluation of the entire pixel layout in the image. The desired threshold corresponds to maximum intra-class variance. The main goal of Otsu's segmentation is to reduce the computation of the sum of foreground pixels and background pixels while selecting a fair threshold value which can perform efficient segmentation. Otsu's Method is known for its rare time consumption and is one of the most efficient methods for threshold selection.

Better threshold selection with respect to uniformity and shape measures for real time images is produced by Otsu segmentation. However, a profound search is required to derive the criteria for expansion of within-class variance [11]. This method gives us the total brain region neglecting the other unwanted regions present in the MR image.

## 7.2.4 Feature Extraction

The process of reducing the dimensions of the image is called Feature Extraction. This reduces a raw set of data into manageable groups for processing. Certain features, parameters, properties, and features are measured from the original set of data to distinguish one input pattern from another. The features extracted are given as classifier inputs [12].

An abnormal brain image will show certain differences in features when compared to a normal brain image. The changes in the features depend upon the type of brain pathology and their cognitive abilities and disabilities. These features are stored into a feature space. In the presence of a small dataset, few instances of abnormalities of a particular neurological disorder will be present in each image. Once the classifier detects an example of the abnormality present in a particular region of the human brain, it learns and produces a model to classify the images as abnormal tissues or corresponding disorder depending on the inputs given.

A crucial step in feature extraction is the selection of features. Good texture features and neighborhood aggregations of the neighborhood intensity data provide better results rather than including individual intensity values [13]. A number of techniques are used for the purpose of feature extraction from MR Images. Some of the common feature extraction techniques are Discrete Wavelet Transform (DWT), Gabor Filters, and a Gray Level Co-Occurrence Matrix. The Gray Level Co-Occurrence Matrix technique is used for this work. The Gray Level Co-Occurrence Matrix (GLCM) outperforms other techniques in terms of the dimension of the feature vectors, thus this technique is considered more appropriate for MRI image classification [14]. GLCM is a statistical technique that extracts texture features from the image. Normal tissues are much different in texture when compared to the abnormal tissues. The texture features which are extracted from GLCM are contrast, correlation, energy, and homogeneity.

Selection of a good set of features also improves efficiency of classification. Additional features were also extracted from this matrix, namely mean, standard deviation, entropy, root mean square, variance, kurtosis, and slowness. In addition to this, the total brain area is estimated and used for classification. When more than two features are used for classification process, it is very difficult to visualize the performance of the classifier. Thus, the features are reduced into two variables that prominently describe all the features derived. This is another process of dimensionality reduction and the Principal Component Analysis technique is used to achieve this. This technique increases interpretability and minimizes information loss at the same time. Thus, visualization can be done with these two prominent variables which are obtained by PCA as a two-dimensional graph [15].

## 7.2.5 Classification

The process of categorizing the given input by a proper classifier is called classification. The objective of classification is to group items that have similar features into sections. We have a number of classifiers or algorithms to choose from which differ in the way they evaluate the right class for a particular test data. One has to consider the requirements and the type of dataset to choose a suitable algorithm from different classifiers. The k-Nearest Neighbour classifier is a simple, non-parametric algorithm which assigns classes to the test data by considering its Euclidean distance with other points [16].

This algorithm works well if there is a small number of features and the performance of this algorithm is worse in situations where there are many features and only a few are informative.

Naïve Bayes classifiers are a family of classifiers containing algorithms based on Bayes’ Theorem in which every pair of features that are being classified are considered to be independent of each other [17]. The extension of Naïve Bayes is the Gaussian Naïve Bayes classifier wherein a Gaussian function is used to estimate the distribution of data. A Gaussian function (or Normal distribution) is the easiest to work with because the estimation of just two parameters, mean and standard deviation from the training data, will help in decision making. In a Syntactic Ambiguity Study, GNB and
