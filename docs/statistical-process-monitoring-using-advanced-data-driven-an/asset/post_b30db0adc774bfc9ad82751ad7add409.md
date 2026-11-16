
features from a V-disparity map, and it has greedy learning properties and the capacity for dimensionality reduction. In addition, the kNN is an unsupervised and nonparametric clustering algorithm that does not require linear or Gaussian distribution of input data.

The DSA-based kNN method detects obstacles as anomalies using a V-disparity map. The V-disparity of images perceived in urban environments without obstacles is relatively stable with weak fluctuations due to measurement noise [34,40], and significant variations in V-disparity can be observed when obstacles are present. The method includes two steps: first, the V-disparity dataset is used to provide unsupervised greedy layerwise training to the deep encoder, and second, kNN is used to reveal potential obstacles. The kNN scheme is trained using features extracted with the DSA model based on an obstacle-free scene. This allows the kNN scheme to separate free and busy scenes in the testing data.

The objective of the monitoring system is to promptly detect any obstacles in front of an autonomous vehicle or mobile robot that can lead to dangerous accidents. In summary, in the DSA-kNN approach, obstacle detection is performed as anomaly detection based on features extracted from the DSA model. The kNN is used to identify deviations between obstacle-free features and newly extracted features. The DSA-kNN obstacle detection scheme is implemented in two stages: feature generation and feature evaluation:

Stage 1. The objective of the first stage is to learn relevant information from the V-disparity map to generate features that are sensitive to the presence of obstacles. To this end, a normalized V-disparity map is used as an input for the DSA model. Then, a reference DSA model is constructed using unsupervised greedy layer-wise training with unlabeled data. This model has four layers. The role of each is to learn complex and hierarchical features, and the output of the $i$th layer feeds the next $(i + 1)$ layer. Additionally, each layer discovers useful features and reduces dimensionality through encoding. Then, the extracted features are utilized for monitoring. The main advantage of DSA is its capacity to learn pertinent information from complex distributed data and produce low-dimensionality outputs. One of the key purposes in training the DSA model is to minimize reconstruction errors computed through cross-entropy (represented by $\mathcal{L}$ in Eq. (8.3)). Cross-entropy is a commonly used metric for evaluating deep learning models. Optimization is achieved by minimizing cross-entropy by quantifying the mismatch between two probability distributions of the input data and the estimation of the DSA model. The DSA model is selected when the dissimilarity between the two distributions decreases, which means that cross-entropy converges near zero [44]:

```
$$\mathcal{L}(X, \hat{X}) = - \sum_i^n \sum_j^m (\hat{x}_{ij} \log(x_{ij}) + (1 - \hat{x}_{ij}) \log(1 - x_{ij})) \quad (8.3)$$
```

where $X$ is the input ($n \times m$) normalized V-disparity matrix and $\hat{X}$ is the reconstructed V-disparity matrix via the built model of size ($n \times m$).

Stage 2. The obstacle detection phase involves evaluating the features extracted through DSA using the kNN scheme, which is an efficient nonparametric algorithm for separating different features (Fig. 8.5). Briefly, the kNN algorithm separates normal features from abnormal features (to identify inliers from outliers) by measuring the distance between the actual observation and the kNNs of obstacle-free data. The kNN scheme is applied by computing all distances, \(d_j\), in elements of the training set, \(S\), using the following equation, \(d_j = \text{distance}(x, S_J)\). The kNN distances with large values are used as indicators of obstacles in front of the vehicle. Euclidean distance is often used to measure similarity in kNN-based approaches. In scenes with no obstacles in front of the vehicle, the kNN distance fluctuates near zero, and in scenes with obstacles, the kNN distance significantly diverges from zero. Hence, large kNN distances indicate that there is a significant inconsistency between new observations and the training (obstacle-free) observations. Specifically, for every observation \(x_i\) (output of the DSA) in the training data, the kNN distances to its nearest neighbor in the training data, \(D_i\), are determined, based on which the sample distributions of distances can be computed:

```
\(\begin{aligned} D_i = \sum_{j=1}^{k} d_{ij}, \end{aligned}\) (8.4)
```

where \(d_{ij}\) is the distance from an observation to its \(j\)th nearest neighbor. The goal is to find obstacles at any time point within an observed scene using image pairs (left and right). This can be done by creating a detection threshold or control limit that distinguishes between free and busy scenes. We utilize the 3-sigma rule to fix the detection threshold, UCL, based on the kNN distance. In other words, we aim to flag an obstacle in front of the vehicle once the kNN distance passes the detection threshold. For the selected threshold, the false alarm rate was 0.27%. Based on the distribution of $D_i$, the parametric threshold of the kNN-Shewhart approach is computed as follows:

$\text{UCL} = \mu_D + 3\sigma_D, \qquad (8.5)$

where $\mu_D$ and $\sigma_D$ are the mean and standard deviation of kNN distances based on obstacle-free training data. An outlier (i.e., obstacle) is identified at the $i$th time point if the kNN distance, $d_j$, exceeds the decision threshold,

$d_j > \text{UCL}. \qquad (8.6)$

## 8.2.2 Data description

The effectiveness of the previously described algorithms was verified using the Malaga stereovision urban data set (MSVUD) [48] and the Daimler urban segmentation data set (DUSD) [49]. MSVUD consists of 15 subdatasets (extracts) with rich urban scenarios. MSVUD data was collected as a vehicle traveled for more than 20 km in an urban environment, which included a straight path, turns, road junctions, avenue traffic, and a freeway. The resolution is $800 \times 600$ pixels. DUSD data, which were gathered in urban traffic, include rectified stereo image pairs with a resolution of $1024 \times 440$ pixels [49].

The training dataset consists of two subdatasets of MSVUD. The first subset (called Extract #05 in MSVUD) includes 5,000 pairs of images collected from an avenue loop closure of around 1.7 km. The second subset (called Extract #08 in MSVUD) includes 10,000 pairs of images collected from a long loop closure of around 4.5 km. We also used 500 pairs of images from the DUSD dataset. For model training purposes, we selected datasets known to be devoid of obstacles.

For testing purposes and to verify the performance of the obstacle detection methods, we used two MSVUD datasets (1437 pairs of images) [48]: FREE-DST (3563 pairs of images) and the BUSY-DST datasets. The FREE-DST consists of images of free roads, while the BUSY-DST dataset consists of images of busy scenes with obstacles (e.g., vehicles, motorbikes, and pedestrians). These two datasets were randomly selected from extracts #10 and #12 of MSVUD.

## 8.2.3 Results and discussion

The DSA-kNN method was implemented into two steps. In the first step, we constructed the DSA model and established the detection threshold of the kNN detector based on training data with no obstacles. In the second step, we used the kNN detection threshold to detect obstacles in the unseen (remaining) data.

## 8.2.4 Model trained using data with no obstacles

Data believed to be devoid of obstacles were used to construct a reference DSA model. Fig. 8.6 displays four examples of scenes with no obstacles and their corresponding V-disparity maps. The inclined line in the V-disparity map represents the road profile, while the vertical line in the low V-disparity map represents the static environment (Fig. 8.6). These scenes do not include obstacles, as indicated by the free inclined line, and the vehicle is relatively far from the static environment, as indicated by the settled vertical lines with low V-disparity.

![](img/aa2f42c739937b682075082233e335bb_274_0.png)

FIGURE 8.6 Examples of four scenes with no obstacles: (right) the input image; (left) its corresponding V-disparity map.

Fig. 8.7 shows the evolution of the loss function (cross-entropy) in the function of the number of epochs. An epoch is one forward and backward pass of the training data over the layers of the deep learning model. The learning rate of the DSA model was set at 0.01. As can be seen in Fig. 8.7, that model loss converges at a relatively fast rate and reaches its minimum, which is close to zero, after 120 epochs. Based on this, we conclude that the DSA is able to model and reconstruct a V-disparity map with small errors. As discussed earlier, DSA has a good capacity for learning complex data without assuming anything regarding the underlying input data. Thus, this model will be adopted to detect obstacles in urban scenes.

The DSA we used has four layers. The V-disparity map is used as an input for the first, or input, layer, which is comprised of 600 × 256 neurons. The second layer, called the first hidden layer, is the first layer used to learn important features and reduce the dimensionality of the input data by 75% ((600 × 256)/4). Then, the output data from the first hidden layer is passed to the second hidden layer, which contains (600 × 256)/64 neurons, in order to extract the remaining information and further reduce dimensionality. The fourth layer, called the
