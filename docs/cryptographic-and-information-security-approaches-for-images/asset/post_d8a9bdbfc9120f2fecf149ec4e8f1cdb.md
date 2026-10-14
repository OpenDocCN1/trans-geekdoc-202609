
derived with respect to x and set equal to zero as a result, is obtained according to Equation 26.5.

$$\hat{X} = -\left(\frac{\delta^2 D}{\delta X^2}\right)^{-1} \frac{\delta D}{\delta X}\tag{26.5}$$

Then, the value of the offset $\hat{X}$ is examined. If it is larger than 0.5, the position of the candidate keypoint varies and interpolation is done for this point. Otherwise, the offset is added to the candidate keypoint and the size of the function is expressed in this extremum position using Equation 26.6.

$$D(\hat{X}) = D + \frac{1}{2} \frac{\partial^2 D}{\partial X^2} \hat{X}\tag{26.6}$$

Thus, the location of the feature in the sub-pixel size is calculated and its exact scale is estimated. The absolute value of the function in the extremum position $|D(\hat{X})|$ is considered as the contrast of each feature and used for the removal of unstable features. In accordance with the proposal of Lowe, features whose contrast value is less than a pre-defined threshold value ($T_c = 0.03$) are unstable and sensitive to noise and thus must be removed. At this stage, after removing these low-contrast features, it is needed to remove the features that are on the edge, as they are sensitive to noise and small changes in their neighbourhood (Lowe 2004). For this purpose, the ratio between the eigenvalues of the Hessian matrix is used to detect and remove the points on the edge. The Hessian matrix is the matrix of second order partial derivatives in respect to $x$ and $y$, estimated according to Equation 26.7.

$$H = \begin{bmatrix} D_{xx} & D_{xy} \\ D_{yx} & D_{yy} \end{bmatrix}\tag{26.7}$$

In this equation, $D_{xx}$ is the second derivative of the candidate point with respect to $x$ on the DOG images, $D_{xy}$ and $D_{yx}$ are the second derivative of the candidate points with respect to $x$, $y$ on the DOG image, and $D_{yy}$ is the second derivative of the candidate points with respect to $y$ on the DOG image. It is assumed that $\alpha$ is the larger and $\beta$ is the smaller magnitude eigenvalue of the Hessian matrix. Therefore, the ratio of these Eigenvalues can be obtained according to Equation 26.8.

$$r = \frac{\alpha}{\beta}\tag{26.8}$$

Based on Lowe’s basic SIFT algorithm, the points for which $r$ is greater than 10 should be deleted.

## 26.6.3 Assignment of Orientation for Each Feature

At this stage, an orientation parameter is determined for each of the extracted features from the previous. The process of allocation of orientation starts by selecting a circular window around each feature in the corresponding Gaussian image. Afterwards, size values and direction of the gradient are calculated for the pixels within the area, and, ultimately, a histogram is created as the histogram of orientation. Moreover, the directions related to the maximum of the histogram column and the directions that are 80% maximum are considered as the direction related to the extracted features.

## 26.6.4 Removal of Unnecessary Keypoints

In this part, removal of the redundant keypoints method is explained consisting of three different steps according to Figure 26.9. After identifying the SIFT keypoints in each image, the distance of the keypoints from each other is initially calculated. Then, when the distances between two different keypoints are less than a certain threshold value, the redundant keypoint is removed based on the redundancy index (RI), and the other one is maintained in the image keypoints.

First, Manhattan distance is calculated between each keypoint and all other keypoints in each image, according to Equation 26.9.

d₁(pₘ, pₙ) = Σᵢ₌₁ˡ |pₘ(i) − pₙ(i)|  (26.9)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_812_0.png)

Figure 26.9 Flowchart of RKEM-SIFT.

In this equation, $p_m(i)$ and $p_n(i)$ are the $i$th coordinate of keypoint $p_m$ and $p_n$ respectively, and $l$ is the dimension of the keypoints in the image. Moreover, sum of distances between each keypoint and all other keypoints in the image is stored according to Equation 26.10

$$SD(p_m) = \sum_{j=1}^{N} d(p_m, p_j) \tag{26.10}$$

In this equation, $N$ is the number of keypoints in the image, and $d(p_m, p_j)$ is the distance between keypoint $p_m$ and keypoint $p_j$ based on Equation 26.9. The RI of keypoint $p_m$ is defined according to Equation 26.11. Then, a threshold value is selected to remove redundant keypoints and finally, if the distance between keypoints (except for the distance of each keypoint from itself) is less than the threshold value, one of these keypoints, which its sum distance value is smaller (RI is higher) is removed.

$$RI(p_m) = \frac{1}{SD(p_m)} \tag{26.11}$$

## 26.7 Description of the Proposed CMFD Method Based on RKEM-SIFT

In this section, we concentrate on RKEM-SIFT for CMFD. According to Figure 26.10, the proposed method is composed of four main steps: feature extraction using the RKEM-SIFT algorithm, the matching process using the g2NN criteria, the keypoint clustering and forgery detection using the agglomerative hierarchical clustering algorithm and removal of mismatches using RANSAC (random sample consensus).

### 26.7.1 Image Features Extraction

In this stage, features and descriptors are computed by applying the RKEM-SIFT algorithm on the image for CMFD. More details of which are described in Section 26.5.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_813_0.png)

Figure 26.10 Flowchart of the proposed method.

### 26.7.2 Keypoints Matching

There are various methods for keypoints matching, where 2NN and generalized 2NN (g2NN) (Amerini et al. 2011) are widely used in image forgery. In the 2NN method, the Euclidean distance of each keypoint descriptor is calculated relative to the descriptors of other keypoints, and then the keypoint whose distance from the first nearest neighbor to its second nearest neighbor, according to Equation 26.12, is less than the threshold is matched. The method is not suitable for the copy-move forgery when an object is copied more than once in the image. The g2NN method iterates the 2NN method until this ratio is greater than the threshold value, which according to (Amerini et al. 2011), is set to 0.5. This method is applicable to multiple copies.

$$\frac{d_1}{d_2} < T$$ (26.12)

### 26.7.3 Clustering

In this stage, the hierarchical agglomerative clustering is used to identify copied areas. In this clustering, each matching point is first considered as distinct clusters, and during the repetitive process at each stage, the Euclidean distance between all clusters is calculated, and, ultimately, the clusters with the most similarity are merged to form one cluster. Linkage methods on the clusters and the cut-off threshold value have an important effect on identifying the forging areas and herein we, according to paper (Amerini et al. 2011), use Ward’s linkage method with the threshold value 2.2.

### 26.7.4 Removal of Mismatches

The random sample consensus (RANSAC) algorithm introduced in 1981 by Fischler is one of the most applicable methods for removal of mismatches in the image (Fischler and Bolles 1981). In the following, the details of this algorithm are described.

### First stage
First, it is required to choose a proper model according to the transformation model because of the variations of the reference and sensed images. The needed matched points for calculation of different transformation parameters are according to Equation 26.13.

$$q = \frac{p}{2}$$ (26.13)

In the affine transformation, three matching points need to be chosen randomly in order to calculate the transformation parameters according to Equations 26.14 and 26.15.

$$\begin{bmatrix} x_1 & y_1 & 1 \\ x_2 & y_2 & 1 \\ x_3 & y_3 & 1 \end{bmatrix} \begin{bmatrix} a \\ b \\ c \end{bmatrix} = \begin{bmatrix} x'_1 \\ x'_2 \\ x'_3 \end{bmatrix}\tag{26.14}$$

$$\begin{bmatrix} x_1 & y_1 & 1 \\ x_2 & y_2 & 1 \\ x_3 & y_3 & 1 \end{bmatrix} \begin{bmatrix} d \\ e \\ f \end{bmatrix} = \begin{bmatrix} y'_1 \\ y'_2 \\ y'_3 \end{bmatrix}\tag{26.15}$$

In these relations, $(x_1,y_1)$, $(x_2,y_2)$ and $(x_3,y_3)$ are the coordinates of the matching points in duplicated region, and $(x'_1,y'_1)$, $(x'_2,y'_2)$ and $(x'_3,y'_3)$ are the coordinates of the matching points in the other duplicated region and $f$, $e$, $c$, $b$, $a$ are the parameters of the transformation model.

### Second stage
To choose the best model, three random matching points (in the affine transformation) are chosen to calculate the transformation parameters and the transformation model is accordingly calculated in each iteration, according to Equation 26.16.

$$\begin{bmatrix} a & b & c \\ d & e & f \\ 0 & 0 & 0 \end{bmatrix} \begin{bmatrix} x_i \\ y_i \\ 1 \end{bmatrix} = \begin{bmatrix} x'_i \\ y'_i \\ 1 \end{bmatrix} \Rightarrow$$
$$\begin{cases} x'_i = a x_i + b y_i + c \\ y'_i = d x_i + e y_i + f \end{cases}\tag{26.16}$$

where:
- $a, b, c, d, e,$ and $f$ are the transformation parameters
- $(x_i, y_i)$ is the matching point coordinates in the duplicated region in the image
- $(x'_i, y'_i)$ is the other duplicated region in the image coordinates of the transformation model

the transformation model could be written as $HP_i$ in which $H$ is the transformation parameters and $P_i$ is the matching points in the duplicated region in the image.

### Third stage
After calculating the transformation model parameters, for each matching point in the duplicated region in the image, the distance $(P, HP_i)$ is calculated in the other duplicated region in the image. If this
