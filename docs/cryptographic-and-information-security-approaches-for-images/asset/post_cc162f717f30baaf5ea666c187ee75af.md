
The work [12] introduces a concept called SIFT-Symmetry, that combines the SIFT with symmetry-based matching for image tampering detection in case of reflection attacks.

An improved keypoint based approach is proposed in [13] by trying to improve the discerning power of keypoints having low contrast, reduce the computational complexity of clustering process and the non-uniform distribution of the keypoints. Initially, to acquire uniformly distributed keypoints, keypoint selection is done with respect to region instead of contrast. To achieve this, detection of keypoints and processes of selection are separately performed. The combination of contrast and density of each keypoint is employed to choose the keypoints by non-maximum value suppression. Later, the opponent SIFT descriptor is used to improve the discerning power of keypoints by the addition of color related information. Finally, clustering overhead is reduced by an optimized J-Linkage algorithm. This optimization is achieved by altering the initial cluster computation and affine transformation hypotheses.

## 24.2.2.1.2 SURF Keypoint Based Approaches

The SURF (Speeded Up Robust Features) [4] consists of a keypoint detector and descriptor. In [14], the keypoints are generated using Fast-Hessian Detector which is based on the Hessian matrix for a particular image pixel. The keypoint descriptor is formed from the wavelet responses in a particular neighborhood of the keypoint and Haar wavelet responses are used for orientation assignment.

The work in [15] extracts interest points, finding possible correspondences between them. Based on geometric constraints, they are clustered into regions with respect to correspondent points. This is followed by a multi-scale representation of the image. The groups generated over various scales are analyzed using a descriptor. This is done to decrease the search space of duplicated regions and leads to the construction of a detection map. The final verdict is made depending on a voting procedure among these detection maps.

## 24.2.2.1.3 Keypoint Based Approaches: Miscellaneous

A hybrid method is presented [16] in which the comparison is based on triangles. Given an input image, the interest points are generated, followed by modeling the objects as a set of connected triangles. The triangles are then matched with respect to inner angles, color representations, and local feature vectors extracted from the vertices. The images used in their work are presented in Figure 24.6.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_754_0.png)

Figure 24.6 Copy-moved images with various rotation and scaling operations from [1] dataset. (1) pristine image. Images (2) to (4) are subjected to copy-move attacks rotations 0° (simple translation), 30° and 210°. Images (8) to (10) are images with copy-move attacks with scale factors 0.5, 1.25 and 1.75. Images from (5) to (7) and (11) to (13) are the expected results of the corresponding images above them.

Yet another hybrid keypoint based work is discussed in [17] which uses an interest point detector called KAZE in combination with SIFT for extracting more feature points. Multiple region duplication is achieved by an improved matching algorithm that use the n-best matched features. False matches are reduced by segmentation. An iteration strategy is employed for the estimation of transformation matrices and determining if forgery is present or not.

In [18] the authors have used image signature tools which were used in MPEG-7. These tools, which were originally used for content-based image retrieval, are modified to be used to detect copy-move forgeries.

The work in [19] uses a combination of SIFT keypoints and Zernike moments. SIFT keypoints are generated on the entire input image and Zernike moments supplement the areas where the SIFT keypoints are missed.

A mixed moment approach is used in [20] to improve the robustness of copy-move forgery detection. They used exponential-Fourier moments and histogram moments, which they called mixed moments. They claim to improve robustness towards translations, rotations, scalings and mixing of these operations. It is claimed to work on post processing like brightness and contrast adjustments.

A combination of Dyadic Wavelet Transform (DyWT) and SIFT are used in [21]. DyWT is applied on an input image to decompose it into four parts LL, LH, HL, and HH. SIFT is applied on the LL image, which carries more information regarding the input image. This procedure ensures obtaining more keypoint extraction, which is required for matching to identify the copy-moved regions.

A texture based copy-move detection is proposed in [22]. The proposed method is a block-based approach. The input image is divided into overlapping blocks and feature vectors for each block are extracted using texture descriptors called LBP operators. The rest of the matching of the descriptors is carried out on similar lines with the general copy-move forgery pipeline discussed earlier.

A summarization of keypoint based methods are provided in Table 24.1.

## 24.2.2.2 Block Based Approaches

Localization and detection of copy-rotate-move (CRM) manipulations using Zernike moments is discussed in [28] over small overlapping image blocks. A block matching scenario depending on locality sensitive hashing is employed and it exploits the phase differences of Zernike moments in a feature-based error reduction approach.

The authors in [29] divide an input image into fixed-size overlapping blocks and apply 2D-DCT on each of these blocks followed by quantization. Each of these quantized blocks are then further divided into nonoverlapping sub-blocks for applying singular value decomposition (SVD) on each of them. Copy-move forged areas are found out by matching. The results reveal that they are able to detect multiple copy-moves and accurate localization of these areas. They claim that it is robust towards postprocessing operations like Gaussian blur, JPEG compression and combined operations.

In [30], an input image is split into sub blocks and mapped to log-polar coordinates. These are then represented with a dimensionality reduced feature vector. Similar regions are searched by comparing the feature vectors.

## Table 24.1 Keypoint Based Works Used for Copy-Move Forgery Detection

| Sl | Authors | Keypoint |
|---|---|---|
| 1 | Amerini et al. [8] | SIFT [23] |
| 2 | Li et al. [11] | SIFT |
| 3 | Ardizzone et al. [1] | SIFT, SURF [4] and Harris [24] |
| 4 | Cozzolino et al. [12] | PatchMatch [25] |
| 5 | Wenchang et al. [13] | SIFT |
| 6 | Kee et al. [26] | KAZE [27], SIFT |
| 7 | Warif et al. [14] | SIFT |
| 8 | Jin and Wan [15] | SIFT |
| 9 | Silva et al. [15] | SURF [4] |
| 10 | Manu and Mehtre [10] | SIFT |
| 11 | Bo et al. [14] | SURF |

In [31], the input image is split into blocks of fixed sizes. Discrete cosine transform (DCT) coefficients are computed on each of them to represent the corresponding block. It is then represented as circular blocks. Four features are extracted from these blocks in order to perform dimensionality reduction of each block. Lexicographic sorting and subsequent matching is done based on a threshold for finding the copy-moved regions.

### 24.2.2.2.1 Hybrid Methods

In this section, the combination of block and keypoint based approaches are discussed, which we call hybrid methods.

The work [32], uses the adaptive detection of keypoints which are supposed to cover the complete image based on a uniqueness metric. A filtering algorithm effectively prunes the wrongly matched regions. The entire procedure is repeated along with adjusting the keypoints density depending on the information achieved.

The work [33] combines various properties of copy-move detection techniques and model the scenario on a multiscale behavior knowledge space. This encodes the output combinations of these techniques as a priori probability considering multiple scales of the training data. The conditional probabilities of missing entries are accurately estimated using generative models. Finally various techniques are proposed that exploit the multi-directionality to generate a detection map using a machine learning based decision-making method.
